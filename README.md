# Terpedia Fusarium linalool transcriptomics audit

This forkable research project audits the published supplementary DEG, protein, and KEGG tables for [Li et al.'s linalool exposure study](https://pmc.ncbi.nlm.nih.gov/articles/PMC9820380/). The [executed Jupyter notebook](notebooks/terputer-fusarium-linalool-supplement.ipynb), [generated white paper](research/fusarium-linalool-supplement/generated/white-paper.md), [claim ledger](research/fusarium-linalool-supplement/generated/claim-ledger.tsv), and [receipts](research/fusarium-linalool-supplement/generated/generation-receipt.json) are committed. See the [project methods and findings](research/fusarium-linalool-supplement/README.md).

The [publisher supplementary archive](https://mdpi-res.com/d_attachment/ijms/ijms-24-00458/article_deploy/ijms-24-00458-s001.zip) is restored from a checksum-pinned URL and kept out of Git. The notebook audits processed author tables; it does not reprocess raw reads or establish an independent replication or direct linalool target.

## Reproduce

```sh
python -m pip install -r requirements.txt
python restore-inputs.py research/fusarium-linalool-supplement/report-spec.json
python notebook-runner.py notebooks/terputer-fusarium-linalool-supplement.ipynb . 300 '["research/fusarium-linalool-supplement/results/pathway_crossomics.tsv","research/fusarium-linalool-supplement/results/gene_protein_overlap.tsv","research/fusarium-linalool-supplement/results/analysis_summary.json"]' '["research/fusarium-linalool-supplement/data/ijms-24-00458-s001.zip"]'
node report-generator.mjs research/fusarium-linalool-supplement/report-spec.json
```

To attach a fork to your `terpedia-report` workspace, fork this repository into your GitHub account under the same repository name and use `add_research_project_submodule` with slug `fusarium-linalool-supplement`. The submodule path is `projects/fusarium-linalool-supplement`.
