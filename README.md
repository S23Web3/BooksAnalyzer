# Book Analyzer

Automated deep analysis of trading/ML/finance books (epub & PDF). Runs 100% locally — no API credits needed.

## Quick Start

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Run Analyzer

**Option 1: Interactive Mode** (Recommended)

```bash
python standalone_analyzer.py
```

**Workflow:**
1. Enter folder path to scan (or press Enter for current directory)
2. View list of found .epub and .pdf files
3. Select which books to analyze:
   - `1,3,5` — analyze specific books
   - `1-10` — analyze range
   - `all` — analyze everything
   - `new` — only unanalyzed books
   - `q` — quit

**Option 2: Auto Mode** (No Prompts)

```bash
python standalone_analyzer.py --auto
```

Analyzes all books in current directory. Good for batch processing.

**Option 3: Specify Folder**

```bash
python standalone_analyzer.py --folder "/path/to/books"
```

**Option 4: Windows Launcher**

Double-click `analyze_books.bat` (Windows only)

## Output

All results saved to: `./book-analysis/` (in same directory as script)

| File | Content |
|------|---------|
| `{book_name}_DEEP.json` | Full JSON analysis (all chapters, concepts, examples) |
| `{book_name}_SUMMARY.md` | Human-readable markdown summary |
| `MASTER_ANALYSIS_SUMMARY.md` | Table of all analyzed books sorted by rating |
| `deep_analysis_log.json` | Analysis log (prevents re-analysis) |

## What It Analyzes

### Trading Concepts Extracted
- **entries**: Entry signals, triggers, patterns
- **exits**: Stop loss, take profit, trailing stops
- **risk**: Position sizing, drawdown, risk management
- **backtesting**: Walk-forward, optimization, overfitting
- **metrics**: Sharpe, Sortino, expectancy, SQN, R-multiples
- **psychology**: Discipline, bias, emotion, mental models

### ML Concepts Extracted
- **supervised**: Classification, regression, labeled data
- **features**: Feature engineering, selection, importance
- **models**: Random forest, XGBoost, neural networks
- **validation**: Cross-validation, purging, k-fold
- **metrics**: Accuracy, precision, recall, F1, SHAP

### Code & Formula Detection
- Searches for Python code blocks (`def`, `class`, `import`)
- Detects LaTeX formulas (`$...$`, `\\frac`, `\\sum`)

### Key Sentences Extraction
Finds sentences with critical keywords:
- "key", "important", "critical", "must", "essential"
- "note that", "remember", "always", "never"

## Rating System (1-10)

| Points | Category | Criteria |
|--------|----------|----------|
| 0-4 | Concept Coverage | Trading + ML concepts found across chapters |
| 0-2 | Code/Formulas | Chapters with executable code or math formulas |
| 0-2 | Key Sentences | Actionable insights extracted |
| 0-2 | Breadth | Covers multiple trading + ML topics |

**Total**: 1-10 (rounded)

## Example Output

### Sample Analysis

**Rating**: 10/10

**Summary Stats**:
- Trading concepts: 108
- ML concepts: 15
- Chapters with code: 15/30
- Chapters with formulas: 17/30

**Top Concepts**:
- Psychology: 106 mentions
- Entries: 92 mentions
- Risk: 62 mentions

**Files Generated**:
- `book_name_analysis.json` — full data
- `book_name_summary.md` — human-readable summary
- `MASTER_SUMMARY.md` — table of all analyzed books

## Dependencies

```bash
pip install -r requirements.txt
```

Includes:
- `ebooklib` — epub parsing
- `beautifulsoup4` — HTML/XML extraction
- `pymupdf4llm` — PDF-to-markdown conversion

## Notes
- **Re-analysis**: Books are logged. If already analyzed, script asks to re-analyze or skip
- **Windows UTF-8**: Script auto-configures UTF-8 console output on Windows
- **Long-running**: Large books (50+ MB) can take 5-10 minutes each

## Advanced: Custom Topics

Edit `TRADING_TOPICS` or `ML_TOPICS` dictionaries in `standalone_analyzer.py` to add your own concepts to track.

Example:
```python
TRADING_TOPICS = {
    'crypto': ['bitcoin', 'ethereum', 'altcoin', 'defi', 'perpetual'],
    'hft': ['latency', 'tick data', 'order book', 'market making'],
}
```

## Todo: Future Enhancements

- [ ] Compare multiple books side-by-side
- [ ] Extract code snippets to separate files
- [ ] Generate concept frequency heatmap
- [ ] Auto-detect book category (trading/ML/general)
- [ ] PDF OCR for image-based PDFs
- [ ] Multi-language support (detect non-English books)

---

**Last Updated**: 2026-02-09
