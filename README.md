# Clash Rules

Clash/Mihomo 规则集镜像仓库，通过 GitHub Actions 自动从上游同步。

## 目录结构

```
rules/
├── MetaCubeX/        ← 来自 MetaCubeX/meta-rules-dat
│   ├── geosite/       ← behavior: domain
│   └── geoip/         ← behavior: ipcidr (需 no-resolve)
├── wwqgtxx/           ← 来自 wwqgtxx/clash-rules
├── ACL4SSR/           ← 来自 ACL4SSR/ACL4SSR
└── custom/            ← 本地自定义规则
```

## 上游来源

| 来源 | 说明 |
|------|------|
| [MetaCubeX/meta-rules-dat](https://github.com/MetaCubeX/meta-rules-dat) | GeoSite + GeoIP 规则集（.mrs） |
| [wwqgtxx/clash-rules](https://github.com/wwqgtxx/clash-rules) | fakeip-filter 规则 |
| [ACL4SSR/ACL4SSR](https://github.com/ACL4SSR/ACL4SSR) | UnBan 白名单规则 |

## 自动同步

每天北京时间 11:00 自动运行 GitHub Actions 同步上游最新规则。也可手动触发。

## OpenClash 配置示例

```yaml
rule-providers:
  cn:
    type: http
    behavior: domain
    format: mrs
    path: ./rules/MetaCubeX/geosite/cn.mrs
    url: https://raw.githubusercontent.com/zhimadelvdou/Clash-rules/main/rules/MetaCubeX/geosite/cn.mrs
    interval: 86400
```
