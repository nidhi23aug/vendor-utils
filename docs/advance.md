# Exploring other functions from rasterio and rio-xarray packages

**Description**:
This example demonstrates the use of key functionalities from the **rasterio** and **rio-xarray** packages for geospatial data processing. It includes operations for **reprojection**, **clipping** a raster to a bounding box, and **resampling** the raster to a new resolution.

**Input**: 
- **Raster dataset** (`ras1`): An input raster opened with `rio-xarray`.  
- **CRS for reprojection**: `"EPSG:4326"`  
- **Bounding box coordinates**:  
  ```text
  minx = -90.32, miny = 31.33, maxx = -89.90, maxy = 31.15
  ```  
- **Scale factor for resampling**: `0.75`  
- **Input raster file path**: `tif_file`  
- **Output raster path for resampled data**:  
  ```
  VendorUtil_Planet/NewData/resampled_raster.tif
  ```

**Expected Output**: 
- **Reprojected Raster**: A raster object (`ras1_lonlat`) reprojected to the `"EPSG:4326"` CRS.  
- **Clipped Raster**: A subset of the raster clipped using the specified bounding box.  
- **Resampled Raster**:  
  - A new raster with dimensions scaled down by 0.75, saved to the specified file.  
  - Confirmation message:  
    ```
    Success: Resample saved
    ```


**Code Snippet**:

```python
# Reprojection
ras1_lonlat = ras1.rio.reproject("EPSG:4326")
print(ras1_lonlat)

# Clip the raster
from shapely.geometry import box

minx, miny, maxx, maxy = -90.32, 31.33, -89.90, 31.15
bbox = box(minx, miny, maxx, maxy)
clipped = ras1_lonlat.rio.clip([bbox], crs="EPSG:4326")

# Resample
from rasterio.enums import Resampling

scale_factor = 0.75
with rasterio.open(tif_file) as src:
    data = src.read(
        out_shape=(
            src.count,
            int(src.height * scale_factor),
            int(src.width * scale_factor)
        ),
        resampling=Resampling.bilinear
    )

    profile = src.profile
    profile.update(
        width=data.shape[2],
        height=data.shape[1]
    )

    with rasterio.open("VendorUtil_Planet/NewData/resampled_raster.tif", "w", **profile) as dst:
        dst.write(data)

print("Success: Resample saved")
