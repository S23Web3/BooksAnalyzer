# Book Analyzer

> Deep analysis of trading/ML/finance books — 100% local, no API credits

Automated chapter-by-chapter concept extraction from epub and PDF books. Runs entirely on your machine.

## Features

- 🔍 **Deep Analysis** — Chapter-by-chapter concept extraction
- 📊 **Smart Rating** — 1-10 rating based on content depth
- 💾 **100% Local** — No API calls, no external services
- 📝 **Rich Output** — JSON data + Markdown summaries
- 🔄 **Smart Logging** — Won't re-analyze books unless requested
- 🎯 **Interactive** — Choose which books to analyze

## Quick Start

```bash
git clone https://github.com/S23Web3/BooksAnalyzer.git
cd BooksAnalyzer
pip install -r requirements.txt
python standalone_analyzer.py
```

## How It Works

1. **Scan** — Point it at a folder with .epub or .pdf files
2. **Select** — Choose which books to analyze (1,3,5 or 1-10 or all)
3. **Analyze** — Extracts chapters, finds concepts, detects code/formulas
4. **Rate** — Generates 1-10 rating based on depth
5. **Export** — Creates JSON + Markdown summaries

## Output

All results saved to `./book-analysis/`:

```
book-analysis/
├── Book_A_analysis.json        # Full data
├── Book_A_summary.md           # Human-readable
├── MASTER_SUMMARY.md           # All books ranked
└── analysis_log.json           # Prevents duplicates
```

## What It Extracts

### Trading Concepts
- Entries (signals, triggers, patterns)
- Exits (stop loss, take profit)
- Risk (position sizing, drawdown)
- Backtesting (optimization, walk-forward)
- Metrics (Sharpe, expectancy, win rate)
- Psychology (discipline, bias, emotion)

### ML Concepts
- Supervised (classification, regression)
- Features (engineering, selection, importance)
- Models (XGBoost, random forest, neural nets)
- Validation (cross-validation, k-fold, purging)
- Metrics (accuracy, precision, SHAP)

### Plus
- Code detection (Python, formulas)
- Key sentence extraction
- Concept frequency analysis

## Rating System

| Points | Criteria |
|--------|----------|
| 0-4 | Trading + ML concept coverage |
| 0-2 | Code & formula presence |
| 0-2 | Key actionable sentences |
| 0-2 | Topic breadth |
| **1-10** | **Total rating** |

## Usage Modes

### Interactive (Recommended)
```bash
python standalone_analyzer.py
```
- Asks for folder
- Lists all books
- You choose which to analyze

### Auto Mode
```bash
python standalone_analyzer.py --auto
```
- Analyzes everything in current directory
- No prompts

### Specify Folder
```bash
python standalone_analyzer.py --folder "/path/to/books"
```

### Windows
Double-click `analyze_books.bat`

## Customization

Edit `TRADING_CONCEPTS` and `ML_CONCEPTS` in `standalone_analyzer.py`:

```python
TRADING_CONCEPTS = {
    'your_topic': ['keyword1', 'keyword2', 'keyword3'],
}
```

## Requirements

- Python 3.7+
- ebooklib (epub parsing)
- beautifulsoup4 (HTML extraction)
- pymupdf4llm (PDF conversion)

Install: `pip install -r requirements.txt`

## Example Output

```
FOUND 5 BOOKS
================================================================================
 1. Book_A.epub (8.6 MB)
 2. Book_B.epub (27.1 MB) [Already analyzed: 10/10]
 3. Book_C.pdf (13.1 MB)

Select books to analyze:
> 1,3

[1/2] Analyzing Book_A...
  📖 Reading: Book_A.epub
  ✓ Extracted 30 chapters
  📊 RESULTS:
     Trading concepts: 109
     ML concepts: 15
  🎯 RATING: 10/10
  ✓ Saved: Book_A_analysis.json
```

## License

MIT License — see [LICENSE](LICENSE)

## Author

S23Web3

## Contributing

Issues and PRs welcome!
