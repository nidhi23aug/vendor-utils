# Calculate Surface Reflectance

**Description**:

- **Input**: 

- **Expected Output**: 

**Code Snippet**:

```python
with PlanetScope.open(tif_file) as planet_obj:
    print(planet_obj.reflectance_coefficient)

with PlanetScope.open(tif_file) as planet_obj:
    print(planet_obj.surface_reflectance.shape)
