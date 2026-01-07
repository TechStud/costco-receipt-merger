# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.2.3] - 2026-01-07

### Added
- Structured per-file summary logging in merge output
- Receipt date range display (oldest → newest) in file list
- Merge log enhanced with aligned multi-line formatting
- Canonical schema lock enforcement with lossless merge first / normalize last
- Progress indicator during merge (non-intrusive)
- Prevent duplicate file re-select warnings even when selecting the same file
- Output filename timestamped (`Costco_Receipts_MERGED_YYYY-MM-DD.json`)

### Changed
- Refactored merge logic to ensure:
  - Merge precedes normalization
  - All canonical arrays always present
  - Partial receipt data is preserved
  - Order of items in `itemArray` preserves adjacency context
- Updated UX terminology & visuals
- Logging cleaned up (no noise during file selection)
- Merge & Save button usability improved
- Clear button resets all state properly

### Fixed
- Fixed duplicate selection warning not firing for same file re-selection
- Fixed edge cases in handling missing dates
- Merged sort behavior to ensure consistent oldest → newest ordering

---

## [0.1.0] - 2025-12-20

### Added
- Initial release
- Drag-and-drop file interface
- Intelligent receipt merging with deep merge algorithm
- Completeness scoring system
- Real-time statistics panel
- Detailed logging console
- Multi-member support
- Automatic duplicate detection and removal
- Smart filename generation
- Modern gradient UI with animations

### Features
- Client-side only processing (privacy-first)
- No dependencies - pure HTML/CSS/JavaScript
- Support for multiple JSON files
- Chronological sorting of merged receipts
- Visual feedback for all operations

