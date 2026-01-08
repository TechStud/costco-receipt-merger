# 🧾 Costco Receipt Merger

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Version](https://img.shields.io/badge/version-0.2.3-green.svg)
[![Changelog](https://img.shields.io/badge/changelog-updates-brightgreen)](CHANGELOG.md)

A **browser-based tool** for intelligently merging multiple local Costco receipt JSON files (including from additional family members) into a single canonical, deduplicated, and schema-complete dataset.

All processing is done **locally in your browser** — no data ever leaves your machine.

---

## ✨ Features

| _Feature_                    	| _Description_                                                                                                                                                                                                                                                                                       	|
|------------------------------	|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| 🔍 **Smart Deduplication**    	| * Merges all Receipts, then deduplicates to create the most complete version possible.<br>* Receipts are uniquely identified using membershipNumber + transactionBarcode as unique key<br> ↳ Good for multi-member families to merge all receipts into a single file.                               	|
| 📄 **Schema-Complete Output** 	| * The final JSON conforms to a locked canonical schema with all expected fields present                                                                                                                                                                                                             	|
| 🔀 **Lossless Merge Logic**   	| * Scalars prefer non-null values<br>* Objects are deep-merged<br>* Arrays are merged intelligently:<br> ↳ `itemArray` preserves adjacency and order<br> ↳ `couponArray` and `tenderArray` merge by identity                                                                                         	|
| 🎨 **Modern UI**              	| * **Drag-and-Drop** interface with **Per-File Context**<br> ↳ Receipt count per file<br> ↳ Oldest --> newest transaction date range<br><br>* **Structured Merge Logs**<br> ↳ Clean, column-aligned summaries<br> ↳ Easy to digest or copy for reference<br><br>* **Progress Feedback** during merge 	|
| 🔐 **Privacy First**          	| * All processing happens locally in your browser                                                                                                                                                                                                                                                    	|
| 👍 **No Installation**        	| * Just open and use                                                                                                                                                                                                                                                                                 	|

## 🚀 Quick Start

### Option A - Use Hosted Version

- Visit the live tool: **[https://TechStud.github.io/costco-receipt-merger/](https://TechStud.github.io/costco-receipt-merger/)**

### Option B - Run Locally

1. Clone the repository:
```bash
   git clone https://github.com/TechStud/costco-receipt-merger.git
```

2. Open the Costco Receipt Merger `index.html` in any modern browser (Safari, Chrome, Firefox, Edge)

3. Start merging your receipt files!

## 📖 How to Use

**NOTE:** The **_Costco Receipt Merger_** tool assumes you already have two or more Costco Receipt JSON files to select, in order to work.

1. **Add Receipt Files**
   - Drag and drop two or more of your Costco Receipt JSON files into the drop zone
   - Or click the drop zone to browse and select files

2. **Review Files**
   - Each file will show the Receipt Counts and Transaction Date range
   - Remove any files you don't want to include before merging

3. **Merge & Save**
   - Click "Merge & Save" button
   - Review the structured merge summary in the log panel below

4. **Download**
   - A single merged file will be automatically saved with a date-stamped name (eg: Costco_Receipts_MERGED_YYYY-MM-DD.json)


## 📌 Example Merge Log Output

```
[9:21:36 AM] Merge started
[9:21:36 AM] Total receipt files selected: 2

[9:21:36 AM]  1. costco-receipts-2025-02-24.json
[9:21:36 AM]     ↳     9 Receipts · 2025-02-01 → 2025-02-22
[9:21:36 AM]  2. costco-receipts-2025-11-18.json
[9:21:36 AM]     ↳   857 Receipts · 2022-01-02 → 2025-11-15

[9:21:36 AM] Total receipts across all files: 866

[9:21:36 AM] Merge complete
[9:21:36 AM] ↳ 861 unique receipts produced
[9:21:36 AM] ↳ Output file: Costco_Receipts_MERGED_2026-01-07.json
```


## 🧠 How It Works

1. Lossless Merge Phase
   - All receipts from all files are evaluated together
   - Receipts sharing the same identity key are merged
   - More complete data is preserved without overwriting existing values

2. Canonical Normalization (Terminal Step)
   - After merging, receipts are normalized into a fixed schema
   - Missing fields become null
   - All expected arrays exist, even if empty

3. Final Output
   - Receipts are sorted oldest → newest
   - Output is saved as a single, clean JSON file

## 🔐 Privacy & Security

- **100% Local Processing** - All merging happens in your browser
- **No Server** - No data is uploaded or stored anywhere
- **No Tracking** - No analytics or external requests
- **Secure** - Your receipt data never leaves your device

## 📦 Related Tools

If you need to **download** your Costco receipts first, visit this tool:
- **Costco Receipt Downloader (TCRD)**
https://techstud.github.io/TCRDD/Downloader/

## 🎯 Use Cases

- **Testing Multiple Downloads** - Merge receipt files from different test runs
- **Family Account Consolidation** - Combine receipts from multiple family members
- **Data Migration** - Consolidate old and new receipt exports
- **Data Quality** - Update incomplete historical receipts with fresh API data

## 🛠️ Technical Details

- **Technology**: Pure HTML/CSS/JavaScript (no dependencies)
- **Browser Support**: Modern browsers with File support
- **File Size**: Single HTML file
- **Processing**: Client-side only - no data leaves your device
- **Performance**: Handles thousands of receipts efficiently


## 🤝 Contributing

Contributions are welcome! 

1. **Fork** the repository
2. **Create** your feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your changes (`git commit -m 'Add some AmazingFeature'`)
4. **Push** to the branch (`git push origin feature/AmazingFeature`)
5. **Submit** a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Inspired by [TechStud's Costco Receipt Downloader (TCRD)](https://github.com/TechStud/TCRDD/Downloader)
- Built to complement the Costco receipt download workflow.

## ⚠️ Disclaimer

This tool is for personal use only. The author and this project are not affiliated with, endorsed or supported by Costco Wholesale Corporation. Use at your own risk.

**SENSITIVE DATA WARNING**: Downloaded receipts contain sensitive purchase and payment data. Keep all files secure and treat them accordingly.

---

**Note**: This tool works when separate JSON files were exported from Costco's receipt system and you want to merge them all into a single canonical, deduplicated, and schema-complete dataset file. This project does not download receipts itself - instead use the [Costco Receipt Downloader](https://github.com/TechStud/TCRDD/Downloader) for that purpose.
