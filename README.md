# Microsoft Sentinel data lake
- **Device**: Monitors suspicious processes, credential dumping, lateral movement
- **Threat Hunting**: Advanced C2 detection, living off the land, data exfiltration, UBA
- **Security Events**: Windows authentication, process creation, account management

## 🎯 **Publication-Ready Features**

✅ **No Setup Dependencies** - Each notebook works independently  
✅ **Simple Configuration** - Just update one workspace name per notebook  
✅ **Universal Compatibility** - Works in any Microsoft Sentinel environment  
✅ **Smart Error Handling** - Clear messages when data isn't available  
✅ **Adapts to Your Data** - Uses whatever tables you have access to  

## Configuration (One Line Per Notebook)

Update workspace name in each notebook's configuration cell:
```python
PRIMARY_WORKSPACE = "your-workspace-name"  # 👈 UPDATE THIS
ENTRA_WORKSPACE = "default"               # Usually keep as "default"
```

**Example workspace names:**
- Enterprise: `"CompanyName-SOC"`, `"Security"`, `"Production"`
- Simple setups: `"default"`
- Custom: Whatever your workspace is named

## Troubleshooting

- **"Table not found"**: Check workspace name and verify Data Lake onboarding
- **Import errors**: Restart kernel, verify Sentinel extension authentication  
- **Performance issues**: Use smaller time windows or larger runtime pool
- **Limited data**: Notebooks adapt automatically - use whatever data you havealysis Notebooks

Security analysis notebooks for Microsoft Sentinel Data Lake using PySpark and advanced threat hunting techniques.

## 🚀 **SIMPLE SETUP - Just Update Workspace Names!**

Each notebook is **completely self-contained** - no setup dependencies!

### Quick Start (30 seconds)
1. **Prerequisites:**
   - Microsoft Sentinel Data Lake access
   - VS Code with Microsoft Sentinel extension
   - Authenticated to your Azure environment

2. **Simple Configuration:**
   - Open any notebook in VS Code
   - Update `PRIMARY_WORKSPACE = "your-workspace-name"` in the configuration cell
   - Run the notebook - everything else is automatic!

3. **Run Any Notebook (no specific order required):**
   - `02_Identity_Security_Analysis.ipynb` - Authentication threats & user behavior
   - `03_Device_Security_Analysis.ipynb` - Endpoint security & threat detection
   - `04_Advanced_Threat_Hunting.ipynb` - Advanced C2, LotL, data exfiltration
   - `05_Security_Events_Analysis.ipynb` - Windows security events analysis

## What Each Notebook Does

- **Identity**: Analyzes failed sign-ins, brute force attacks, geographic anomalies, user behavior
- **Device**: Monitors suspicious processes, credential dumping, lateral movement
- **Threat Hunting**: Advanced C2 detection, living off the land, data exfiltration
- **Security Events**: Windows authentication, process creation, account management

## Configuration

Update workspace name in each notebook:
```python
PRIMARY_WORKSPACE = "your-workspace-name"  # � UPDATE THIS
```

## Troubleshooting

- **"Table not found"**: Check workspace name and Data Lake onboarding
- **Import errors**: Restart kernel, verify Sentinel extension authentication
- **Performance issues**: Use smaller time windows or larger runtime pool

## Runtime Pool Guide

- **Small**: Development, testing (< 1GB data)
- **Medium**: Regular analysis (1-10GB data)  
- **Large**: Extensive hunting (> 10GB data)

---

Ready to start threat hunting! 🔍🛡️
