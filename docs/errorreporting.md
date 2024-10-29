## Error Reporting

If you encounter any errors during testing, please follow these steps to report them:

1. **Capture the error output**: Copy the error message from the notebook.
2. **Open a GitHub issue**: Go to the GitHub repository and open a new issue. https://github.com/NASA-IMPACT/csdap-vendor-utilities/issues
3. **Provide the following details**:
   - A brief description of the issue.
   - The steps to reproduce the error.
   - The error message or stack trace.
   - Relevant PlanetScope product details (e.g., 3-band, 4-band, or 8-band).
   - Any additional context or data used in the test.
4. Checking integration with rasterio and rio-xarray for
    - Fill no data / Interpolate (rio-xarray)
    - Reprojection  (rio-xarray)
    - Zonal statistics  (rio-xarray)
    - Clip (rio-xarray)
    - Resampling (rasterio)

### Issue Template Example

```markdown
**Description**: Briefly describe the error.

**Steps to Reproduce**:
1. List the steps taken before the error occurred.

**Error Message**: Paste the error message or stack trace here.

**Data Information**: Mention the PlanetScope product and any specific bands used (e.g., 3-band, 4-band, or 8-band).

**Additional Context**: Provide any extra details that might help in debugging.