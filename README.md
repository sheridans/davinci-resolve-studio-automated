# DaVinci Resolve Studio - Automated PKGBUILD

An enhanced PKGBUILD for the [DaVinci Resolve Studio AUR package](https://aur.archlinux.org/packages/davinci-resolve-studio) that eliminates manual version and hash updates through automation.

## Features

- **Automatic Version Detection** - Extracts version from zip filename using `pkgver()` function
- **Zero Maintenance** - No more manual version or hash updates needed
- **Robust Error Handling** - Clear messages for missing, multiple, or invalid files
- **File Validation** - Ensures correct file exists before processing
- **Enhanced Prepare** - Automatic zip extraction with user feedback

## How It Works

1. **Download** `DaVinci_Resolve_Studio_X.Y.Z_Linux.zip` from [Blackmagic Design](https://www.blackmagicdesign.com/support/family/davinci-resolve-and-fusion)
2. **Place** the zip file in the PKGBUILD directory
3. **Run** `makepkg` - version is automatically detected from filename
4. **Build** proceeds with proper validation and extraction

## Key Improvements

### Dynamic Version Detection
```bash
pkgver() {
  # Automatically finds and extracts version from zip filename
  # Handles errors gracefully with helpful messages
}
```

### Simplified Checksums
- Uses `SKIP` for the zip file (appropriate for manual downloads from official source)
- Maintains checksum verification for package-provided scripts
- Eliminates hash update burden for maintainers

### Enhanced Error Messages
- Clear guidance when no file is found
- Helpful error when multiple versions exist
- Validation for proper filename format

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/sheridans/davinci-resolve-studio-automated.git
   cd davinci-resolve-studio-automated
   ```

2. Download DaVinci Resolve Studio zip from Blackmagic Design

3. Build the package:
   ```bash
   makepkg -si
   ```

## Comparison with Original

| Feature | Original | Automated |
|---------|----------|-----------|
| Version updates | Manual edit | Automatic detection |
| Hash updates | Manual calculation | SKIP (appropriate for manual downloads) |
| Error handling | Basic | Comprehensive with helpful messages |
| User experience | Requires PKGBUILD editing | Drop file and build |

## Files Included

- `PKGBUILD` - Enhanced with automation features
- `davinci-control-panels-setup.sh` - Control panels launcher script
- `davinci-resolve-studio.install` - Post-installation hooks
- `davinci-resolve-studio-automation.patch` - Diff showing all changes

## Security Considerations

The zip file checksum uses `SKIP` because:
- Users manually download from Blackmagic's official site (not automated)
- File integrity is validated during extraction and processing
- This approach is appropriate for manually-downloaded proprietary software
- Eliminates maintenance burden while preserving security through validation

## Credits

- **Original Maintainer**: [Muflone](http://www.muflone.com/contacts/english/)
- **Original Contributors**: Alex S., Jonathon Fernyhough

Based on the official [davinci-resolve-studio AUR package](https://aur.archlinux.org/packages/davinci-resolve-studio).

## Contributing

Feel free to open issues or submit pull requests for improvements to the automation logic.

## License

Follows the same license terms as the original AUR package. DaVinci Resolve Studio itself requires a commercial license from Blackmagic Design.