# Documentation

Materials for the **Sprout** Internship 1 technical report (English LaTeX, 12pt Times New Roman).

Build and setup: **[repository README](../README.md#build-the-report)**.

## Layout

| Path | Description |
|------|-------------|
| [`report/source/`](report/source/) | LaTeX source (`main.tex`, `sections/`, `diagrams/`, `Makefile`) |
| [`report/exports/sprout-internship-final-report.pdf`](report/exports/sprout-internship-final-report.pdf) | Submission PDF (`make export`) |
| [`references/reviews/internship-report-review.pdf`](references/reviews/internship-report-review.pdf) | Reviewer feedback |
| [`references/thesis-templates/DATH/`](references/thesis-templates/DATH/) | BK formatting reference (not Sprout content) |

## Chapters

1. Introduction  
2. Literature Review  
3. System Context and Use Cases  
4. Methodology  
5. Implementation Details  
6. Evaluation Methodology  
7. Discussion  
8. Operations and Reproducibility  
9. Conclusion and Future Work  

**Student:** Nguyen Thanh Minh Duc (2470734) · **Advisor:** Quản Thành Thơ · **Reviewer:** Trương Quang Khải

## Quick commands

```bash
cd docs/report/source
make export    # build PDF and copy to report/exports/
```
