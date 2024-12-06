# Working with DataTables in .NET (C#/VB)

Below are common operations to interact with a `DataTable` (`dt`) in .NET, along with examples:

---

## 1. **Get the Number of Rows in a DataTable**

You can get the total number of rows in a `DataTable` using:

```
int rowCount = dt.Rows.Count;
```

### Output

- **Type**: int32
- **Example**: If `dt` has 5 rows, `rowCount` will be `5`.


## 2. Get the Number of Columns in a DataTable

To retrieve the total number of columns:

```
int columnCount = dt.Columns.Count
```

### Output
- **Type**: Int32
- **Example Usage in UiPath*:

```
columnCount = dt.Columns.Count
```
`columnCount` will hold the total number of columns.

