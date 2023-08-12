# `CWndBase`: Empty methods

The list the methods of `CWndBase` and `CWndNeuz` that are actually used and has an empty definition:

- `OnLButtonUp`, `OnLButtonDown`, `OnRButtonUp`, `OnRButtonDown`, `OnMButtonUp`, `OnMButtonDown`, `OnLButtonDblClk`, `OnRButtonDblClk`, `OnMButtonDblClk`
- `OnNonClientLButtonDblClk`
- `OnMouseMove`
- `OnChar`, `OnKeyUp`, `OnKeyDown`
- `OnDestroyChildWnd`
- `OnSetFocus`
- `OnMouseWndSurface`
- `OnMouseWheel` (return value is never used)
- `AfterSkinTexture`


## Why does it matter?

It is very unlikely that you will modify the definitions of these methods for
`CWndBase` as they implement the "nothing happens by default" behavior.

If a class that inherits from `CWndBase` or `CWndNeuz`, overrides any of these
functions with an empty body, you can remove the override method.


## Example

- Base code (V15 style)

```cpp
class CWndMyConvolutedWindow : public CWndNeuz {
public:
  // things
  virtual void OnLButtonUp( UINT nFlags, CPoint point );
};

void CWndMyConvolutedWindow::OnLButtonUp( UINT nFlags, CPoint point ) {

}
```

- Better (Use C++11 `override` specifier)

```cpp
class CWndMyConvolutedWindow : public CWndNeuz {
public:
  // things
  void OnLButtonUp( UINT nFlags, CPoint point ) override;
};

void CWndMyConvolutedWindow::OnLButtonUp( UINT nFlags, CPoint point ) {

}
```

*By adding the override specifier, a compile error is produced if 
`void OnLButtonUp( UINT nFlags, CPoint point )` does not exist in one of the inherited
class.*

- Even better (`OnLButtonUp` is in the list because `CWndBase::OnLButtonUp` is empty)

```cpp
class CWndMyConvolutedWindow : public CWndNeuz {
public:
  // things
};
```

