# T3 epoch-4000 submission artifact

This archive contains the 400-demo T3 ACT checkpoint evaluated at 3/5 on the
local warmed RGB seed matrix. GitHub-compatible parts are each below 100 MB.

From the repository root after pulling:

```bash
(
  cd submission_artifacts/T3
  sha256sum -c SHA256SUMS.parts
  cat t3-stack-bowls-two-epoch4000.tar.gz.part-* > t3-stack-bowls-two-epoch4000.tar.gz
  echo "c3060bd1e0f58246abf4befae612ea53897c9623165e2c93ecf15a720de6ae2e  t3-stack-bowls-two-epoch4000.tar.gz" | sha256sum -c -
)
tar -xzf submission_artifacts/T3/t3-stack-bowls-two-epoch4000.tar.gz
```

Expected extracted-file SHA-256:

```text
policy_best.ckpt  43b1c28bce2961688cd1ecfa461cd0a9e0d351bc1d41ea54561d9a16e9ab5f3e
dataset_stats.pkl 165ae102218955c1098e91f0cf3f4a4ac8bda35817a3cedb0b13fcce39702948
```

Submit from the repository root:

```bash
python submit/submit.py \
  --server https://submit.troncamp-mani.limxdynamics.com \
  --token=<your-token> \
  --track T3 \
  --code-dir external/robotwin_local \
  --ckpt external/robotwin_local/policy/ACT/act_ckpt/act-stack_bowls_two/stack_bowls_two_combined_400ep-400-epoch4000/policy_best.ckpt
```
