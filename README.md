
下載 script 檔案，放到 ~/bin

打開 terimal 以及輸入以下指令 
`chmod +x ~/bin/filemanage`

`nano ~/.zshrc`

新增 `export PATH="$HOME/bin:$PATH"` 到 .zshrc 中

然後使用以下指令
`source ~/.zshrc`


finemanage 指令用法

```
用法：
  filemanage [動作選項] [其他選項] [-e ext1,ext2,...] SRC [DEST]

動作（四選一，必填）：
  -m    move：搬移（依副檔名 或 -A 整包）
  -c    copy：複製（依副檔名 或 -A 整包）
  -d    delete：刪除（僅依副檔名）
  -p    preview：預覽（依副檔名列檔案 或 -A 預覽整包操作）

其他選項：
  -A    整包資料夾模式（A2）：把 SRC 資料夾整包搬/拷到 DEST
        -m -A：使用 mv
        -c -A：使用 ditto（mac 友善，保留屬性/隱藏檔）
        -p -A：只顯示將執行的命令
        注意：-A 模式不需要 -e，且 -k 無效
  -k    保留資料夾結構（僅對「依副檔名」的 move/copy 有效）
  -e    副檔名列表（逗號分隔，例如：jpg,png,mp4；僅「依副檔名」模式必填）
  -h    顯示說明

參數：
  SRC   來源資料夾
  DEST  目標資料夾（move/copy 必填；delete/preview 依情境）

範例：
  # A2：整包搬移 ~/project 到 /backup（結果會變成 /backup/project）
  filemanage -m -A ~/project /backup

  # A2：整包複製 ~/project 到 /backup（結果會變成 /backup/project）
  filemanage -c -A ~/project /backup

  # A2：預覽將執行什麼命令
  filemanage -p -A ~/project /backup

  # 依副檔名：搬移 jpg,png，保留母資料夾+結構
  filemanage -m -k -e jpg,png ~/Projects ~/Backup/ProjectsImages
  ```
