# Errata: *Python Testing with pytest* – Chapter 5 Example C

## Issue Summary

When running the example `test_api_exceptions.py` in **Chapter 5, Example C** of *Python Testing with pytest* under **pytest 5.4.1**, the following error occurs:

```
AttributeError: module 'pytest' has no attribute 'config'
```

### Affected Versions

- **Book**: *Python Testing with pytest* by Brian Okken (2017)
- **Pytest**: 5.0 and later (confirmed with 5.4.1)
- **Python**: 3.8.3

## Problem Description

The error originates from this line in `conftest.py`:

```python
if report.failed and pytest.config.getoption("nice"):
```

The `pytest.config` global was **deprecated in pytest 4.0** and **removed in pytest 5.0**, which causes an `AttributeError` when used in newer versions.

## How to Reproduce

```bash
cd /path/to/code/ch5/c/tasks_proj/tests/func
pytest --tb=no test_api_exceptions.py -k TestAdd
```

You will likely see output similar to:

```
INTERNALERROR> AttributeError: module 'pytest' has no attribute 'config'
```

## Recommended Fix

Update the affected `conftest.py` hook implementations to use the `config` argument provided by pytest:

```python
def pytest_report_header(config):
    """Thank tester for running tests."""
    if config.getoption("nice"):
        return "Thanks for running the tests."

def pytest_report_teststatus(config, report):
    """Turn failures into opportunities."""
    if report.when == "call":
        if report.failed and config.getoption("nice"):
            return (report.outcome, "O", "OPPORTUNITY for improvement")
```

This approach is compatible with **pytest 5.0+**.

## Additional Notes

- The original code in the book works as expected only with **pytest < 5.0**.
- If following the book exactly, consider using a virtual environment with an older pytest version.
- Refer to the [pytest changelog](https://docs.pytest.org/en/stable/changelog.html) for details on breaking changes.
