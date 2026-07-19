# T2 submission artifact

GitHub does not allow a public fork to upload new Git LFS objects. The selected
checkpoint archive is therefore stored as four regular Git files, each below
GitHub's 100 MB per-file limit:

```text
t2-grab_roller-policy_best.tar.gz.part-00
t2-grab_roller-policy_best.tar.gz.part-01
t2-grab_roller-policy_best.tar.gz.part-02
t2-grab_roller-policy_best.tar.gz.part-03
```

After pulling the repository, verify, join, and extract from the repository root:

```bash
(
  cd submission_artifacts/T2
  sha256sum -c SHA256SUMS.parts
  cat t2-grab_roller-policy_best.tar.gz.part-* > t2-grab_roller-policy_best.tar.gz
  echo "b00492c92c45437b8b8425aa4c540f86ee908609341b5dd559d4dfa85ee6811f  t2-grab_roller-policy_best.tar.gz" | sha256sum -c -
)
tar -xzf submission_artifacts/T2/t2-grab_roller-policy_best.tar.gz
```

Expected SHA-256:

```text
policy_best.ckpt  777615d12b5c71f80dcfd4f3dc45480c47b7ab68ce13755fb152ac53e0e4d3c4
dataset_stats.pkl b57a70c96de0fd7a38dd527becbeb2d966380fcfbef69b905315747b7bb232a0
```

Then verify the extracted files:

```bash
sha256sum \
  external/robotwin_local/policy/ACT/act_ckpt/act-grab_roller/grab_roller_200ep-200/policy_best.ckpt \
  external/robotwin_local/policy/ACT/act_ckpt/act-grab_roller/grab_roller_200ep-200/dataset_stats.pkl
```

Submit from the repository root:

```bash
python submit/submit.py \
  --track T2 \
  --code-dir external/robotwin_local \
  --ckpt external/robotwin_local/policy/ACT/act_ckpt/act-grab_roller/grab_roller_200ep-200/policy_best.ckpt \
  --token-file /path/to/token.txt
```

The token is intentionally not stored in this repository.
