# Segmentation of nuclei

Beginning the workflow, we want to start by **detecting cell nuclei** as individual objects. Cell nuclei in a fluorescence image are clearly brighter than the surrounding background so many automated thresholding algorithms will be successful in finding the correct thresholding values. However, we will add several post-processing steps to make sure that the edges of the detected nuclei are smooth and that the small bright particles in the background are not mistakenly classified as nuclei.

<script src="https://fast.wistia.com/embed/medias/ogftgh3nwb.jsonp" async></script><script src="https://fast.wistia.com/assets/external/E-v1.js" async></script><div class="wistia_responsive_padding" style="padding:56.25% 0 0 0;position:relative;"><div class="wistia_responsive_wrapper" style="height:100%;left:0;position:absolute;top:0;width:100%;"><div class="wistia_embed wistia_async_ogftgh3nwb seo=false videoFoam=true" style="height:100%;position:relative;width:100%"><div class="wistia_swatch" style="height:100%;left:0;opacity:0;overflow:hidden;position:absolute;top:0;transition:opacity 200ms;width:100%;"><img src="https://fast.wistia.com/embed/medias/ogftgh3nwb/swatch" style="filter:blur(5px);height:100%;object-fit:contain;width:100%;" alt="" aria-hidden="true" onload="this.parentNode.style.opacity=1;" /></div></div></div></div>

## Analysis pipeline steps

### PartSeg: ROI mask extraction
- Median filtering (r = 2)
- Thresholding ‘Otsu’
- Opening (r = 5)
- Hill holes (r = 100)
- Size restriction (>400)
- Connect by sides
- Convex hull (r = 1)

