### Qt取消信号槽

在切换tableWidget时，如果connect在局部的需要手动的去disconnect，否则将导致事件触发多次，如clicked第一次切换，触发两次，第二次切换触发三次

```qt
    /***************************************************************************************************************/
    /* When switching wigets, you need to disconnect signal, otherwise repeatedly seed signal */
//    disconnect(ui->tableView->horizontalHeader(), &QHeaderView::sectionClicked, this, &Widget::slot_table_header_clicked);
    /***************************************************************************************************************/

    /* table header clicked */
    connect(ui->tableView->horizontalHeader(), &QHeaderView::sectionClicked, this, 			&Widget::slot_table_header_clicked);
//    connect(ui->tableView->horizontalHeader(), &QHeaderView::sectionClicked, this, [=](int col){
//        QMessageBox::information(this, "Notice", "clicked columon " + QString::number(col));
//    });
```

