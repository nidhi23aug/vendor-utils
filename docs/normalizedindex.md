# Calculate Normalized Index

**Description**:

- **Input**: 

- **Expected Output**: 

**Code Snippet**:

```python
# Band Ratio
with PlanetScope.open(tif_file) as planet_obj:   
    normalized_idx = planet_obj.normalized_indices(band1_index = 0, band2_index = 3)
    print(np.isnan(normalized_idx).all())

# NDVI
with PlanetScope.open(tif_file) as planet_obj:   
    ndvi = planet_obj.ndvi
    print(np.unique(ndvi))

#EVI
with PlanetScope.open(tif_file) as planet_obj:   
    evi = planet_obj.evi
    print(np.unique(evi))

