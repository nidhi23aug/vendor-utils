# Read Quality Flag

**Description**:

- **Input**: 

- **Expected Output**: 

**Code Snippet**:
### Accessing different quality masks

```python
with PlanetScope.open(tif_file) as planet_obj:    
    planet_obj.get_quality_mask("clear")
    planet_obj.get_quality_mask("cloud")
    planet_obj.get_quality_mask("snow")
    planet_obj.get_quality_mask("shadow")
    planet_obj.get_quality_mask("haze_light")
    planet_obj.get_quality_mask("haze_heavy")
    planet_obj.get_quality_mask("cloud")
    planet_obj.get_quality_mask("confidence")

### Extract quality flags for a point from the data
with PlanetScope.open(tif_file) as planet_obj:
    print(planet_obj.get_quality_from_point(lat=28.866933958061644, lon=-97.90677761357139))    
