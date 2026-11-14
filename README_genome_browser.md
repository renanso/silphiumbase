# Silphium genome browser

The browser loads the reference assembly and gene annotation from the public Google Cloud Storage bucket `gs://silphiumbase`. Keep these five objects at the bucket root:

- `genome.fasta.gz`, `genome.fasta.gz.fai`, and `genome.fasta.gz.gzi`
- `sorted.gff3.gz` and `sorted.gff3.gz.csi`

The objects must allow anonymous reads and byte-range requests. The browser also needs CORS access from the website origin. Apply the CORS policy in [`gcs-cors.json`](./gcs-cors.json) with:

```sh
gcloud auth login
gcloud storage buckets update gs://silphiumbase --cors-file=gcs-cors.json
```

Use an account with permission to update the bucket. This replaces its existing CORS policy; merge these origins and response headers into any policy you need to keep. Add your own site origin to the JSON if the site uses a custom domain. Public object access is separate from CORS and must be enabled for the browser to fetch the data.

To run the site locally, start a web server from the project directory:

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000/genome_browser_local.html>. The page loads IGV.js from jsDelivr, so an internet connection is also required.

The reference index uses chromosome names `Chr01` through `Chr07`. The browser opens at `Chr01:218000-223000` to show a gene model clearly; search with any chromosome and coordinate range to explore other regions.
