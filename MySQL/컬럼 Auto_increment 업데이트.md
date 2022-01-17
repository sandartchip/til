
```sql
ALTER TABLE [테이블명] AUTO_INCREMENT=1;
SET @COUNT = 0;
UPDATE [테이블명] SET [AUTO_INCREMENT 열 이름] = @COUNT:=@COUNT+1;
```

```sql
ALTER TABLE `tb_board_item` AUTO_INCREMENT=1;
SET @COUNT = 0;
UPDATE `tb_board_item` SET board_item_key = @COUNT:=@COUNT+1;
```
