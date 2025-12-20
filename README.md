# 🧾 Costco Receipt Merger

A browser-based tool for intelligently merging multiple local Costco receipt files (JSON) with automatic deduplication and data completion.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Version](https://img.shields.io/badge/version-0.1.0-green.svg)

## ✨ Features

- 🎯 **Intelligent Merging** - Deep merges receipt data to fill in missing fields
- 🔍 **Smart Deduplication** - Uses transaction barcode + membership number as unique key
- 📊 **Completeness Scoring** - Automatically updates incomplete receipts with complete data
- 📈 **Detailed Statistics** - Real-time stats showing updates, duplicates, and new receipts
- 🎨 **Modern UI** - Drag-and-drop interface with live logging
- 🔒 **Privacy First** - All processing happens locally in your browser
- 💾 **No Installation** - Just open and use

## 🚀 Quick Start

### Option 1: Use GitHub Pages (Recommended)

Visit the live tool: **[https://TechStud.github.io/costco-receipt-merger/](https://TechStud.github.io/costco-receipt-merger/)**

### Option 2: Run Locally

1. Download or clone this repository:
```bash
   git clone https://github.com/TechStud/costco-receipt-merger.git
```

2. Open `index.html` in any modern browser (Chrome, Firefox, Edge, Safari)

3. Start merging your receipt files!

## 📖 How to Use

1. **Load Files**
   - Drag and drop your JSON receipt files into the drop zone
   - Or click the drop zone to browse and select files
   - You can load multiple files at once

2. **Review Files**
   - See the list of loaded files with receipt counts
   - Remove any files you don't want to include

3. **Merge**
   - Click "Merge & Download" button
   - Review the statistics in the panel
   - The merged file will automatically download

4. **Check Results**
   - View the detailed log to see what was merged/updated
   - Statistics show: new receipts, updated receipts, and duplicates removed

## 🔧 How It Works

### Intelligent Merge Algorithm

The tool uses a two-pass merge algorithm:

1. **First Pass**: Index all receipts by unique key (`membershipNumber-transactionBarcode`)
2. **Second Pass**: For each receipt:
   - If it exists: Deep merge and calculate completeness scores
   - If merge improves data: Update and mark as "updated"
   - If identical: Skip as duplicate
   - If new: Add to collection

### Completeness Scoring

Each receipt is scored based on:
- Critical fields (transaction data, warehouse info, financial totals)
- Array presence (items, tenders, coupons)
- Nested object completeness (taxes)

When duplicate receipts are found, the tool merges them to create the most complete version possible.

### Data Structure

The tool expects Costco receipt JSON files with this structure:
```json
[
  {
    "transactionBarcode": "...",
    "membershipNumber": "...",
    "transactionDateTime": "...",
    "warehouseName": "...",
    "total": "...",
    "itemArray": [...],
    "tenderArray": [...],
    "subTaxes": {...}
    ...
  }
]
```

## 🎯 Use Cases

- **Testing Multiple Downloads** - Merge receipt files from different test runs
- **Family Account Consolidation** - Combine receipts from multiple family members
- **Data Migration** - Consolidate old and new receipt exports
- **Data Quality** - Update incomplete historical receipts with fresh API data

## 🛠️ Technical Details

- **Technology**: Pure HTML/CSS/JavaScript (no dependencies)
- **Browser Support**: Modern browsers with File API support
- **File Size**: Single HTML file (~15KB)
- **Processing**: Client-side only - no data leaves your device
- **Performance**: Handles thousands of receipts efficiently

## 🔐 Privacy & Security

- **100% Local Processing** - All merging happens in your browser
- **No Server** - No data is uploaded or stored anywhere
- **No Tracking** - No analytics or external requests
- **Secure** - Your receipt data never leaves your device

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Inspired by [TechStud's Costco Receipt Downloader (TCRD)](https://github.com/TechStud/TCRDD/Downloader)
- Built to complement the Costco receipt download workflow

## 📧 Contact

Your Name - [@TechStud](https://github.com/TechStud)

Project Link: [https://github.com/TechStud/costco-receipt-merger](https://github.com/TechStud/costco-receipt-merger)

## ⚠️ Disclaimer

This tool is for personal use only. The author is not affiliated with, endorsed by, or supported by Costco Wholesale Corporation. Use at your own risk.

**SENSITIVE DATA WARNING**: Downloaded receipts contain sensitive purchase and payment data. Keep all files secure and treat them accordingly.

---

**Note**: This tool works when separate JSON files were exported from Costco's receipt system and you want to merge them all into a single file. This project does not download receipts itself - instead use the [Costco Receipt Downloader](https://github.com/TechStud/TCRDD/Downloader) for that purpose.
