### xlwt简介
- 用来在任何系统上创建并且写Excel文件，兼容Excel 97/2000/XP/2003 XLS
- 支持Python 2.6, 2.7, 3.3+
- 安装命令 pip install xlwt
- [github xlwt](https://github.com/python-excel/xlwt)
### 一个示例学会使用
```
import xlwt

if __name__ == "__main__":
    # 创建工作簿
    wb = xlwt.Workbook()

    # 创建第一个sheet-'users'
    sheet1 = wb.add_sheet('users', cell_overwrite_ok=True)

    # 创建一个3列的表头作为第1行
    row0 = ['id', 'name', 'age']
    for col_num in range(len(row0)):
        sheet1.write(0, col_num, row0[col_num])

    # 行数据
    rows = [
        [1, 'Python', 30],
        [2, 'Perl', 33],
        [3, 'Ruby', 20]
    ]

    # 逐行写入
    row_num = 1
    for row in rows:
        for col_num in range(len(row)):
            sheet1.write(row_num, col_num, row[col_num])
        row_num += 1
    #
    wb.save('new.xls')
```

