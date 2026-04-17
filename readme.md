## HP KE100 Label Printer (ZPL Compatible) – Minimal CUPS PPD

Minimal CUPS PPD for the HP KE100 label printer using ZPL compatibility. Optimized for reliable 4×6 label printing with:
- Correct media sizing
- Zero margins
- Stable output for shipping and warehouse workflows

Supports Linux and macOS environments using CUPS.

---

## Features

- 4×6 label (288 × 432 points)
- Zero-margin printing
- ZPL-compatible raster output
- Supports 203 DPI and 300 DPI
- Direct Thermal and Thermal Transfer modes
- Lightweight, minimal configuration (no unnecessary options)

---

## PPD File

```ppd
*PPD-Adobe: "4.3"
*%%%% HP KE100 Label Printer (ZPL Compatible)
*%%%% Minimal CUPS PPD for 4x6 labels
*FormatVersion: "4.3"
*FileVersion: "1.0"
*LanguageVersion: English
*LanguageEncoding: ISOLatin1

*PCFileName: "HP_KE100.PPD"
*Product: "(HP KE100 Label Printer)"
*Manufacturer: "HP"
*ModelName: "HP KE100 Label Printer"
*ShortNickName: "HP KE100"
*NickName: "HP KE100 Label Printer (ZPL Compatible)"

*PSVersion: "(3010.000) 0"
*LanguageLevel: "3"
*ColorDevice: False
*DefaultColorSpace: Gray
*FileSystem: False
*Throughput: "8"
*LandscapeOrientation: Plus90
*TTRasterizer: Type42

*cupsSNMPSupplies: "false"
*cupsVersion: 2.1
*cupsModelNumber: 18
*cupsManualCopies: False
*cupsFilter: "application/vnd.cups-raster 50 rastertolabel"
*cupsLanguages: "en"

*OpenUI *PageSize/Media Size: PickOne
*OrderDependency: 10 AnySetup *PageSize
*DefaultPageSize: w288h432
*PageSize w288h432/4x6 Label: "<</PageSize[288 432]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageSize

*OpenUI *PageRegion/Media Size: PickOne
*OrderDependency: 10 AnySetup *PageRegion
*DefaultPageRegion: w288h432
*PageRegion w288h432/4x6 Label: "<</PageSize[288 432]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageRegion

*DefaultImageableArea: w288h432
*ImageableArea w288h432/4x6 Label: "0 0 288 432"

*DefaultPaperDimension: w288h432
*PaperDimension w288h432/4x6 Label: "288 432"

*HWMargins: 0 0 0 0
*MaxMediaWidth: "288"
*MaxMediaHeight: "432"

*OpenUI *Resolution/Resolution: PickOne
*OrderDependency: 10 AnySetup *Resolution
*DefaultResolution: 203dpi
*Resolution 203dpi/203 DPI: "<</HWResolution[203 203]/cupsBitsPerColor 1/cupsColorSpace 3>>setpagedevice"
*Resolution 300dpi/300 DPI: "<</HWResolution[300 300]/cupsBitsPerColor 1/cupsColorSpace 3>>setpagedevice"
*CloseUI: *Resolution

*OpenUI *MediaType/Media Type: PickOne
*OrderDependency: 20 AnySetup *MediaType
*DefaultMediaType: Direct
*MediaType Direct/Direct Thermal: "<</MediaType(Direct)>>setpagedevice"
*MediaType Thermal/Thermal Transfer: "<</MediaType(Thermal)>>setpagedevice"
*CloseUI: *MediaType

*DefaultFont: Courier
```

---

## Installation

### Linux (CUPS)

```bash
# Copy PPD to system directory
sudo cp HP_KE100.PPD /usr/share/ppd/custom/

# Add printer (example)
lpadmin -p HP_KE100 -E -v usb://HP/KE100 -P /usr/share/ppd/custom/HP_KE100.PPD
```

---

### macOS (CUPS Web UI)

```text
1. Open: http://localhost:631
2. Go to: Administration → Add Printer
3. Select your printer connection
4. Choose: "Provide a PPD File"
5. Upload: HP_KE100.PPD
```

---

## Recommended Settings

- Media Size: 4x6 Label
- Resolution: 203 DPI (default)
- Media Type: Direct Thermal (unless using ribbon)
- Scaling: 100% (disable fit-to-page in apps)

---

## Notes

- Designed for ZPL-compatible label printers
- Uses rastertolabel filter for consistent output
- Zero margins ensure full label utilization
- Works best with shipping platforms (UPS, FedEx, USPS, etc.)

---

## File Structure Example

```text
HP_KE100_PPD/
└── HP_KE100.PPD
```

---

## Troubleshooting

- **Misaligned prints**  
  Ensure application scaling is disabled (no “fit to page”)

- **Blank labels**  
  Verify correct Media Type (Direct vs Thermal)

- **Incorrect size**  
  Confirm PageSize is set to 4x6 (w288h432)

- **Slow printing**  
  Use 203 DPI unless higher resolution is required

---

## License / Usage

This PPD is provided as-is for compatibility and testing purposes. Adjustments may be required depending on firmware or environment.
