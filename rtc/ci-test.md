# ci-test测试用例  

## busybox测试用例  
1. test_bzip2_case1-测试 busybox bzip2 压缩一个文件 [test_bzip2_case1](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/bz2/testcase_bz2.py)  
2. test_bzip2_case2-测试 busybox bzip2 压缩一个文件并busybox bunzip2解压 [test_bzip2_case2](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/bz2/testcase_bz2.py)  
3. test_bzip2_case3-测试 busybox bzip2 压缩一个文件并使用busybox bzcat查看 [test_bzip2_case3](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/bz2/testcase_bz2.py)  
4. test_cp_case1-测试 busybox cp 一个文件 [test_cp_case1](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/cp/testcase_cp.py)  
5. test_cp_exit_case2-测试 busybox cp 一个当前路径下已经存在的文件 [test_cp_exit_case2](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/cp/testcase_cp.py)  
6. test_gzip_case1-测试 busybox gzip 压缩一个文件 [test_gzip_case1](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/gz/testcase_gz.py)  
7. test_gunzip_case2-测试 busybox gzip 压缩一个文件并使用busybox gunzip解压该压缩文件 [test_gunzip_case2](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/gz/testcase_gz.py)  
8. test_mv_case1-测试 busybox mv 重命名一个文件 [test_mv_case1](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/mv/testcase_mv.py)  
9. test_setftpd_case1-测试 busybox ftpd 服务，包含客户端 cd、pwd、mkdir、rmdir、put、get、ls、delete 交互测试 [test_setftpd_case1](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/setftpd/testcase_setftpd.py)  
10. test_ftpdput_case2-测试 busybox tftp -p 上传一个文件 [test_ftpdput_case2](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/setftpd/testcase_setftpd.py)  
11. test_ftpdget_case3-测试 busybox tftp -g 下载一个文件 [test_ftpdget_case3](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/setftpd/testcase_setftpd.py)  
12. test_telnet_case1-测试 busybox telnet 是否能与本地 /etc/init.d/xinetd 服务建立连接 [test_telnet_case1](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/telnet/testcase_telnet.py)  
13. test_unzip_case1-测试 busybox unzip 解压 .zip 包 [test_unzip_case1](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/unzip/testcase_unzip.py)  
14. test_cat_case1-测试 busybox cat 输出一个文件的内容 [test_cat_case1](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/cat/testcase_cat.py)  
15. test_ftpget_case1-测试 busybox ftpget 下载一个文件 [test_ftpget_case1](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/ftpgetput/testcase_ftpgetput.py)  
16. test_ftpput_case2-测试 busybox ftpput 上传一个文件 [test_ftpput_case2](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/ftpgetput/testcase_ftpgetput.py)  
17. test_httpd_case1-测试 busybox httpd 服务，本地客户端验证访问静态页面 [test_httpd_case1](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/httpd/testcase_httpd.py)  
18. test_nslookup_case1-测试 busybox nslookup 是否能获取域名所对应的DNS信息 [test_nslookup_case1](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/tree/master/testcase/userapps/busybox/nslookup)  
19. test_tar_case1-测试 busybox tar 压缩一个文件 [test_tar_case1](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/tar/testcase_tar.py)  
20. test_uname_case1-测试 busybox uname -a 是否显示操作系统的发行编号 [test_uname_case1](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/uname/testcase_uname.py)  
21. test_busybox_wget_case1-测试 busybox wget http 下载功能 [test_busybox_wget_case1](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/wget/testcase_wget.py)  
22. test_busybox_wget_case2-测试 busybox wget ftp 下载功能 [test_busybox_wget_case2](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/wget/testcase_wget.py)  
23. test_busybox_wget_case3-测试 busybox wget https 下载功能 [test_busybox_wget_case3](https://git.rt-thread.com/alliance/rt-smart/ci-build/-/blob/master/testcase/userapps/busybox/wget/testcase_wget.py)  

## userapps测试用例  
