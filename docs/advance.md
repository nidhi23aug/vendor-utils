# Exploring other functions from rasterio and rio-xarray packages

**Description**:

- **Input**: 

- **Expected Output**: 

**Code Snippet**:

```python
# Reprojection
data_array_lonlat = data_array.rio.reproject("EPSG:4326")
print(data_array_lonlat)

# Clip the raster
from shapely.geometry import box

minx, miny, maxx, maxy = -90.32, 31.33, -89.90, 31.15
bbox = box(minx, miny, maxx, maxy)
clipped = data_array_lonlat.rio.clip([bbox], crs="EPSG:4326")

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
