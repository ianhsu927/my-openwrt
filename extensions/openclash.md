# OpenClash

## 配置文件

```bash
# clash 二进制文件
# Path: /etc/openclash/core/clash_meta
# 自定义规则
# Path: /etc/openclash/custom/openclash_custom_rules.list
```

| 目录                                              | 说明             |
| ------------------------------------------------- | ---------------- |
| /etc/openclash/core/clash_meta                    | clash 二级制文件 |
| /etc/openclash/config.yaml                        | 配置文件         |
| /etc/openclash/custom/openclash_custom_rules.list | 自定义规则       |

openclash 自定义配置

1. 不代理 ssh 端口, `DST-PORT,22,DIRECT`
