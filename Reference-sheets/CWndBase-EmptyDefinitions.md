# `CWndBase`: Empty methods

The list the methods of `CWndBase` and `CWndNeuz` that are actually used and have an empty definition:

- `OnDraw`
- `OnLButtonUp`
- `OnLButtonDown`
- `OnRButtonUp`
- `OnRButtonDown`
- `OnMButtonUp`
- `OnMButtonDown`
- `OnLButtonDblClk`
- `OnRButtonDblClk`
- `OnMButtonDblClk`
- `OnMouseMove`
- `OnChar`
- `OnKeyUp`
- `OnKeyDown`
- `OnDestroyChildWnd`
- `OnSetFocus`
- `OnMouseWndSurface`
- `OnMouseWheel` (return value is never used)
- `AfterSkinTexture`
- `OnCommand` only returns `TRUE`

*Maybe*:
- `OnChildNotify` only if you inherit from `CWndBase` and not from `CwndNeuz`
- `OnNonClientLButtonDblClk` only if you inherit from `CWndBase` and not from `CwndNeuz`


## Why does it matter?

It is very unlikely that you will modify the definitions of these methods for
`CWndBase` as they implement the "nothing happens by default" behavior.

If a class that inherits from `CWndBase` or `CWndNeuz`, overrides any of these
functions with an empty body, you can remove the override method.


## Example

- Base code: V15 style

```cpp
class CWndConvoluted : public CWndNeuz {
public:
  // things
  virtual void OnLButtonUp( UINT nFlags, CPoint point );
  virtual BOOL OnCommand( UINT nID, DWORD dwMessage, CWndBase* pWndBase );
};

void CWndConvoluted::OnLButtonUp( UINT nFlags, CPoint point ) {

}

BOOL CWndConvoluted::OnCommand( UINT nID, DWORD dwMessage, CWndBase* pWndBase ) 
{ 
	return CWndNeuz::OnCommand( nID, dwMessage, pWndBase ); 
}

```

- Better: Use C++11 `override` specifier

```cpp
class CWndConvoluted : public CWndNeuz {
public:
  // things
  void OnLButtonUp( UINT nFlags, CPoint point ) override;
  BOOL OnCommand( UINT nID, DWORD dwMessage, CWndBase* pWndBase ) override;
};

void CWndConvoluted::OnLButtonUp( UINT nFlags, CPoint point ) {

}

BOOL CWndConvoluted::OnCommand( UINT nID, DWORD dwMessage, CWndBase* pWndBase ) 
{ 
	return CWndNeuz::OnCommand( nID, dwMessage, pWndBase ); 
}
```

*By adding the override specifier, a compile error is produced if 
`void OnLButtonUp( UINT nFlags, CPoint point )` does not exist in one of the inherited
class.*

- Even better: `OnLButtonUp` is in the list because `CWndBase::OnLButtonUp` is empty, so
it can be removed

```cpp
class CWndConvoluted : public CWndNeuz {
public:
  // things
  BOOL OnCommand( UINT nID, DWORD dwMessage, CWndBase* pWndBase ) override;
};

BOOL CWndConvoluted::OnCommand( UINT nID, DWORD dwMessage, CWndBase* pWndBase ) 
{ 
	return CWndNeuz::OnCommand( nID, dwMessage, pWndBase ); 
}
```

- Final version: All `CWndMyConvolutedWindow::OnCommand` does is calling the
method that is inherited, so it is useless to redefine it.

```cpp
class CWndConvoluted : public CWndNeuz {
public:
  // things
};
```
