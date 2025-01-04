---
tags:
  - excerpt
  - documentation
  - code_package
  - pytorch/lightning
aliases: 
keywords: 
topics:
  - code/doc
language: python
date of note: 2024-03-25
name: Pytorch Lightning User Guide and Doc
version: 2.2.1
year: 2024
---
# Hooks

>[!quote]
>This is the pseudocode to describe the structure of [`fit()`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.trainer.trainer.Trainer.html#lightning.pytorch.trainer.trainer.Trainer.fit "lightning.pytorch.trainer.trainer.Trainer.fit"). The inputs and outputs of each function are not represented for simplicity. Please check each function’s API reference for more information.

```python
# runs on every device: devices can be GPUs, TPUs, ...
def fit(self):
    configure_callbacks()

    if local_rank == 0:
        prepare_data()

    setup("fit")
    configure_model()
    configure_optimizers()

    on_fit_start()

    # the sanity check runs here

    on_train_start()
    for epoch in epochs:
        fit_loop()
    on_train_end()

    on_fit_end()
    teardown("fit")


def fit_loop():
    torch.set_grad_enabled(True)

    on_train_epoch_start()

    for batch in train_dataloader():
        on_train_batch_start()

        on_before_batch_transfer()
        transfer_batch_to_device()
        on_after_batch_transfer()

        out = training_step()

        on_before_zero_grad()
        optimizer_zero_grad()

        on_before_backward()
        backward()
        on_after_backward()

        on_before_optimizer_step()
        configure_gradient_clipping()
        optimizer_step()

        on_train_batch_end(out, batch, batch_idx)

        if should_check_val:
            val_loop()

    on_train_epoch_end()


def val_loop():
    on_validation_model_eval()  # calls `model.eval()`
    torch.set_grad_enabled(False)

    on_validation_start()
    on_validation_epoch_start()

    for batch_idx, batch in enumerate(val_dataloader()):
        on_validation_batch_start(batch, batch_idx)

        batch = on_before_batch_transfer(batch)
        batch = transfer_batch_to_device(batch)
        batch = on_after_batch_transfer(batch)

        out = validation_step(batch, batch_idx)

        on_validation_batch_end(out, batch, batch_idx)

    on_validation_epoch_end()
    on_validation_end()

    # set up for train
    on_validation_model_train()  # calls `model.train()`
    torch.set_grad_enabled(True)
```



----------
##  Citations

- Pytorch Lightning Homepage Doc [link](https://lightning.ai/docs/pytorch/stable/)
- `LightningModule` **Hooks** [section](https://lightning.ai/docs/pytorch/stable/common/lightning_module.html#hooks)
- *code source*:
- *code package link*




