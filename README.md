# Microsoft Sentinel data lake
- **Data Exfiltration Early Warning**: Detects staging, CLI uploads, egress spikes, and storage audit anomalies (with customizable allow-lists)
- **Service Principal Sign-Ins**: Zero-config risk & anomaly analytics (bursts, rare apps, off-hours, persistence, risky principal enrichment)
- **Device**: Monitors suspicious processes, credential dumping, lateral movement
- **Threat Hunting**: Advanced C2 detection, living off the land, data exfiltration, UBA
- **Security Events**: Windows authentication, process creation, account management

## 🎯 **Publication-Ready Features**

✅ **No Setup Dependencies** - Each notebook works independently  
✅ **Zero-Config (Service Principals)** - Auto-detects tables & infers schema; no workspace variable needed  
✅ **Simple Configuration** - Just update one workspace name per notebook (others optional)  
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
- **Limited data**: Notebooks adapt automatically - use whatever data you have

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
   - `01_Data_Exfiltration_Early_Warning.ipynb` - Compression staging, suspicious uploads, egress spikes, storage audit anomalies
   - `02_Identity_Security_Analysis.ipynb` - Authentication threats & user behavior
   - `03_Device_Security_Analysis.ipynb` - Endpoint security & threat detection
   - `04_Advanced_Threat_Hunting.ipynb` - Advanced C2, LotL, data exfiltration
   - `05_Security_Events_Analysis.ipynb` - Windows security events analysis
   - `06_ServicePrincipal_SignIn_Analysis.ipynb` - Service principal sign-in anomalies, pivot patterns, enrichment & scoring

## What Each Notebook Does

- **Data Exfiltration Early Warning**: Correlates compression jobs, staging directories, network egress, and storage operations. Includes allow-list scaffolding so you can tune out expected backup activity while keeping visibility into new behaviours.
- **Identity**: Analyzes failed sign-ins, brute force attacks, geographic anomalies, user behavior
- **Device**: Monitors suspicious processes, credential dumping, lateral movement
- **Threat Hunting**: Advanced C2 detection, living off the land, data exfiltration
- **Security Events**: Windows authentication, process creation, account management
- **Service Principals**: Bursts (μ+3σ), rare app usage, failure→success pivots, new/off-hours IPs, persistence patterns, risky principal enrichment & scoring

## Configuration

Update workspace name in each notebook (except the service principal notebook which auto-detects):
```python
PRIMARY_WORKSPACE = "your-workspace-name"  # 👈 UPDATE THIS
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
