# Removing Duplicate Records in UiPath

To remove duplicate rows from a `DataTable` by considering the entire table, UiPath provides a dedicated activity:

---

## **Remove Duplicate Records**

You can use the **`Remove Duplicate Records`** activity to achieve this.

### Steps:
1. Drag and drop the **`Remove Duplicate Records`** activity into your workflow.
2. Set the **`Input DataTable`** property to the variable containing your `DataTable` (e.g., `dt`).
3. Set the **`Output DataTable`** property to a new or existing `DataTable` variable (e.g., `dt_unique`).

---

### Example Workflow:
- **Input DataTable:** `dt`  
- **Output DataTable:** `dt_unique`  

After execution, `dt_unique` will contain the original `DataTable` without duplicate rows.

---

### Notes:
- This activity works by comparing all columns in the `DataTable` to identify duplicate rows.
- If you want to remove duplicates based on specific columns, you’ll need to use a LINQ query or a custom workflow.


# Removing Duplicate Records in One Column in UiPath

To remove duplicate rows based on a specific column, you can use an **Assign** activity with LINQ. This approach groups rows by the specified column and retains only the first row from each group.

---

## **Assign Activity Code**

```
dt = dt.AsEnumerable().
        GroupBy(Function(i) i.Field(Of String)("ColumnWithDuplicateValues")).
        Select(Function(g) g.First).
        CopyToDataTable
```
### Example Workflow:
- **Input DataTable**: `dt`
- **Column to Check for Duplicates**: `"ColumnWithDuplicateValues"`
- **Result**: The DataTable `dt` is updated to include only `unique rows` based on the specified column.


# Selecting Specific Columns from a DataTable in UiPath

You can extract specific columns from a `DataTable` using the `DefaultView.ToTable` method in an **Assign** activity. Here's how:

---

## **1. Get a Single Column**

To create a new `DataTable` with only one column:

```
dt = dt.DefaultView.ToTable(False, "Columnname-1")
```

### Explanation:
`False`: Indicates that duplicate rows are not removed.

`"Columnname-1"`: The name of the column to include in the new DataTable.



## **2. Get Multiple Specific Columns**

To create a new `DataTable` with `multiple` specific columns:
```
dt = dt.DefaultView.ToTable(False, "Columnname-1", "Columnname-2", "Columnname-3")
```

### Explanation
`False`: Duplicate rows are not removed.

`"Columnname-1"`, `"Columnname-2"`, ...: List of column names to include.

## **3. Get Specific Columns with Distinct Records**
To retrieve specific columns while removing duplicate rows:

```
dt = dt.DefaultView.ToTable(True, "Columnname-1")
```

### Explanation:
`True`: Removes duplicate rows in the resulting DataTable.

`"Columnname-1"`: The column to include with distinct rows.

### Example Workflow:

Use an Assign activity:

- **For one column**:
```
dt_filtered = dt.DefaultView.ToTable(False, "Columnname-1")
```
- **For multiple columns**:
```
dt_filtered = dt.DefaultView.ToTable(False, "Columnname-1", "Columnname-2")
```
- **For distinct rows**:
```
dt_filtered = dt.DefaultView.ToTable(True, "Columnname-1")
```

The resulting DataTable (`dt_filtered`) will contain only the selected columns or distinct rows.

