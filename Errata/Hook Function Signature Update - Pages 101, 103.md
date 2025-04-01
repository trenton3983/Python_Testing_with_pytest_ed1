# Errata: *Python Testing with pytest* – Hook Function Signature Update (Pages 101/103)

## Issue Summary

On **pages 101 and 103**, the book shows examples of `pytest` hook functions (`pytest_report_header` and `pytest_report_teststatus`) that reference `pytest.config` directly. This is outdated in recent versions of `pytest`.

## Cause

Since **pytest 5.0**, the `config` object must be passed explicitly to hook functions. Accessing it via `pytest.config` results in an `AttributeError`.

## Original (Outdated) Code

```python
# This will raise AttributeError in pytest ≥5.0
if pytest.config.getoption('nice'):
```

## Corrected Code for Modern pytest Versions

```python
def pytest_report_header(config):
    """Thank tester for running tests."""
    if config.getoption('nice'):
        return "Thanks for running the tests."


def pytest_report_teststatus(report, config):
    """Turn failures into opportunities."""
    if report.when == 'call':
        if report.failed and config.getoption('nice'):
            return (report.outcome, 'O', 'OPPORTUNITY for improvement')
```

## Affected Pages

- Page **101**
- Page **103**

## Additional Notes

- This change ensures compatibility with **pytest 5.0 and later**.
- For full documentation, see [Writing plugins](https://docs.pytest.org/en/stable/writing_plugins.html#hook-function-validation) in the pytest docs.