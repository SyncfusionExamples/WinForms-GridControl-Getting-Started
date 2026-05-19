# WinForms GridControl Getting Started
This section will explain about creating simple Windows Forms GridControl and the overview of its basic functionalities.

## Adding GridControl through Code

Windows Forms GridControl can be added through code-behind by following the below steps.

1. Create a new Windows Form Application.
2. Add the below assemblies into the project file
   - Syncfusion.Grid.Windows.dll
   - Syncfusion.Grid.Base.dll
   - Syncfusion.Shared.Base.dll
   - Syncfusion.Shared.Windows.dll

Initialize a GridControl by using the below code in code behind.

```csharp
//Initializing a new Grid.
private Syncfusion.Windows.Forms.Grid.GridControl gridControl1 = new Syncfusion.Windows.Forms.Grid.GridControl();
```

Use the below code for adding the initialized GridControl to the application.

```csharp
//Add required size for the Grid.
this.gridControl1.Size = new System.Drawing.Size(344, 250);
this.Controls.Add(this.gridControl1);
```

## Populating Data

Windows Forms GridControl is a cell based control and hence to populate the GridControl, RowCount and ColCount are necessary. By default the RowCount and ColCount values are 10. Data can be populated by any one of the following methods.

Populate data by looping through cells in GridControl.

```csharp
//Specifying row and column count
gridControl1.RowCount = 15;
gridControl1.ColCount = 4;

//Looping through the cells and assigning the values based on row and column index
for (int row = 1; row <= gridControl1.RowCount; row++)
{
    for (int col = 1; col <= gridControl1.ColCount; col++)
    {
        gridControl1.Model[row, col].CellValue = string.Format("{0}/{1}", row, col);
    }
}
```

## Cell Styles

In Windows Forms GridControl, each cell contains distinct style information and can be customized independently using GridStyleInfo objects.

### Modifying Cell Styles through Designer

To edit cell styles in Designer mode, select the grid and click Edit to access the designer surface. Use the PropertyGrid to modify appearance and style settings for the whole grid or selected range of cells.

### Modifying Cell Styles through Code

Use GridStyleInfo class to customize cell appearance and apply the style to desired range of cells.

```csharp
//Creates GridStyleInfo object.
GridStyleInfo style = new GridStyleInfo();

//Set properties to it.
style.BackColor = Color.DarkGreen;
style.TextColor = Color.White;
style.Font.Facename = "Verdana";
style.Font.Bold = true;
style.Font.Size = 9f;

//Apply the style to desired range of cells.
this.gridControl1.ChangeCells(GridRangeInfo.Cells(2, 2, 4, 2), style);
```

## Selection

Windows Forms GridControl provides two types of selection: Range selection (cell-based) and Record selection (record-based).

For record selection, set the ListBoxSelectionMode property:

```csharp
this.gridControl1.ListBoxSelectionMode = SelectionMode.None;
```

For range selection, set the AllowSelection property:

```csharp
this.gridControl1.AllowSelection = Syncfusion.Windows.Forms.Grid.GridSelectionFlags.Any;
```

Selection operations can be handled using SelectionChanging and SelectionChanged events.

## Editing

By default the GridControl is in editable state. Use the ReadOnly property to enable or disable editing for the whole grid or individual cells.

```csharp
// Disabling Edit mode for the whole Grid.
this.gridControl1.ReadOnly = false;

// Disabling edit mode for a particular cell.
GridStyleInfo style = gridControl1.Model[2, 2];
style.ReadOnly = false;
```

Editing operations can be customized using CurrentCellStartEditing and CurrentCellEditingComplete events.

## For More Information

Refer to the Syncfusion WinForms GridControl documentation: [Getting Started Guide](https://help.syncfusion.com/windowsforms/grid-control/getting-started)