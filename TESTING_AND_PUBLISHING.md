# Testing and Publishing Guide for Monochai

## Testing the Extension Locally

### Method 1: Development Mode (Recommended)

1. Open the `monochai` folder in VSCode
2. Press `F5` to launch a new Extension Development Host window
3. In the new window, go to `File > Preferences > Color Theme` (or `Ctrl+K Ctrl+T`)
4. Select either "Monochai Dark" or "Monochai Light"
5. Test with different file types to ensure syntax highlighting works correctly

### Method 2: Install from .vsix file

1. Package the extension: `vsce package`
2. Install the .vsix file: `code --install-extension monochai-1.0.0.vsix`

## Publishing to VSCode Marketplace

### Prerequisites

1. Install vsce: `npm install -g vsce`
2. Create a Visual Studio Marketplace publisher account at: https://marketplace.visualstudio.com/manage
3. Generate a Personal Access Token in Azure DevOps

### Steps to Publish

1. **Update package.json** with your actual publisher name:

   ```json
   "publisher": "your-actual-publisher-name"
   ```

2. **Package the extension**:

   ```bash
   cd monochai
   vsce package
   ```

3. **Login to your publisher account**:

   ```bash
   vsce login your-publisher-name
   ```

4. **Publish the extension**:
   ```bash
   vsce publish
   ```

### Alternative: Manual Upload

1. Package: `vsce package`
2. Go to https://marketplace.visualstudio.com/manage
3. Upload the .vsix file manually

## Pre-Publishing Checklist

- [ ] Test both dark and light themes
- [ ] Verify all colors display correctly
- [ ] Test syntax highlighting with various file types
- [ ] Update publisher name in package.json
- [ ] Update repository URLs to actual GitHub repo
- [ ] Create GitHub repository and push code
- [ ] Ensure README.md has screenshots (optional but recommended)

## Publishing Commands Summary

```bash
# Package only
vsce package

# Publish directly
vsce publish

# Publish with version bump
vsce publish patch   # 1.0.0 -> 1.0.1
vsce publish minor   # 1.0.0 -> 1.1.0
vsce publish major   # 1.0.0 -> 2.0.0
```

## Post-Publishing

1. Verify extension appears in marketplace
2. Test installation from marketplace
3. Monitor reviews and feedback
4. Update documentation as needed
