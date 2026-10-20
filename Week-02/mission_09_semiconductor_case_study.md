# Mission 9 — Case Study: Predicting Routing Congestion / DRC Hotspots with ML

**Area:** Physical Design (RTL-to-GDSII), placement → routing.

## 1. Engineering problem
After placement, routing may produce congestion and design-rule-check (DRC) violations that are discovered late, after the time-consuming routing step. If designers could predict *where and whether* routability problems will appear right after placement, they could fix placement earlier and avoid costly iterations.

## 2. Data needed
- Placement results (cell/macro locations, densities, pin/net information) converted into per-region features or image-like maps (e.g. RUDY-style wire-density estimates, macro regions).
- Optionally global-routing congestion maps.
- **Labels:** where DRC hotspots/violations actually occurred after detailed routing, from completed runs on many designs.
- Design metadata: technology/tool settings.

## 3. Model output and task type
- Output: a **map** showing the likely location of DRC hotspots/congestion, or an overall routability judgement of a placement.
- Task type: classification (hotspot / no hotspot per region) with a spatial output; closely related to regression of congestion values.
- Learning approach: **supervised** (labels come from finished routed designs). Reported approach in the primary source uses a convolutional neural network (deep learning), which is covered in later weeks.

## 4. What the sources report
- **Primary source:** RouteNet (Xie et al., ICCAD 2018). It uses a convolutional neural network to either assess the overall routability of a placement without running global routing, or predict DRC hotspot locations, taking large macros of mixed-size designs into account. In their benchmark experiments the authors report that overall routability forecasts were similar in accuracy to the global router with much less runtime, and that DRC hotspot prediction accuracy improved by 50 % compared with global routing, outperforming SVM and logistic regression.
- **Secondary source:** the methodological survey *Towards Machine Learning for Placement and Routing in Chip Design* (arXiv 2202.13564) describes RouteNet as the first attempt to use a CNN to forecast DRC-hotspot locations from placement and global-routing information, and places it among other routability-prediction work.

**Status classification (deployed vs research vs proposal):** RouteNet is a **peer-reviewed research demonstration on benchmark circuits**. The sources I read do not establish that it is deployed in a commercial flow, so I do not claim that.

## 5. How results could be evaluated
- Hold out **entire designs** for testing, not random tiles from the same design.
- Metrics: recall of true hotspots (misses are costly), precision (false alarms waste effort), plus comparison with a baseline (e.g. a global-routing estimate or simple density rule).
- Runtime saved vs accuracy lost; spatial accuracy of predicted locations.

## 6. Limitations engineers must investigate
- **Generalisation:** does it work on designs, nodes and tool versions not in the training set? (Drift risk.)
- **Label cost:** training labels require completed routing runs, which are expensive.
- **Class imbalance:** hotspots are a small fraction of tiles, so accuracy alone misleads.
- **Explainability:** engineers need to know *why* a region is flagged to act on it.
- **Benchmarks vs industry reality:** published benchmarks may not represent proprietary, much larger designs.
- Predictions guide decisions but do not replace sign-off routing/DRC.

## 7. Sources
See `sources.md` (entries S8 and S9).
