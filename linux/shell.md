//打包压缩文件
tar -czf jpg.tar.gz *.jpg

// 按行分割文件
split -l 2000000 20181212.log 

// https://coolshell.cn/articles/9070.html
awk '$2 ~ /[0-9a-z]+.png/ || NR==1 {print $2}' stat_edu24ol.sql.20181023.out
