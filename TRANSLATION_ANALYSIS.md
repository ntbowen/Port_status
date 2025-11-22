# Port Status 翻译去重分析报告

## 📊 翻译统计

| 类别 | 数量 |
|------|------|
| **总翻译字符串** | 56 个 |
| **已在 luci-base 中** | 20 个 (35.7%) |
| **4IceG 特有翻译** | 33 个 (58.9%) |
| **复数形式** | 1 个 (1.8%) |
| **空占位符** | 2 个 (3.6%) |

## ✅ 已在 luci-base 中的翻译（无需重复）

这些翻译已经在 `/feeds/luci/modules/luci-base/po/zh_Hans/base.po` 中存在：

### 网络统计相关 (10 个)
- `Received bytes` → 接收字节
- `Received packets` → 接收数据包
- `Received multicast` → 接收组播
- `Receive errors` → 接收错误
- `Receive dropped` → 接收丢弃
- `Transmitted bytes` → 发送字节
- `Transmitted packets` → 发送数据包
- `Transmit errors` → 发送错误
- `Transmit dropped` → 发送丢弃
- `Collisions seen` → 检测到冲突

### 端口状态显示 (6 个)
- `Port status` → 端口状态
- `Speed: %d Mibit/s, Duplex: %s` → 速度：%d Mibit/s，双工：%s
- `Connected` → 已连接
- `no link` → 无连接
- `Part of zone %q` → 属于区域 %q
- `No zone assigned` → 未分配区域

### 网络接口相关 (2 个)
- `(no interfaces attached)` → （未连接接口）
- `Port is not part of any network` → 端口不属于任何网络

### 通用按钮 (2 个)
- `Cancel` → 取消
- `Save` → 保存

## 🆕 4IceG 特有翻译（需要添加）

这些是 Port Status 扩展功能专用的翻译，共 **33 个**：

### 端口标签编辑 (6 个)
1. `Edit Port Label` → 编辑端口标签
2. `Enter new label for this port:` → 输入此端口的新标签：
3. `Original label` → 原始标签
4. `Restore Original` → 恢复原始
5. `Click to edit label` → 点击编辑标签
6. `Label max 9 chars, description max 50 chars.` → 标签最多 9 个字符，描述最多 50 个字符。

### 端口描述 (1 个)
7. `Enter description (optional):` → 输入描述（可选）：

### 拖拽排序 (2 个)
8. `Hold to drag and reorder` → 按住拖动以重新排序
9. `Port order saved` → 端口顺序已保存

### 配置保存 (3 个)
10. `Port configuration saved successfully` → 端口配置保存成功
11. `User settings are saved to the /etc/user_defined_ports.json file.` → 用户设置保存到 /etc/user_defined_ports.json 文件。
12. `Saving configuration...` → 正在保存配置...

### 配置导入导出 (5 个)
13. `Save .json file` → 保存 .json 文件
14. `Upload .json file` → 上传 .json 文件
15. `Configuration file downloaded` → 配置文件已下载
16. `Configuration file not found` → 未找到配置文件
17. `Download error: %s` → 下载错误：%s

### 配置恢复 (7 个)
18. `Restore configuration` → 恢复配置
19. `This will overwrite current ports configuration. Continue?` → 这将覆盖当前端口配置。继续吗？
20. `Configuration restored successfully. Reloading...` → 配置恢复成功。正在重新加载...
21. `File restore failed: %s` → 文件恢复失败：%s
22. `Invalid configuration format` → 无效的配置格式
23. `Invalid JSON file: %s` → 无效的 JSON 文件：%s
24. `Restore` → 恢复

### 错误处理 (9 个)
25. `Save Error` → 保存错误
26. `Cannot save port configuration. ` → 无法保存端口配置。
27. `Directory /etc may be read-only or insufficient permissions. ` → 目录 /etc 可能为只读或权限不足。
28. `Try running: chmod 755 /etc && touch %s && chmod 644 %s` → 尝试运行：chmod 755 /etc && touch %s && chmod 644 %s
29. `Original error: %s` → 原始错误：%s
30. `Warning: Could not create port configuration file.` → 警告：无法创建端口配置文件。
31. `Port customizations will not be saved.` → 端口自定义设置将不会被保存。
32. `Check /etc directory permissions` → 检查 /etc 目录权限
33. `Device` → 设备

## 📁 文件说明

### 完整翻译文件
- **Port_status_zh-Hans.po** - 包含所有 56 个翻译（包括重复的）
- 适用于独立使用或参考

### 去重翻译文件（推荐）
- **Port_status_zh-Hans_deduplicated.po** - 仅包含 33 个 4IceG 特有翻译
- 避免与 luci-base 重复
- 减小翻译文件体积
- 便于维护

## 🔧 使用建议

### 方案 1：使用去重文件（推荐）
```bash
# 将去重文件放到正确位置
mkdir -p po/zh_Hans/
cp Port_status_zh-Hans_deduplicated.po po/zh_Hans/port_status.po
```

**优点**：
- ✅ 避免重复翻译
- ✅ 文件更小（33 vs 56 条）
- ✅ 依赖 luci-base 的标准翻译
- ✅ 更易维护

**注意**：需要确保 luci-base 的中文翻译包已安装

### 方案 2：使用完整文件
```bash
# 使用完整翻译文件
mkdir -p po/zh_Hans/
cp Port_status_zh-Hans.po po/zh_Hans/port_status.po
```

**优点**：
- ✅ 独立完整，不依赖其他包
- ✅ 适合作为独立应用发布

**缺点**：
- ❌ 与 luci-base 有 20 个重复翻译
- ❌ 文件较大

## 📝 复数形式处理

简体中文不区分单复数，因此：
```po
msgid "Part of network:"
msgid_plural "Part of networks:"
msgstr[0] "属于网络："
```

## ⚠️ 注意事项

1. **Device** 这个词在 luci-base 中可能有翻译，但上下文不同，建议保留
2. 所有格式化占位符 (`%s`, `%d`, `%q`) 必须保持不变
3. 文件路径和命令（如 `chmod`）保持原样不翻译
4. 编译时会自动生成 `.lmo` 二进制文件

## 🎯 推荐做法

**使用去重文件** + **确保 luci-i18n-base-zh-cn 已安装**

这样可以：
- 减少翻译文件大小 41%
- 避免维护重复内容
- 保持与 LuCI 标准的一致性
