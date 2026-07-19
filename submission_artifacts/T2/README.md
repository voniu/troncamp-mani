# T2 submission artifact

GitHub does not allow a public fork to upload new Git LFS objects. The source
code and normalization statistics are stored in Git; the selected checkpoint
is distributed separately as the GitHub Release asset:

```text
t2-grab_roller-policy_best.tar.gz
```

Extract the release asset from the repository root:

```bash
tar -xzf /path/to/t2-grab_roller-policy_best.tar.gz
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
