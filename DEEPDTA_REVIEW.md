# DeepDTA KIBA ensemble review bundle

This branch contains a compressed unified source patch for the KIBA ensemble integration and regression updates. The complete runnable review package is supplied separately as **DeepDTA_Review_Package.zip** in the accompanying ChatGPT conversation.

## Applying the source patch

The file `review_changes.patch.gz` is a gzip-compressed unified diff against the supplied project archive. Extract the review ZIP, decompress the patch, and apply it from the project root:

```bash
gzip -dc review_changes.patch.gz > review_changes.patch
git apply review_changes.patch
```

The review ZIP includes the full codebase, both selected ensemble checkpoints, their hash manifest, updated frontend source and built assets, documentation, tests, and a regenerated package integrity manifest.

## Scientific status

- Selected KIBA candidate: equal-weight average of baseline seed 42 and seed 123.
- Validation only: 19,709 pairs; MSE 0.166168, RMSE 0.407637, MAE 0.234778, CI 0.876827.
- The candidate's supplied test fold has not been evaluated.
- The previous single-model uncertainty calibration is disabled for this ensemble.
- Cold-drug/cold-protein benchmark results belong to separate benchmark models, not this candidate.
- The original single-model checkpoint is retained as a reference.

## Review gates

1. Apply the patch to the review ZIP and inspect the source diff.
2. Run the backend regression suite in the documented Python 3.11 environment.
3. Build the frontend from source.
4. Evaluate the frozen ensemble on the supplied test fold once, then perform cold-entity evaluation.
5. Rebuild ensemble-specific calibration before restoring any per-prediction accuracy estimate.

This branch is for team review only. It is not a production approval and does not modify the official DeepDTA repository.
