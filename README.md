# MPD Arrest Report Data Repository

This repository contains arrest report PDFs from the Metropolitan Police Department (MPD) of Washington, DC.

## Data Overview
- **Time Period**: October 2019 - September 2024
- **Districts**: 1D, 2D, 3D, 4D, 5D, 6D, 7D
- **Total PDFs**: ~5,254 files
- **Total Size**: ~240 MB
- **Storage**: Git LFS (Large File Storage)

## Directory Structure
```
├── 1D/          # First District arrest reports
├── 2D/          # Second District arrest reports
├── 3D/          # Third District arrest reports
├── 4D/          # Fourth District arrest reports
├── 5D/          # Fifth District arrest reports
├── 6D/          # Sixth District arrest reports
└── 7D/          # Seventh District arrest reports
```

## File Naming Convention
- **Standard format (2019-2020)**: `[DISTRICT]-arrest-YYYYMMDD.pdf`
  - Example: `1D-arrest-20200315.pdf`
- **Thread format (2021+)**: `d[DISTRICT]-t[THREAD]-n[NUMBER]-YYYYMMDD.pdf`
  - Example: `d1D-t42-n1234-20240815.pdf`

## Data Source
Data scraped from official MPD Google Groups using the "Preliminary Arrest Report" threads:
- https://groups.google.com/g/official-mpd-1d
- https://groups.google.com/g/official-mpd-2d
- https://groups.google.com/g/official-mpd-3d
- https://groups.google.com/g/official-mpd-4d
- https://groups.google.com/g/official-mpd-5d
- https://groups.google.com/g/official-mpd-6d
- https://groups.google.com/g/official-mpd-7d

## Usage

### Cloning with Git LFS
```bash
# Ensure Git LFS is installed
git lfs install

# Clone the repository (PDFs will be downloaded automatically)
git clone https://github.com/donaldbraman/mpd-arrest-data.git
```

### Selective Download
To clone without downloading all PDFs immediately:
```bash
GIT_LFS_SKIP_SMUDGE=1 git clone https://github.com/donaldbraman/mpd-arrest-data.git
cd mpd-arrest-data

# Then pull specific files as needed
git lfs pull --include="1D/*.pdf"  # Just District 1D
git lfs pull --include="*/1D-arrest-202403*.pdf"  # Just March 2024 from 1D
```

## Related Repositories
- **Processing Pipeline**: https://github.com/donaldbraman/mpd-data-pipeline
  - Contains code for scraping, parsing, and harmonizing arrest data
  - Converts PDFs to structured parquet format

## Data Observations
- **District 1D**: Only district with continuous data through 2024
- **Districts 2D-7D**: Data collection appears to have stopped in late 2020/early 2021
- **Format Change**: Starting in 2021, District 1D adopted a new thread-based naming format

## License
This data is collected from public government sources. The original arrest reports are public records published by the Metropolitan Police Department of Washington, DC.

## Contributing
To add new arrest reports:
1. Place PDFs in the appropriate district directory
2. Follow the existing naming convention
3. Commit with descriptive message: `Add [District] arrest reports for [date range]`
4. Push to repository (files will be uploaded via Git LFS)

## Contact
For questions about the data collection process or pipeline, see the [mpd-data-pipeline](https://github.com/donaldbraman/mpd-data-pipeline) repository.