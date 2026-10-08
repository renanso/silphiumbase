# Local Silphium genome browser

The browser page uses the reference assembly and gene annotation in `data/`:

- `genome.fasta.gz`, `genome.fasta.gz.fai`, and `genome.fasta.gz.gzi`
- `sorted.gff3.gz` and its CSI index, `sorted.gff3.gz.csi`

Serve the workspace over HTTP so IGV.js can fetch the local files. From the project directory, run:

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000/genome_browser_local.html>. The page loads IGV.js from jsDelivr, so an internet connection is also required.

The reference index uses chromosome names `Chr01` through `Chr07`. The browser opens at `Chr01:218000-223000` to show a gene model clearly; search with any chromosome and coordinate range to explore other regions.
