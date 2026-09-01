# Prime-RL compatibility wheels

This repository publishes narrowly scoped compatibility wheels used by
Prime-RL experiments. Wheels are release assets rather than files committed
to Git history.

## TorchAO 0.17.0 for Cutlass DSL 4.6.2

The wheel is based on pytorch/ao tag `v0.17.0`, commit
`02105d46c61dc80a8c9d39d5836e827ba3af8439`. It replaces TorchAO's import of
the removed private Cutlass helper `cutlass.base_dsl._mlir_helpers.arith` with
the Cutlass DSL 4.6.2 `Numeric.bitcast` API. See
`patches/torchao-0.17.0-cutlass-4.6.2.patch`.

Validated on NVIDIA B200 with:

- CPython 3.12
- PyTorch `2.13.0+cu129`
- Cutlass DSL `4.6.2`
- Prime-RL Qwen3.5 trainer import

Artifact:

```text
torchao-0.17.0+git02105d46c.cutlass462-cp312-cp312-linux_x86_64.whl
sha256:0bea5dc2b337a07d0fb3cebc83c8aaf4d4baac1a08bbaa017d80119d8426f8e0
```

The wheel contains software from
[`pytorch/ao`](https://github.com/pytorch/ao) and retains its upstream license
metadata.

## FlashAttention-4 b28 compatibility build

The FA4 wheel is based on Dao-AILab/flash-attention commit `0251105`. It
accepts scalar `max_seqlen` tensors at the public interface boundary and keeps
the TVM FFI `>=0.1.11` dependency used by the validated vLLM 0.27.1 stack. See
`patches/flash-attn-4-b28-max-seqlen.patch`.

Artifact:

```text
flash_attn_4-4.0.0b28.dev0+g0251105.d20260826-py3-none-any.whl
sha256:9aae0f6fa850f2b64c5f7a3c4658ef5db8a81a34bcf7edd61f3084017ce47b95
```
