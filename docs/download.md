
### `docs/download.md`

```markdown
# Download Data

**Description**: Download satellite images based on the filtered search results. Each image is available in a format suitable for geospatial analysis (e.g., TIFF).

- **Input**: Image product IDs from the filtered search
- **Expected Output**: TIFF files of the selected satellite images

**Code Snippet**:
```python
# Select an item from the search results
item_id = results[0]["id"]
product_type = "analytic"

# Download the selected item
client.download(item_id, product_type, output_dir="downloaded_images")
print("Download completed for:", item_id)
