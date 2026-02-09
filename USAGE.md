# Book Analyzer - Quick Guide

## 🎯 What It Does
Analyzes trading/ML/finance books completely locally (no API credits).
- Deep chapter-by-chapter analysis
- Extracts trading & ML concepts
- Rates books 1-10
- Generates JSON + Markdown summaries

## ⚡ Quick Start

### Windows (Double-Click)
Just double-click: **`analyze_books.bat`**

### Command Line
```bash
python standalone_analyzer.py
```

## 📖 Interactive Workflow

```
Step 1: Enter folder path
> C:\Users\User\Downloads
(or press Enter for default)

Step 2: View found books
================================================================================
FOUND 13 BOOKS
================================================================================
 1. Van Tharp - Trade Your Way.epub (8.6 MB)
 2. Stefan ML.epub (27.1 MB) [Already analyzed: 10/10]
 3. De Prado - Advances in ML.epub (13.1 MB) [Already analyzed: 10/10]
 ...

Step 3: Select books to analyze
> 1,5,7        (analyze books 1, 5, 7)
> 1-5          (analyze books 1 through 5)
> all          (analyze all books)
> new          (only unanalyzed books)
> q            (quit)

Step 4: Watch analysis
[1/3] Analyzing Van Tharp...
  📖 Reading: Van Tharp - Trade Your Way.epub
  ✓ Extracted 30 chapters
  📊 RESULTS:
     Trading concepts: 109
     ML concepts: 15
  🎯 RATING: 10/10
  ✓ Saved: Van_Tharp_analysis.json

Step 5: View results
Output folder: 07-TEMPLATES\book-analysis\
  - Van_Tharp_analysis.json
  - Van_Tharp_summary.md
  - MASTER_SUMMARY.md
```

## 🚀 Advanced Usage

### Auto-Mode (No Prompts)
```bash
python standalone_analyzer.py --auto
```

### Custom Folder
```bash
python standalone_analyzer.py --folder "D:\My Books"
```

### Python Script
```python
from standalone_analyzer import StandaloneAnalyzer
analyzer = StandaloneAnalyzer()
result = analyzer.analyze_book("path/to/book.epub")
```

## 📊 Output Files

All saved to: `07-TEMPLATES\book-analysis\`

| File | Content |
|------|---------|
| `{book}_analysis.json` | Full analysis data |
| `{book}_summary.md` | Human-readable summary |
| `MASTER_SUMMARY.md` | Table of all books by rating |
| `analysis_log.json` | Prevents re-analyzing same books |

## 🎯 Rating System

| Points | What It Measures |
|--------|------------------|
| 0-4 | Trading + ML concepts found |
| 0-2 | Code & formulas present |
| 0-2 | Key actionable sentences |
| 0-2 | Breadth (multiple topics) |
| **Total** | **1-10** |

## 📚 Your Library Results

| Rating | Book |
|--------|------|
| 10/10 | De Prado — Advances in Financial ML |
| 10/10 | Jansen — ML for Algo Trading |
| 10/10 | Van Tharp — Trade Your Way |
| 9/10 | Hilpisch — Derivatives Analytics |
| 9/10 | Hilpisch — RL for Finance |
| 6/10 | Volatility (Hilpisch) |

## 🔧 Dependencies

```bash
pip install ebooklib beautifulsoup4
pip install pymupdf4llm  # Optional, for PDFs
```

## ❓ FAQ

**Q: Does it use API credits?**
A: No! 100% local processing.

**Q: Can I re-analyze a book?**
A: Yes. Books are logged, but you can select already-analyzed books to update them.

**Q: What file types?**
A: `.epub` (always works) and `.pdf` (needs pymupdf4llm installed)

**Q: How long does it take?**
A: ~30 seconds per book for small books, up to 2 minutes for large ones (50+ MB).

**Q: Can I analyze books in multiple folders?**
A: Yes. Run the script multiple times, or move all books to one folder first.

## 🎨 Customization

Edit `TRADING_CONCEPTS` and `ML_CONCEPTS` dictionaries in `standalone_analyzer.py` to track different concepts.

Example:
```python
TRADING_CONCEPTS = {
    'crypto': ['bitcoin', 'ethereum', 'defi'],
    'hft': ['latency', 'order book', 'market making'],
}
```

## 📝 Notes

- Books are logged — won't re-analyze unless you select them again
- PDFs require `pymupdf4llm` (install separately)
- Large books (50+ MB) take longer but work fine
- UTF-8 is auto-configured for Windows console

---

**Need Help?** Check `README.md` for full documentation.
