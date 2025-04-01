# Errata: *Python Testing with pytest* – Chapter 2 Custom Mark Warnings

## Issue Summary

While running the smoke tests in **Chapter 2** of *Python Testing with pytest*, pytest emits warnings about **unregistered custom marks** such as `@pytest.mark.smoke` and `@pytest.mark.get`.

### Example Warning Output

```
PytestUnknownMarkWarning: Unknown pytest.mark.smoke - is this a typo?
You can register custom marks to avoid this warning - for details, see https://docs.pytest.org/en/latest/mark.html
```

This warning appears for lines such as:

```python
@pytest.mark.smoke
@pytest.mark.get
```

## Cause

As of **pytest 4.5**, custom markers must be explicitly registered in your `pytest.ini` configuration file. This is to prevent typos and improve test clarity.

## Affected Files

- `tests/func/test_add.py`
- `tests/func/test_api_exceptions.py`

## Recommended Fix

To silence these warnings and properly register your custom markers, add the following to your `pytest.ini`:

```ini
[pytest]
markers =
    smoke
    get
```

## Additional Notes

- This requirement was introduced in newer versions of pytest and is not covered in the original 2017 edition of the book.
- For more information, see the [pytest marks documentation](https://docs.pytest.org/en/latest/mark.html) and [warnings reference](https://docs.pytest.org/en/latest/warnings.html).
