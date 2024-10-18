# proxy_cache

```
proxy_cache_path /data/nginx/cache levels=1:2;  # 第二层级有16*256=4096个目录
/data/nginx/cache/b/51/d7b6e5978e3f042f52e875005925e51b 

proxy_cache_path /data/nginx/cache levels=1:2:2 keys_zone=cache_zone:100m max_size=100g inactive=365d use_temp_path=off;

```

[proxy_cache_path](https://nginx.org/en/docs/http/ngx_http_proxy_module.html#proxy_cache_path)


1. 实现目录缓存
2. 实现levels=1:2:2
3. 实现keys_zone=cache_zone:100m, name=cache_zone, 内存缓存CacheSizeMax=100m (默认使用btree实现)
4. 实现max_size=100g 最大文件系统缓存大小
5. inactive 指定了项目在不被访问的情况下能够在内存中保持的时间
6. use_temp_path=off or use_temp_path=/data/nginx/cache/temp
7. max_files 总缓存文件数量(与max_size共同决定能缓存的大小和数量)
8. 待定[manager_files=number] [manager_sleep=time] [manager_threshold=time] [loader_files=number] [loader_sleep=time] [loader_threshold=time] [purger=on|off] [purger_files=number] [purger_sleep=time] [purger_threshold=time]; 

## vfs
https://github.com/rainycape/vfs
https://github.com/avfs/avfs
https://github.com/C2FO/vfs
https://github.com/spf13/afero