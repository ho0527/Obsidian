# connection failed: connection to server at "127.0.0.1", port 5432 failed: FATAL: could not open file "global/pg_filenode.map": Permission denied 該怎麼解決?

在 Windows + Docker 環境中，Permission denied 通常與容器內的資料目錄對應到宿主機的權限設定有關。以下是解決方法：

1. 確認 Docker Compose 或 Docker 指令的 Volume 設定
檢查是否正確對應了 PostgreSQL 的資料目錄。通常，資料目錄映射如下：

yaml
複製程式碼
volumes:
  - ./db:/var/lib/postgresql/data
確保宿主機的資料夾(./db)存在且有適當的權限。
可以先直接跳到第三點

2. 修正宿主機資料夾的權限
在 Windows 上，資料夾權限可能導致問題。確保對應的資料夾(例如 ./data)在 Docker Desktop 的共享目錄中設定正確：
開啟 Docker Desktop。
進入 Settings > Resources > File Sharing，確認資料夾已被共享。
如果需要，刪除並重新新增資料夾到共享列表。

3. 刪除並重新初始化 Volume
如果資料夾內容已損壞，嘗試刪除並重新初始化 Volume：
器的日誌，確認是否還有其他錯誤：

```bash
docker logs {container_id}
```

如果問題仍然存在，提供
```bash
docker-compose down -v
docker-compose up -d
```
這會重新生成對應的資料。

4. 檢查容器內的權限
進入容器，確認 PostgreSQL 用戶是否擁有資料目錄的正確權限：

```bash
docker exec -it {container_id} bash
ls -ld /var/lib/postgresql/data
chown -R postgres:postgres /var/lib/postgresql/data
```

5. 重啟容器
修正權限後，重新啟動容器：

```bash
docker restart *{container_id}*
```

6. 檢查 Docker 日誌
查看 PostgreSQL 容你的 docker-compose.yml 或 Docker 啟動指令，我可以進一步協助診斷。