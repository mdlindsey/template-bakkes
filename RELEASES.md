# Automated Releases with GitHub Actions

This repository automatically builds and releases your BakkesMod plugin on every push to the main branch.

## 🚀 **What Happens Automatically**

- **Builds** your plugin using MSBuild on Windows
- **Creates** both DLL and ZIP files
- **Releases** to GitHub with version numbers
- **Updates** build numbers automatically

## 📁 **Available Workflows**

| Workflow | Purpose | Features |
|----------|---------|----------|
| `build.yml` | Basic builds | Simple, stub headers |
| `build-advanced.yml` | Matrix builds | Better error handling, PR builds |
| `build-with-sdk.yml` | Production builds | Real SDK integration |

## ⚠️ **Important: SDK Dependencies**

Your plugin requires BakkesMod SDK headers that aren't available on GitHub Actions by default.

### **Current Setup (Stub Headers)**
- ✅ Compiles successfully
- ❌ Resulting DLL won't work in BakkesMod
- 🎯 Use for testing build pipeline

### **Production Setup (Real SDK)**
- ✅ Creates functional plugin DLLs
- ❌ Requires hosting SDK files publicly
- 🎯 Use for actual releases

## 🔧 **Setting Up Real SDK Integration**

### **Option 1: Host SDK Publicly**
1. Extract SDK from your BakkesMod installation:
   ```
   C:\Users\[Username]\AppData\Roaming\bakkesmod\bakkesmod\bakkesmodsdk\
   ```
2. Upload to public hosting (Google Drive, Dropbox, etc.)
3. Update workflow to download from your URL

### **Option 2: GitHub Secrets**
1. Store SDK as base64-encoded secret
2. Decode during build
3. More secure but requires manual updates

### **Option 3: GitHub Packages**
1. Create private package containing SDK
2. Reference in workflow
3. Professional approach for commercial plugins

## 🧪 **Testing Your Setup**

```bash
# Test with stub headers first
git add .github/
git commit -m "Add GitHub Actions workflows"
git push origin main

# Check Actions tab for build results
# Verify DLL files are created
```

## 🔍 **Common Issues & Solutions**

| Problem | Cause | Solution |
|---------|-------|----------|
| "Cannot open include file" | Missing SDK headers | Implement SDK integration |
| MSBuild not found | Environment not set up | Uses `VsDevCmd.bat` (should work) |
| DLL doesn't load in BakkesMod | Using stub headers | Implement real SDK integration |
| Permission denied on release | Missing permissions | Check `GITHUB_TOKEN` settings |

## 📋 **Production Checklist**

- [ ] Choose SDK integration method
- [ ] Test build pipeline thoroughly
- [ ] Verify generated DLL works
- [ ] Set up automated releases
- [ ] Include installation instructions

## 📚 **Resources**

- [GitHub Actions Docs](https://docs.github.com/en/actions)
- [BakkesMod Plugin Dev](https://bakkesmod.com/docs/)
- [MSBuild Reference](https://docs.microsoft.com/en-us/visualstudio/msbuild/msbuild-command-line-reference)

---

*This setup provides professional, automated builds for your BakkesMod plugin.*
