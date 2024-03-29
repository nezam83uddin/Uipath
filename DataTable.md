|Variable Type|Syntax|
|:----|:----|
|Condtion|IsNothing(out_TransactionData) or out_TransactionData.RowCount = 0|
|Condtion|io_TransactionData.RowCount >= in_TransactionNumber|
|o_str_TransactionItem|io_TransactionData.Rows(in_TransactionNumber-1).Item("Trans1").ToString|
|o_str_TransactionItemRequire|Convert.ToBoolean(io_TransactionData.Rows(in_TransactionNumber-1).Item("IsRequired"))|
