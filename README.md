# 11/24作業

## 創建 teacher 帳號 

- 設定密碼

```bash
sudo useradd -m -s /bin/bash teacher
echo "teacher:teacher" | sudo chpasswd
```

- 撰寫程式

> nano tc.sh

```bash
#!/bin/bash
while read line ;do
echo ${line} >> /tmp/teacher_history.log
done < /home/teacher/.bash_history
```

- 把`/home/teacher/.bash_history` 的資料一行一行寫入`/tmp/teacher_history.log`

## 變更檔案權限

> chmod +x tc.sh

- 撰寫程式

> nano tm.sh

```bash
#!/bin/bash
inotifywait -mre MODIFY /home/teacher --format '%T,%w,%f,%e' --timefmt '%Y-%m-%d-%H-%M-%S' >> /tmp/teacher_teacher_inotify.log
```

- 把inotify指令的指定目錄設定為 `/home/teacher` 並且把檔案輸出 `/tmp/teacher_teacher_inotify.log`
 
- 變更檔案權限

> chmod +x tm.sh
