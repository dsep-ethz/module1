# Module 1: Cloud-native data in R

This module introduces tools for finding, querying, and analysing large remote datasets without downloading them in full. These tools are useful across many fields; here, we learn them by examining how biodiversity data are produced, accessed, and used in policy.

The main lesson is in [`module1.qmd`](module1.qmd).

## Learning goals

By the end of the module, you will be able to:

- distinguish a data catalogue or API from the location where data are stored;
- query remote Parquet data with Arrow and familiar `dplyr` verbs;
- search a STAC catalogue and read a small window from satellite imagery;
- query and join socio-political indicators;
- explain how data infrastructure shapes what becomes visible in policy; and
- communicate a focused result, its policy relevance, and its limitations.

## Sessions

1. **GBIF:** query biodiversity occurrence records stored as remote Parquet files.
2. **STAC and NDVI:** find Sentinel-2 imagery and read only the pixels needed for a small area.
3. **Socio-political data:** search and query World Bank indicators.
4. **Data, society, and policy:** investigate one social or political dimension of biodiversity data using ideas from *A political ecology of data*.

Sessions 1–3 can be completed independently. Session 4 builds mainly on Sessions 1 and 3; satellite imagery is optional.

## Getting started

1. Open [`module1.Rproj`](module1.Rproj) in RStudio.
2. Open [`module1.qmd`](module1.qmd).
3. Run the installation chunk once if you do not already have the required packages.
4. Restart R, then work through the document from the beginning.

Required R packages:

```r
install.packages(c(
  "tidyverse",
  "arrow",
  "rstac",
  "terra",
  "httr2",
  "WDI"
))
```

You also need Quarto and an internet connection that can reach GBIF's public S3 bucket, Earth Search, and the World Bank API.

## How to work

Work with a partner using driver and navigator roles, switching regularly. The exercises move from guided examples, to code with blanks, to an open query of your own.

The recurring workflow is:

1. **Find** the data through documentation or a catalogue.
2. **Connect** R to the relevant service or files.
3. **Narrow** the request before transferring data.
4. **Collect** or read only a manageable result.

Do not call `collect()` on the full GBIF dataset. The module saves selected small results in a local `cache/` directory so expensive queries do not need to be repeated.

## Final output

With your partner, complete one analysis of a social or political dimension of biodiversity data. Submit your question, code, figure or table, short policy interpretation, and at least two limitations. Relate your interpretation to one idea from *A political ecology of data* and present the result in three minutes.

## (Un)grading rubric

This rubric is for reflection and feedback, not for adding up points. Use it to identify evidence of your learning and decide what you would improve next. Productive mistakes, revisions, and well-explained limitations are evidence of learning.

| Dimension | Compelling evidence | Some evidence | Not yet evident |
|---|---|---|---|
| **Question and scope** | The question is focused, socially or politically meaningful, and answerable at the chosen scale. | The topic is relevant, but the question or scale needs clarification. | The question is missing or cannot be answered with the selected data. |
| **Cloud-native workflow** | The analysis finds, narrows, and reads or collects only the data needed; the group can explain where computation and transfer occur. | The workflow runs, but some choices or data movements are unclear or inefficient. | The workflow attempts to download or collect an unmanageably large dataset, or cannot be explained. |
| **Analysis and communication** | The code is reproducible, and the figure or table clearly supports the stated finding. | The analysis is mostly reproducible, but the output or connection to the finding needs refinement. | The result cannot be reproduced or does not support the claim. |
| **Political ecology of data** | The interpretation uses a specific idea from the reading to examine production, infrastructure, governance, visibility, or power. | The reading is mentioned, but its connection to the result remains general. | The interpretation treats the data as neutral or does not engage with the reading. |
| **Policy interpretation and limits** | The group distinguishes observation from explanation, proposes a proportionate policy implication, and discusses at least two meaningful limitations. | A policy implication and limitations are present but need stronger links to the evidence. | The analysis makes causal or policy claims beyond what the evidence supports, or omits limitations. |
| **Collaboration and presentation** | Both partners can explain the workflow and decisions; the three-minute presentation communicates the question, finding, interpretation, and an important limitation. | Participation or explanation is uneven, or one required presentation element is unclear. | One person cannot explain the work, or the presentation does not communicate the central result. |

## Render the document

Use RStudio's **Render** button, or run:

```sh
quarto render module1.qmd
```

Rendering executes the enabled code chunks and contacts remote data services, so it can take time. Exercise chunks containing `___` are intentionally disabled until completed.

## Troubleshooting

- If a network check returns `NA`, the service may be blocked by your network.
- If a remote query is too large, filter and summarise before calling `collect()`.
- If no satellite scenes are found, widen the date range, increase the cloud limit, or enlarge the bounding box.
- If a cached result is stale, delete the relevant file in `cache/` and rerun that chunk.