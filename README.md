# How to listen checked state change of the check boxes in WPF DataGrid(SfDataGrid) GridCheckBoxColumn?

## About the sample

This sample illustrates how to listen checked state change of the check boxes in WPF DataGrid(SfDataGrid) GridCheckBoxColumn.

In [WPF DataGrid](https://www.syncfusion.com/wpf-controls/datagrid)(SfDataGrid), there is no direct event to listen the checked state change of the checkboxes in the [GridCheckBoxColumn](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.GridCheckBoxColumn.html). You can listen the check state change of the check box by using [SfDataGrid.CurrentCellValueChanged](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.SfDataGrid.html#Syncfusion_UI_Xaml_Grid_SfDataGrid_CurrentCellValueChanged) event.

```c#

private void DataGrid_CurrentCellValueChanged(object sender, Syncfusion.UI.Xaml.Grid.CurrentCellValueChangedEventArgs e)
{
    SfDataGrid grid = sender as SfDataGrid;
    int columnindex = grid.ResolveToGridVisibleColumnIndex(e.RowColumnIndex.ColumnIndex);
    var column = grid.Columns[columnindex];
    if (column.GetType() == typeof(GridCheckBoxColumn) && column.MappingName == "IsDelivered")
    {
        var rowIndex = grid.ResolveToRecordIndex(e.RowColumnIndex.RowIndex);
        var record = grid.View.Records[rowIndex].Data as OrderInfo;

        var value = record.IsDelivered;
    }
}

```

## Requirements to run the demo
Visual Studio 2015 and above versions
