# Short notes

A place where very small notes are placed.


## D3DX `XXDeviceObject` functions convention

- `InitDeviceObjects`: when the component is created
- `InvalidateDeviceObjects`: when the window rendering is lost (for example the user pressed ctrl + alt + suppr)
- `RestoreDeviceObjects`: when the window rendering is back
- `DeleteDeviceObjects`: The window is destroyed / the component is destroyed

## Name validation

- It is not an error to not find a file for `FILE_ALLOWED_LETTER` / `FILE_ALLOWED_LETTER2`: in this case, all letters are valid
- *Letter2* is for shops:
    - `FILE_ALLOWED_LETTER2` is bound to `Letter1_XXX.inc` files
    - `Letter2_XXX.inc` files are never used. It may be a bug and could possibly intended to be used with `FILE_ALLOWED_LETTER2`.

