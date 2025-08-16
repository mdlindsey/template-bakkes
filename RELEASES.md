# GitHub Actions Automated Build & Release

This repository includes GitHub Actions workflows that automatically build your BakkesMod plugin and create releases whenever you push to the main branch.

## 🚀 What These Workflows Do

### Basic Workflow (`build.yml`)
- **Triggers**: Push to main branch, manual dispatch
- **Builds**: Release x64 configuration
- **Outputs**: DLL files and ZIP packages
- **Releases**: Creates GitHub releases automatically

### Advanced Workflow (`build-advanced.yml`)
- **Triggers**: Push to main/develop, pull requests, manual dispatch
- **Builds**: Matrix build with Release x64 configuration
- **Outputs**: DLL files, ZIP packages, build verification
- **Releases**: Enhanced release notes and build status summary
- **Features**: Better error handling, build verification, status reporting

## 📋 Prerequisites

1. **GitHub Repository**: Your code must be in a GitHub repository
2. **GitHub Actions**: Enabled in your repository settings
3. **Permissions**: The `GITHUB_TOKEN` secret is automatically available

## 🔧 Setup Instructions

### 1. Enable GitHub Actions
- Go to your repository on GitHub
- Click on the "Actions" tab
- Click "Enable Actions" if not already enabled

### 2. Push the Workflow Files
The workflow files are already in the `.github/workflows/` directory. Just commit and push them:

```bash
git add .github/
git commit -m "Add GitHub Actions workflows for automated builds"
git push origin main
```

### 3. Verify Setup
- Go to the "Actions" tab in your repository
- You should see the workflows listed
- The first workflow will run automatically on your next push to main

## 📁 Workflow Structure

```
.github/
└── workflows/
    ├── build.yml              # Basic build workflow
    └── build-advanced.yml     # Advanced build workflow
```

## 🔄 How It Works

### Automatic Triggers
- **Push to main**: Automatically builds and creates a release
- **Push to develop**: Builds but doesn't create a release
- **Pull requests**: Builds to verify changes (no release)

### Manual Triggers
- **Workflow dispatch**: Manually trigger builds from the Actions tab
- **Release type selection**: Choose patch/minor/major versioning

### Build Process
1. **Setup**: Install MSBuild, Visual Studio 2022
2. **Build**: Compile the plugin using MSBuild
3. **Package**: Create ZIP files containing the DLL
4. **Release**: Upload to GitHub releases (main branch only)
5. **Status**: Generate build summary and status

## 📦 Output Files

### Build Artifacts
- **DLL files**: Compiled plugin files
- **ZIP packages**: Ready-to-install plugin packages
- **Build logs**: Detailed build information

### Release Files
- **Plugin DLL**: Direct download of the compiled plugin
- **ZIP package**: Complete plugin package for easy installation
- **Release notes**: Automatic changelog and installation instructions

## 🎯 Customization Options

### Build Configuration
- **Platforms**: Currently x64, can add x86 if needed
- **Configurations**: Currently Release, can add Debug
- **Output paths**: Customizable build and output directories

### Release Settings
- **Versioning**: Automatic build number incrementing
- **Release notes**: Customizable templates and formatting
- **File naming**: Configurable ZIP and release names

## 🐛 Troubleshooting

### Common Issues

#### Build Failures
- Check that all dependencies are properly referenced
- Verify the project file paths are correct
- Ensure the `Bakkes.props` file is properly configured

#### Release Failures
- Verify you're pushing to the main branch
- Check that the `GITHUB_TOKEN` has proper permissions
- Ensure the workflow has access to create releases

#### DLL Not Found
- Check the build output directory configuration
- Verify the project builds successfully locally
- Check the MSBuild output for errors

### Debug Steps
1. **Check Actions tab**: View detailed build logs
2. **Verify file paths**: Ensure build directories exist
3. **Test locally**: Build the project on your machine first
4. **Check permissions**: Ensure GitHub Actions can create releases

## 📚 Additional Resources

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [MSBuild Command Line Reference](https://docs.microsoft.com/en-us/visualstudio/msbuild/msbuild-command-line-reference)
- [GitHub Releases API](https://docs.github.com/en/rest/reference/releases)

## 🤝 Contributing

To modify these workflows:
1. Edit the `.yml` files in `.github/workflows/`
2. Test changes in a fork or branch first
3. Submit a pull request with your improvements
4. Ensure the workflows still build successfully

## 📝 Notes

- **Build artifacts** are retained for 30 days
- **Releases** are only created for pushes to main branch
- **Version numbers** are automatically incremented from `version.h`
- **ZIP packages** include all necessary plugin files
- **Build verification** ensures DLL files are created successfully

---

*These workflows are designed specifically for BakkesMod plugin development and will automatically handle the build process, packaging, and release creation.*
