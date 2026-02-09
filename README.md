# Book Analysis System

Automated deep analysis of trading/ML/finance books (epub & PDF).

## Files

| Script | Purpose |
|--------|---------|
| `deep_book_analyzer.py` | **Main script** — Full chapter-by-chapter deep analysis |
| `extract_van_tharp_psychology.py` | Extract psychology chapters from epub (Van Tharp example) |
| `create_psychology_summary.py` | Generate psychology summary from extracted text |

## Quick Start

### 1. Interactive Mode (Recommended)

```bash
cd "c:\Users\User\Documents\Obsidian Vault\PROJECTS\book-extraction"
python standalone_analyzer.py
```

**Workflow:**
1. Script asks for folder path (default: Downloads)
2. Scans and lists all .epub and .pdf files
3. Shows which books are already analyzed
4. You select which to analyze:
   - `1,3,5` — analyze specific books
   - `1-10` — analyze range
   - `all` — analyze everything
   - `new` — only unanalyzed books
   - `q` — quit

### 2. Auto-Mode (No Prompts)

```bash
python standalone_analyzer.py --auto
```

Analyzes all books in Downloads automatically. Good for overnight runs.

### 3. Specify Folder

```bash
python standalone_analyzer.py --folder "C:\path\to\books"
```

### 4. Python API

```python
from standalone_analyzer import StandaloneAnalyzer
from pathlib import Path

analyzer = StandaloneAnalyzer()
book = Path(r"C:\Users\User\Downloads\some_book.epub")
result = analyzer.analyze_book(book)
analyzer.save_log()
```

## Output Files

All outputs go to: `C:\Users\User\Documents\Obsidian Vault\07-TEMPLATES\book-analysis\`

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

### Van Tharp Analysis

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
- Metrics: 48 mentions
- Exits: 44 mentions

**Chapter 8 Example**:
```
Trading Concepts:
  - entries: 11 mentions
    Example: "...time setup. it certainly is not an entry signal..."
  - psychology: 4 mentions
    Example: "...lotto bias described in chapter 2..."

Key Sentences:
  > "Setups refer to conditions that must occur before other action is taken..."
  > "They are an essential aspect of most entry and exit portions of any system..."
```

## Existing Books Analyzed

Location: `C:\Users\User\Downloads`

| File | Format | Size |
|------|--------|------|
| Van Tharp - Trade Your Way to Financial Freedom | epub | 8.6 MB |
| Stefan mschine learning | epub | 27.1 MB |
| López de Prado - Advances in Financial ML | epub | 13.1 MB |
| Yves Hilpisch - AI in Finance | pdf | 23.7 MB |
| Yves Hilpisch - Python for Algo Trading | pdf | 4.0 MB |
| Yves Hilpisch - Derivatives Analytics | epub | 8.6 MB |
| Yves Hilpisch - Reinforcement Learning | epub | 9.6 MB |
| John Sweeney - Maximum Adverse Excursion | pdf | 1.4 MB |
| volatility.epub | epub | 53.6 MB |

## Dependencies

```bash
pip install ebooklib beautifulsoup4 pymupdf4llm
```

- `ebooklib` — epub parsing
- `beautifulsoup4` — HTML/XML extraction
- `pymupdf4llm` — PDF-to-markdown (optional but recommended)

## Notes

- **PDFs require pymupdf4llm**: Without it, PDFs are skipped
- **Re-analysis**: Books are logged. If already analyzed, script asks to re-analyze or skip
- **Windows UTF-8**: Script auto-configures UTF-8 console output on Windows
- **Long-running**: Large books (50+ MB) can take 5-10 minutes each

## Advanced: Custom Topics

Edit `TRADING_TOPICS` or `ML_TOPICS` dictionaries in `deep_book_analyzer.py` to add your own concepts to track.

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
