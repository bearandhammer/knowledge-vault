https://codereview.stackexchange.com/questions/70996/speeding-up-parallel-foreach-iterating-through-datatable-and-rendering-report

https://stackoverflow.com/questions/19225841/enumerating-datatable-rows-in-batches-efficiently

Tasks - batching???

OperationBatcher (current implementation).

Won't matter as the DataTable (and DataRowCollection) is not threadsafe and cannot be concurrently modified.