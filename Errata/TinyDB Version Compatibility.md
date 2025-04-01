# Errata: *Python Testing with pytest* – TinyDB Version Compatibility

## Issue Summary

The code examples in *Python Testing with pytest* use **TinyDB**, but the **TinyDB 4.x** API introduces breaking changes that are incompatible with the examples provided in the book.

## Cause

The book was written using **TinyDB 3.15.1**, but the current `tinydb` releases (4.x and later) have introduced significant API changes. These changes may cause errors or unexpected behavior in the sample project.

## Affected Files

- `tasks_proj/setup.py`
- `ch7/tasks_proj_v2/setup.py`

## Recommended Fix

Pin the `tinydb` version to **3.15.1** to maintain compatibility with the book’s code:

### In `tasks_proj/setup.py`:

```python
install_requires = [
    'click==7.1.2',
    'tinydb==3.15.1'
]
```

### In `ch7/tasks_proj_v2/setup.py`:

```python
install_requires = [
    'click==7.1.2',
    'tinydb==3.15.1',
    'pytest',
    'pytest-mock'
]
```

## Additional Notes

- This issue does **not** impact your ability to learn `pytest` itself.
- The book’s focus is on testing methodology, and the database is a supporting component.

## Author Note

> “Pin the TinyDB version to 3.15.1. The API changed in the 4.x series of TinyDB. However, the change doesn’t affect you learning pytest.”  
> — Brian Okken, Author of *Python Testing with pytest*
