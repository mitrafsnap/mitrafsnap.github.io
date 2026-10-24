<p align="center">
  <a href="https://mitrafsnap.github.io"><img src="https://img.shields.io/badge/Project%20page-mitrafsnap.github.io-cc3333" alt="Project page"></a>
  <a href="https://github.com/mitrafsnap/demo"><img src="https://img.shields.io/badge/Live%20demo-mitrafsnap%2Fdemo-cc3333" alt="Live demo"></a>
  <a href="https://github.com/mitrafsnap/evaluation"><img src="https://img.shields.io/badge/Evaluation-mitrafsnap%2Fevaluation-cc3333" alt="Evaluation"></a>
</p>

# MitraFSnap project page

Source of **[mitrafsnap.github.io](https://mitrafsnap.github.io)**, the project page for:

> **MitraFSnap. Build Less, Pull Less, Restart Never: Fast Container Image Distribution and
> In-Place Updates**<br>
> The paper is under review.

MitraFSnap updates the data mounted in a running container without replacing the container. It
consists of an OCI compatible builder, a registry and a containerd snapshotter. The builder
packages each model or asset as an independently built and cached allotment with its chunk
index. The registry turns the partition a client selects into a prefetch policy over the
complete image. The snapshotter refreshes a running container, replacing only the changed layers
and invalidating only the changed cached ranges. Across three language models of up to 59 GB
and a video analytics bundle of four models, refresh lowers the update latency by 8.3 to 85.9×
in the cloud and by 7.0 to 265.6× at the edge compared with container replacement.

## Links

| | |
|---|---|
| Project page | https://mitrafsnap.github.io |
| Builder | https://github.com/mitrafsnap/builder |
| Registry | https://github.com/mitrafsnap/registry |
| Snapshotter | https://github.com/mitrafsnap/snapshotter |
| Live demo | https://github.com/mitrafsnap/demo |
| Evaluation | https://github.com/mitrafsnap/evaluation |
| Demo videos | https://mitrafsnap.github.io/#demo |

## Live demo

The [demo](https://github.com/mitrafsnap/demo) runs one vision application with Docker,
eStargz, 2DFS and MitraFSnap at the same time and updates it in four acts. Its dashboard shows
the camera of each method and live charts of downtime, update latency, build time and
downloaded bytes. It runs with Docker on macOS or Linux.

```bash
git clone https://github.com/mitrafsnap/demo.git
cd demo
docker compose up -d --build    # then open http://localhost:8080
```

The [demo README](https://github.com/mitrafsnap/demo#readme) describes the scenarios, the GPU
options and how to run the registry, the builder and the backend on separate machines.

## About this repository

A static site without a build step or a framework, served by GitHub Pages from `main`.

```text
index.html                 page content, the three figures as inline SVG, theme and scroll script
assets/style.css           styles, dark and light themes, method colors as in the paper
assets/fonts/              CMU Sans Serif (SIL Open Font License, OFL.txt)
assets/video/              demo recordings (MP4) and their poster frames
.nojekyll                  tells GitHub Pages to serve the files as they are
```

**Preview locally**

```bash
python3 -m http.server 8000
# open http://127.0.0.1:8000
```

**Update the demo videos.** The recordings come from the demo repository.
`tools/record.py` captures the dashboard during a run, and `tools/encode.sh` writes
`demo.mp4`, `demo-highlight.mp4` and the GIF. Copy `demo.mp4` to `assets/video/traffic.mp4` or
`assets/video/people.mp4`, `demo-highlight.mp4` to `assets/video/traffic-highlight.mp4`, and
take a poster frame from the video. The numbers in the demo table come from
`tools/summary.py` applied to the trace of the same run.

**Figures.** The architecture, selective distribution and refresh figures are drawn as inline
SVG in `index.html` and take their colors from the theme variables in `assets/style.css`, so they
follow the dark and light themes.
