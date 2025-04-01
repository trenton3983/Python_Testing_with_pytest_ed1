# Errata: *Python Testing with pytest* – Incorrect Type Hint in `start_tasks_db` Function

## Issue Summary

In the **downloadable source code**, the file `tasks_proj/src/tasks/tasksdb_tinydb.py` contains an incorrect type hint comment for the `start_tasks_db` function.

## File and Line

- **File**: `tasks_proj/src/tasks/tasksdb_tinydb.py`
- **Line**: 66 (in original downloadable code)

## Incorrect Code

```python
def start_tasks_db(db_path):  # type (str) -> TasksDB_MongoDB object
    """Connect to db."""
    return TasksDB_TinyDB(db_path)
```

## Corrected Code

```python
def start_tasks_db(db_path):  # type (str) -> TasksDB_TinyDB object
    """Connect to db."""
    return TasksDB_TinyDB(db_path)
```

## Additional Notes

- This is a simple documentation error in the type hint comment and does not affect runtime behavior.
- The returned class is correctly implemented as `TasksDB_TinyDB`, not `TasksDB_MongoDB`.