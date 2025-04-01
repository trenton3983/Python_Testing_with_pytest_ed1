# Errata: *Python Testing with pytest* – Typo in `pytest.ini` Option (`testspaths` → `testpaths`)

## Issue Summary

In **Chapter 6**, under "Specifying Test Directory Locations", the configuration option `testspaths` is used twice. This is a typo. The correct option is **`testpaths`**.

## Affected Locations

- **Chapter 6**
- Kindle format: **Location 6256** and **6289**

## Correction

Replace:

```ini
[pytest]
testspaths = tests
```

With:

```ini
[pytest]
testpaths = tests
```

## Additional Notes

- `testpaths` is the correct key recognized by pytest for specifying directories to search for tests.
- Using the incorrect `testspaths` option will cause pytest to ignore the directive.

## Reference

See the [`pytest.ini` configuration docs](https://docs.pytest.org/en/stable/customize.html#confval-testpaths) for the official usage of `testpaths`.
