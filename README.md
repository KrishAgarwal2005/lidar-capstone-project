# LiDAR Denoising in Adverse Weather — Capstone CPG No. 5

Interactive showcase for our LiDAR point-cloud denoising capstone at **Thapar
Institute of Engineering & Technology, Patiala**.

Rain corrupts a LiDAR scan two ways at once: droplets create phantom points in
mid-air, and attenuation destroys distant returns outright. We built six
denoisers and measured them not by how good the point cloud *looks*, but by
whether a 3D object detector could still find the cars.

**Live site:** https://krishagarwal2005.github.io/lidar-capstone-project/

## What's in here

A static, dependency-free showcase site:

- **Explorer** — a live 3D point-cloud viewer (three.js) over real KITTI frames
  under physics-simulated rain, at light / moderate / heavy intensities.
- **Live filters** — SOR, ROR and IDSOR running natively in your browser,
  with tunable parameters.
- **Results** — detection-consistency, ablation, supervision-comparison and
  throughput charts driven by the JSON in `data/`.
- **Findings & Method** — the write-up, plus the full report in
  `assets/final_report.pdf`.

## Methods compared

`SOR` · `ROR` · `IDSOR` · `DGCNN` · `PointNet-AE` · `RangeRestoreNet` — evaluated
across 84 paired observations.

## Layout

```
index.html          the whole site
css/style.css       styles
js/app.js           page wiring
js/viewer.js        three.js point-cloud viewer
js/filters.js       in-browser denoising filters
js/charts.js        results charts
data/               point clouds (packed i16/u8/i32) + metrics JSON
assets/             final report
img/                contributor photos
```

Point clouds are stored as packed binary typed arrays (`.xyz.i16`,
`.intensity.u8`, `.label.u8`, `.keep.i32`) with `data/manifest.json` describing
the layout and dequantisation for each.

## Running locally

The site needs to be served over HTTP (the viewer fetches binary data, which
`file://` blocks):

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Contributors

Jayantika · **Krish Agarwal** · Ramyak Sharma · Shardool Dhodawat · Siddhant Singh

## Source

This repository is a copy of the team's showcase site, originally published at
[ramyak-sharma/lidar-denoising-showcase](https://github.com/ramyak-sharma/lidar-denoising-showcase)
([live](https://ramyak-sharma.github.io/lidar-denoising-showcase/)). All work is
the joint output of the five contributors above.

## License

Released under the [MIT License](LICENSE), © 2026 the contributors listed above.
