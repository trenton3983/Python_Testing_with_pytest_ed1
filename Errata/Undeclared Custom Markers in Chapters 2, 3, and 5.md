# Errata: *Python Testing with pytest* – Undeclared Custom Markers in Chapters 2, 3, and 5

## Issue Summary

In **Chapters 2, 3, and 5**, multiple `tasks_proj/tests` directories contain tests that use custom markers like `@pytest.mark.smoke` and `@pytest.mark.get`. These markers are not declared in a `pytest.ini` file, which causes warnings in newer versions of pytest:

```
PytestUnknownMarkWarning: Unknown pytest.mark.smoke - is this a typo?
```

## Cause

At the time of publication (2017), pytest did not require declaring custom markers. Since **pytest 4.5**, all custom marks must be registered explicitly in the `pytest.ini` file to avoid warnings.

## Affected Chapters

- **Chapter 2**
- **Chapter 3**
- **Chapter 5**

## Recommended Fix

To suppress these warnings, add the following `pytest.ini` file to each relevant `tests` directory:

```ini
[pytest]
markers =
    smoke
    get
```

This should be placed in the directory containing the tests that use these markers.

## Additional Notes

- This is a compatibility issue introduced by changes in pytest's marker validation system.
- Declaring markers helps prevent typos and improves clarity in test annotations.
- See the [pytest documentation on custom markers](https://docs.pytest.org/en/latest/mark.html) for details.
