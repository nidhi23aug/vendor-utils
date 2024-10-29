# Read Data

**Description**:

- **Input**: 

- **Expected Output**: 

**Code Snippet**:
```python
with PlanetScope.open(tif_file) as planetdat:
    data_array = planetdat.data
    udm_data_array = planetdat.quality_data
    metadata = planetdat.metadata
    
    print(metadata)
    print(udm_data_array)