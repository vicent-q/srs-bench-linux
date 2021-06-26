# srs-bench-linux
SB(SRS Bench) is a benchmark tool for HTTP-FLV, RTMP, HLS 

## About
服务器负载测试工具SB(SRS Bench)：

1. 模拟huge并发：2G内存就可以开300k连接。基于states-threads的协程。
1. 支持HLS解析和测试，下载ts片后等待一个切片长度，模拟客户端。支持HLS点播和直播。执行程序：`./objs/sb_hls_load`
1. 支持HTTP负载测试，所有并发重复下载一个http文件。可将80Gbps带宽测试的72Gbps。执行程序：`./objs/sb_http_load `
1. 支持RTMP流播放测试，一个进程支持5k并发。执行程序：`./objs/sb_rtmp_load`
1. 支持RTMP流推流测试，一个进程支持500个并发。执行程序：`./objs/sb_rtmp_publish`
1. RTMP协议使用高性能服务器SRS([SimpleRtmpServer](https://github.com/ossrs/srs))的协议栈。

注意：

1. HTTP/HLS：依赖服务器Content-Length，不支持chunked方式(chunked时会把所有内容当做body一直读)。
2. 所有程序都在Linux下运行，模拟客户端运行。
