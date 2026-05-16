# Data Visualization

[Source: WORK/BOOKS/[TEC TUF] the visual display of quantitative information.pdf]

**Central thesis (Tufte):** Graphical excellence = complex ideas communicated with clarity, precision, and efficiency. The purpose of a statistical graphic is to reveal data — not to decorate, impress, or signal methodological sophistication.

## Core Principles of Graphical Excellence

1. **Show the data** — the data is the substance; everything else is scaffolding
2. **Induce the viewer to think about substance, not methodology or graphic design**
3. **Avoid distorting what the data have to say**
4. **Present many numbers in a small space**
5. **Make large data sets coherent**
6. **Encourage the eye to compare different pieces of data**
7. **Reveal data at several levels of detail** — from broad overview to fine structure
8. **Serve a clear purpose**: description, exploration, tabulation, or decoration
9. **Be closely integrated with statistical and verbal descriptions of the data set**

## Anscombe's Quartet

Four datasets with identical summary statistics (mean, variance, correlation, linear regression) but radically different distributional structure visible only in graphical form:

| Dataset | Pattern |
|---------|---------|
| I | Linear, moderate scatter (the "normal" case the statistics describe) |
| II | Quadratic — clear curve that linear stats ignore |
| III | Almost perfect linear, one extreme outlier distorting slope |
| IV | All points at same x-value except one outlier at distant x |

**The lesson:** summary statistics alone cannot substitute for graphical examination of data. The regression line is identical across all four. The data are categorically different. Graphics reveal what statistics obscure.

## Data-Ink Ratio

**Data-ink** = ink in the graphic that represents data. **Non-data-ink** = ink that does not represent data.

**Data-ink ratio = data-ink / total ink in graphic**

Graphical excellence maximizes the data-ink ratio within reason. Every non-data element must earn its place — if removal would not cost information, remove it.

**Erasure test:** would erasing this element lose data? If no → erase it.

**Non-data-ink categories (reduce or eliminate):**
- Grid lines heavier than the data
- Tick marks that duplicate axis labels
- Redundant axis labels
- Box borders around the plot area
- Background fills
- Legend boxes (integrate labels directly)
- Shadows and 3D effects

## Chartjunk

Tufte's term for graphical decoration that does not encode data:

- **Vibrations** — moiré patterns, heavy grid lines that produce optical interference
- **Grids** — most grids should be eliminated or made nearly invisible; they organize the page, not the data
- **The Duck** — graphics whose design element overpowers the data (Tufte: "chart that has been jazzed up")

**Chartjunk as corruption:** it clutters the graphic, obscures the data signal, and signals that the designer is unconfident in the data's ability to speak for itself.

## Data Density and Small Multiples

**Data density** = number of data points / unit area of graphic. High data density graphics are the most valuable because they enable comparison at scale.

**Small multiples:** a series of graphics with identical design and scale, varying only in the variable of interest. Allow the eye to detect pattern, variation, and exception across many cases simultaneously.

- Same axis scales across all panels (critical — rescaling per panel removes comparability)
- Minimal labels; the eye moves across panels without interruption
- Size each panel to the data, not to the page

Examples: sparklines (time-series in-text), trellis displays, geographic small multiples.

## Graphical Integrity

**The Lie Factor** = size of effect shown in graphic / size of effect in the data

A Lie Factor of 1.0 = accurately represented. Factors >1 = exaggerated; <1 = suppressed.

**Common integrity violations:**
- Truncated axes — y-axis starting at a non-zero value to exaggerate differences
- Area encoding of 1D data — bar width as well as height encodes value, doubling the apparent effect
- Perspective distortion — 3D charts distort relative magnitudes
- Inconsistent time scales — non-uniform spacing on x-axis implies linear time when it is not

**Rule:** the representation of numbers, as physically measured on the surface of the graphic itself, should be directly proportional to the numerical quantities represented.

## The Sparkline

Small, word-sized graphic embedded in text. Designed to be read in context, not isolated. Communicates trend without requiring a dedicated figure.

Characteristics: no axes, no labels, 6–8× the height of the x-dimension, designed to communicate the shape of a time series rather than precise values.

## Graphical Forms

**The best graphic:** the one that reveals the most data with the fewest graphical elements.

| Form | Best use |
|------|---------|
| Scatter plot | Relationship between two continuous variables |
| Time-series | Temporal trend |
| Small multiples | Comparison across many similar cases |
| Map | Spatial distribution |
| Table | Precise values for small data sets; lookup |

**Pie charts:** avoid. Angular differences are harder to judge than linear differences; only work for 2-3 slices; bar charts are uniformly superior for the same data.

## Typography in Graphics

Labels should be smaller than the data. The data is the signal; labels are the decoding apparatus. Typeface choice: serif or sans-serif with high legibility at small sizes. Rotate axis labels only when necessary (left-axis label: horizontal text > rotated text).

## Sources

- `WORK/BOOKS/[TEC TUF] the visual display of quantitative information.pdf` — Tufte, 1983
