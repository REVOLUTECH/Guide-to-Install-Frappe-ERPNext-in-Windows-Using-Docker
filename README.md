
    bench init --skip-redis-config-generation --frappe-branch develop frappe-bench
    cd frappe-bench

    bench set-config -g db_host mariadb
    bench set-config -g redis_cache redis://redis-cache:6379
    bench set-config -g redis_queue redis://redis-queue:6379
    bench set-config -g redis_socketio redis://redis-socketio:6379
    
    bench new-site revolutech.localhost --no-mariadb-socket 
    
    bench --site revolutech.localhost set-config developer_mode 1
    bench --site revolutech.localhost clear-cache   
    
    bench get-app --branch develop --resolve-deps erpnext
    bench --site revolutech.localhost install-app erpnext
    
    
    bench start
    
   
