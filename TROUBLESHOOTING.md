# Troubleshooting Guide

Common issues and solutions for Microsoft Sentinel Data Lake notebooks.

## Import Errors

**Error:** `ImportError: No module named 'sentinel_lake'`

**Solutions:**
- ✅ Verify you're in VS Code with Microsoft Sentinel extension
- ✅ Check authentication to Microsoft Sentinel extension  
- ✅ Select appropriate runtime pool (Small/Medium/Large)
- ✅ Restart notebook kernel

## Table Not Found

**Error:** `Table 'SignInLogs' not found`

**Solutions:**
- ✅ Verify Data Lake onboarding is complete
- ✅ Check workspace name is correct in notebooks
- ✅ Ensure sufficient data has been ingested
- ✅ Verify table permissions

## Spark Session Issues

**Error:** `NameError: name 'spark' is not defined`

**Solutions:**
- ✅ Restart notebook kernel
- ✅ Verify you're in Data Lake environment
- ✅ Check Microsoft Sentinel extension status

## Performance Issues

**Problem:** Slow queries or timeouts

**Solutions:**
- ✅ Reduce time windows (use fewer days/hours)
- ✅ Add filters early in queries
- ✅ Use larger runtime pool for big datasets
- ✅ Avoid collecting large results to driver

## Authentication Problems

**Problem:** Connection or permission errors

**Solutions:**
- ✅ Re-authenticate Microsoft Sentinel extension
- ✅ Verify RBAC permissions
- ✅ Check Azure subscription access
- ✅ Restart VS Code if needed

## No Data Found

**Problem:** Empty query results

**Solutions:**
- ✅ Verify data ingestion is working
- ✅ Check time windows (try longer periods)
- ✅ Confirm data sources are configured
- ✅ Check data retention settings

## Quick Fixes

1. **Restart Everything:** Kernel → VS Code → Extension
2. **Check Basics:** Authentication → Permissions → Workspace name
3. **Verify Environment:** Data Lake → Tables → Data volume
4. **Optimize Queries:** Time filters → Early filtering → Smaller results

## Getting Help

- Check Output pane in VS Code (Microsoft Sentinel > Debug)
- Review Microsoft Learn documentation for Data Lake
- Contact Azure Support for technical issues
- Data Lake onboarding not complete
- Insufficient data ingestion
- Incorrect workspace name
- Missing permissions

**Solutions:**
1. ✅ **Check Workspace Name**: Verify `WORKSPACE_NAME` is correct in your notebooks
2. ✅ **Wait for Data**: Data Lake onboarding can take time - wait for sufficient data ingestion
3. ✅ **Verify Permissions**: Ensure you have appropriate Azure RBAC roles
4. ✅ **Check Onboarding Status**: Verify Data Lake feature is fully enabled

### Issue 4: Authentication / Permission Errors

**Symptoms:**
```
Unauthorized access
Forbidden (403)
Access denied
```

**Causes:**
- Insufficient Azure permissions
- Not authenticated to correct tenant
- Missing Data Lake access

**Solutions:**
1. ✅ **Check RBAC Roles**: Ensure you have:
   - Microsoft Sentinel Reader (minimum)
   - Microsoft Sentinel Contributor (for full access)
   - Log Analytics Reader
2. ✅ **Verify Tenant**: Make sure you're connected to the correct Azure tenant
3. ✅ **Re-authenticate**: Sign out and back into the Microsoft Sentinel extension

### Issue 5: Performance Issues / Timeouts

**Symptoms:**
- Slow query execution
- Session timeouts
- Memory errors

**Causes:**
- Large datasets
- Insufficient runtime pool size
- Inefficient queries

**Solutions:**
1. ✅ **Upgrade Runtime Pool**: Use Medium or Large pool for bigger workloads
2. ✅ **Add Time Filters**: Limit data scope with time-based filters
3. ✅ **Optimize Queries**: 
   - Filter early in processing
   - Use `.show()` instead of `.collect()` for previews
   - Avoid collecting large datasets to driver
4. ✅ **Clear Memory**: Use `df.unpersist()` to free up memory

### Issue 6: Visualization Errors

**Symptoms:**
```
ImportError: No module named 'matplotlib'
ImportError: No module named 'seaborn'
```

**Causes:**
- Missing visualization libraries
- Environment not properly configured

**Solutions:**
1. ✅ **Install Libraries**: Run in a notebook cell:
   ```python
   %pip install matplotlib seaborn pandas
   ```
2. ✅ **Use Alternative**: Use Spark's built-in `.show()` for basic data display
3. ✅ **Check Environment**: Ensure runtime pool has required packages

### Issue 7: JSON Parsing Errors

**Symptoms:**
```
Cannot parse JSON field
Schema mismatch errors
```

**Causes:**
- Incorrect JSON schema definition
- Malformed JSON data
- Schema evolution

**Solutions:**
1. ✅ **Check Schema**: Verify JSON schema matches actual data structure
2. ✅ **Handle Nulls**: Use proper null handling in schema definitions
3. ✅ **Sample Data First**: Examine raw JSON before defining schema
4. ✅ **Use Flexible Schema**: Allow for optional fields and variations

### Issue 8: No Data in Results

**Symptoms:**
- Empty DataFrames
- Zero row counts
- No recent data

**Causes:**
- Insufficient data ingestion
- Incorrect time filters
- Data retention policies

**Solutions:**
1. ✅ **Check Time Windows**: Expand analysis time window (e.g., 72 hours instead of 24)
2. ✅ **Verify Data Sources**: Check which data sources are actively ingesting
3. ✅ **Remove Filters**: Temporarily remove filters to see if any data exists
4. ✅ **Check Data Freshness**: Verify when data was last ingested

## 🔧 Diagnostic Commands

### Check Environment Status
```python
from sentinel_utilities import get_environment_status
status = get_environment_status()
print(status)
```

### Test Basic Connectivity
```python
from sentinel_utilities import SentinelDataLakeHelper
helper = SentinelDataLakeHelper("your-workspace-name")
result = helper.check_table_availability("SignInLogs")
print(result)
```

### Debug Table Availability
```python
# List all available tables
tables = ['SignInLogs', 'DeviceEvents', 'SecurityEvent', 'Heartbeat']
for table in tables:
    result = helper.check_table_availability(table)
    print(f"{table}: {result}")
```

### Memory and Performance Check
```python
# Check Spark configuration
print("Spark Configuration:")
for key, value in spark.sparkContext.getConf().getAll():
    if 'memory' in key.lower() or 'executor' in key.lower():
        print(f"{key}: {value}")
```

## 🛠️ Environment Validation Checklist

Before running analysis notebooks, verify:

- [ ] ✅ VS Code with Microsoft Sentinel extension installed
- [ ] ✅ Authenticated to correct Azure tenant
- [ ] ✅ Microsoft Sentinel Data Lake access enabled
- [ ] ✅ Sufficient Azure RBAC permissions
- [ ] ✅ Data Lake onboarding completed
- [ ] ✅ Sufficient data ingested (wait time after onboarding)
- [ ] ✅ Correct workspace name configured
- [ ] ✅ Appropriate runtime pool selected
- [ ] ✅ Network connectivity to Azure services

## 📞 Getting Additional Help

### Documentation Resources
- [Microsoft Sentinel Data Lake Overview](https://learn.microsoft.com/en-us/azure/sentinel/datalake/sentinel-lake-overview)
- [Using Notebooks with Data Lake](https://learn.microsoft.com/en-us/azure/sentinel/datalake/notebooks)
- [Sample Notebooks](https://learn.microsoft.com/en-us/azure/sentinel/datalake/notebook-examples)

### Support Channels
1. **Azure Support**: For platform and access issues
2. **Microsoft Learn Q&A**: For technical questions
3. **GitHub Issues**: For notebook-specific problems

### Diagnostic Information to Collect
When seeking help, include:
- Environment status output
- Full error messages
- Notebook cell that's failing
- Data Lake onboarding date
- Azure subscription and tenant details
- Runtime pool configuration

## 🔄 Recovery Procedures

### Complete Environment Reset
1. Sign out of Microsoft Sentinel extension
2. Restart VS Code
3. Sign back into extension
4. Select correct subscription and workspace
5. Choose appropriate runtime pool
6. Restart notebook kernel
7. Re-run setup notebook

### Cache Clearing
```python
# Clear Spark SQL cache
spark.sql("CLEAR CACHE")

# Clear catalog cache
spark.catalog.clearCache()

# Restart Spark context (use with caution)
spark.sparkContext.stop()
```

### Session Recovery
If your session becomes unresponsive:
1. Save your work
2. Use VS Code command: "Jupyter: Restart Kernel"
3. Re-run initialization cells
4. Continue from where you left off

---

*This troubleshooting guide is updated regularly. Report issues or improvements to help others in the community.*
