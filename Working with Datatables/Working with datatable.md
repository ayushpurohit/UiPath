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
- **Example Usage in UiPath**:

```
columnCount = dt.Columns.Count
```
`columnCount` will hold the total number of columns.

## 3. Get the Index of a Specific Row (Inside a For Each Row Loop)
To get the index of the current row inside a For Each Row loop:
```
dt.Rows.IndexOf(CurrentRow)
```

### Output
- **Type**: `Int32`
- **Example Usage in UiPath**:

- Inside a `For Each Row` activity:
  - Assign activity:
```
rowIndex = dt.Rows.IndexOf(CurrentRow)
```

`rowIndex` will contain the zero-based index of the current row.

## 4. Get the Index of a Specific Column (By Column Name)

To get the index of a column when the column name is known:
```
dt.Columns.IndexOf("ColumnName")
```

To get the index of a column by its position:
```
dt.Columns.IndexOf(ColumnIndex)
```

- **Type**: - `Int32`
- **Example Usage in UiPath**:
  - Assign activity:
```
columnIndex = dt.Columns.IndexOf("ColumnName")
```

`columnIndex` will hold the zero-based index of the column with the name `"ColumnName"`.


## 5. Get Column Name from Index

To get the column name by its index:

```
Str_ColumnName = dt.Columns(Int_ColumnIndex).ColumnName.ToString
```

### Example Usage:
- Assign activity:
```
Str_ColumnName = dt.Columns(2).ColumnName.ToString
```
If column index `2` corresponds to a column named `"Age"`, `Str_ColumnName` will hold `"Age"`.

### Notes:
- `Count` starts from `1`, representing the total count of rows/columns.
- `Index` starts from `0`, representing the zero-based position of rows/columns.
- Ensure the `DataTable` is initialized before performing these operations to avoid errors.
