# -Q1
紀錄記不住的東西

Python：錯誤FileNotFoundError: [Errno 2] No such file or directory: 'objects/epsilon.pkl

解釋:
沒有該文件夾或者該文件，也就是你訪問了不存在的文件，但其實你訪問的文件如果不存在，切訪問用的是w方法的法，是會新建文檔的，所以問題主要是，沒有這個文件夾，新建即可。

詳細解釋:
python，os庫對於文件的讀寫，是有要求的。由於你的文件的打開方式是'w'，也就是文件不存在時就創建文件，所以那個pkl文件（我指的是相對路徑中的pkl）不存在會自動創建，這不是問題，問題就在於那個相對路徑，就是那個path是否存在，這個文件夾不存在一樣會出問題。所以先要判斷這個path是否存在。不存在則創建。


import os
if not os.path.exists(path):
    os.mkdir(path)
    
而且需要注意，對於路徑一次只能創建一層，就是說你objects的上一層的存在，不然還是會出錯。

資料來源:https://blog.csdn.net/lvsehaiyang1993/article/details/80615549

# -Q2
