# DDNS

配置文件路径：`/etc/config/ddns`

```
config service 'myddns_ipv4'
	option enabled '1'
	option use_ipv6 '0'
	option service_name 'aliyun.com'
	option lookup_host 'url'
	option domain 'url'
	option username ''
	option password ''
	option ip_source 'network'
	option ip_network 'wan'
	option interface 'wan'
	option use_syslog '2'
	option check_unit 'minutes'
	option force_unit 'minutes'
	option retry_unit 'seconds'
```
