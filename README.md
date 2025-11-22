# Port_status

![GitHub release (latest by date)](https://img.shields.io/github/v/release/4IceG/Port_status?style=flat-square)
![GitHub stars](https://img.shields.io/github/stars/4IceG/Port_status?style=flat-square)
![GitHub forks](https://img.shields.io/github/forks/4IceG/Port_statuse?style=flat-square)
![GitHub All Releases](https://img.shields.io/github/downloads/4IceG/Port_status/total)

> [!NOTE]
> <img src="https://raw.githubusercontent.com/4IceG/Personal_data/master/dooffy_design_icons_EU_flags_United_Kingdom.png" height="24">
> My small modification of "Port Status".   
> <img src="https://raw.githubusercontent.com/4IceG/Personal_data/master/dooffy_design_icons_EU_flags_Poland.png" height="24">
> Moja mała modyfikacja "Statusu portów".

> [!IMPORTANT]
> <img src="https://raw.githubusercontent.com/4IceG/Personal_data/master/dooffy_design_icons_EU_flags_United_Kingdom.png" height="24">   
> ***Change port label / description*** - click on the header   
> ***Change port order*** - drag and drop (grab the area around the icon)   
> <img src="https://raw.githubusercontent.com/4IceG/Personal_data/master/dooffy_design_icons_EU_flags_Poland.png" height="24">   
> ***Zmiana etykiety / opisu portu*** - klikamy w nagłówek   
> ***Zmiana kolejności portów*** - przeciągnij i upuść (chwytamy za obszar wokół ikony)

> [!NOTE]
> <img src="https://raw.githubusercontent.com/4IceG/Personal_data/master/dooffy_design_icons_EU_flags_United_Kingdom.png" height="24">
> ***Installation on a router:***

<details>
   <summary>Show me</summary>

1. Replace the contents of the 29_ports.js file using WinSCP (/www/luci-static/resources/view/status/include).
2. Change the permissions in luci-mod-status-index.json (/usr/share/rpcd/acl.d/luci-mod-status-index.json).
We search for the section with permissions for luci-mod-status-index-ports and replace it with this:   

``` bash
	"luci-mod-status-index-ports": {
	  "description": "Grant access to port status display",
		"read": {
			"file": {
				"/etc/user_defined_ports.json": [ "read" ]
			},
			"ubus": {
				"file": [ "read" ],
				"luci": [ "getBuiltinEthernetPorts" ]
			}
		},
		"write": {
			"file": {
				"/etc/user_defined_ports.json": [ "write" ]
			},
			"ubus": {
				"file": [ "write" ]
			}
		}
	},
```    
4. Cleare browser cache.
5. The first time, it created the /etc/user_defined_ports.json file, but it was empty. Repeate the configuration and We got what we want.
</details>

> [!NOTE]
> <img src="https://raw.githubusercontent.com/4IceG/Personal_data/master/dooffy_design_icons_EU_flags_Poland.png" height="24">
> ***Instalacja na routerze:***

<details>
   <summary>Pokaż</summary>

1. Podmieniamy zawartość pliku 29_ports.js za pomocą WinSCP (/www/luci-static/resources/view/status/include)
2. Zmieniamy uprawnienia w luci-mod-status-index.json (/usr/share/rpcd/acl.d/luci-mod-status-index.json). Szukamy sekcji z uprawnieniami dla luci-mod-status-index-ports i podmieniamy na:   

``` bash
	"luci-mod-status-index-ports": {
	  "description": "Grant access to port status display",
		"read": {
			"file": {
				"/etc/user_defined_ports.json": [ "read" ]
			},
			"ubus": {
				"file": [ "read" ],
				"luci": [ "getBuiltinEthernetPorts" ]
			}
		},
		"write": {
			"file": {
				"/etc/user_defined_ports.json": [ "write" ]
			},
			"ubus": {
				"file": [ "write" ]
			}
		}
	},
```    
3. Czyścimy cache przeglądarki
4. Za pierwszym razem może utworzyć plik /etc/user_defined_ports.json ale pusty, ponawiamy konfigurację i już mamy to co być powinno.
</details>

> [!NOTE]
> <img src="https://raw.githubusercontent.com/4IceG/Personal_data/master/dooffy_design_icons_EU_flags_Poland.png" height="24">
> ***Dodanie przy kompilacji:***

<details>
   <summary>Pokaż</summary>

1. Podmieniamy plik 29_ports.js w lokalizacji
   > /feeds/luci/modules/luci-mod-status/htdocs/luci-static/resources/view/status/include
2. Zmieniamy uprawnienia w luci-mod-status-index.json, plik znajduje się w
   > /feeds/luci/modules/luci-mod-status/root/usr/share/rpcd/acl.d/luci-mod-status-index.json.

	Szukamy sekcji z uprawnieniami dla luci-mod-status-index-ports i podmieniamy na:   
``` bash
	"luci-mod-status-index-ports": {
	  "description": "Grant access to port status display",
		"read": {
			"file": {
				"/etc/user_defined_ports.json": [ "read" ]
			},
			"ubus": {
				"file": [ "read" ],
				"luci": [ "getBuiltinEthernetPorts" ]
			}
		},
		"write": {
			"file": {
				"/etc/user_defined_ports.json": [ "write" ]
			},
			"ubus": {
				"file": [ "write" ]
			}
		}
	},
```    
3. Dodajemy tłumaczenie dla nowych okienek / elementów menu. Kopiujemy linijki tłumaczenia z pliku Port_status.pot do pliku w lokalizacji /feeds/luci/modules/luci-base/po/pl
4. Dopisujemy do pliku
   > /package/base-files/files/lib/upgrade/keep.d/base-files-essential

	na końcu nową linijkę /etc/user_defined_ports.json, aby zachować ustawienia poczynione przez użytkownika podczas generowania archiwum z kopią zapasową
</details>



### <img src="https://raw.githubusercontent.com/4IceG/Personal_data/master/dooffy_design_icons_EU_flags_United_Kingdom.png" height="24"> Preview / <img src="https://raw.githubusercontent.com/4IceG/Personal_data/master/dooffy_design_icons_EU_flags_Poland.png" height="24"> Podgląd

<img width="1290" height="510" alt="Status_port" src="https://github.com/user-attachments/assets/cee839c8-f8ef-444b-b888-456f0761d7fc" />

![](https://github.com/4IceG/Personal_data/blob/master/zrzuty/Port_status.gif?raw=true)

---

## 📊 Technical Comparison / 技术对比

### Differences between 4IceG version and Official LuCI version

### 4IceG 版本与 LuCI 官方版本的区别

| Feature / 功能 | 4IceG Version | Official LuCI |
|----------------|---------------|---------------|
| **File Size / 文件大小** | 1048 lines | 366 lines |
| **Custom Port Labels / 自定义端口标签** | ✅ Yes | ❌ No |
| **Port Description / 端口描述** | ✅ Yes (max 50 chars) | ❌ No |
| **Drag & Drop Reorder / 拖拽排序** | ✅ Yes (mouse + touch) | ❌ No |
| **Configuration Persistence / 配置持久化** | ✅ `/etc/user_defined_ports.json` | ❌ No |
| **Import/Export Config / 导入导出配置** | ✅ Yes (.json file) | ❌ No |
| **Touch Support / 触摸支持** | ✅ Yes (400ms delay) | ❌ No |
| **Edit Modal / 编辑对话框** | ✅ Yes | ❌ No |

### 🆕 New Features in 4IceG Version / 4IceG 版本新增功能

#### 1. **Port Label Customization / 端口标签自定义**

- Click on port name to edit / 点击端口名称进行编辑
- Maximum 9 characters / 最多 9 个字符
- Restore to original label / 恢复原始标签

#### 2. **Port Description / 端口描述**

- Optional description field / 可选描述字段
- Maximum 50 characters / 最多 50 个字符
- Displayed below port label / 显示在端口标签下方

#### 3. **Drag & Drop Reordering / 拖拽重新排序**

- Hold 200ms (mouse) or 400ms (touch) to start dragging / 按住 200ms（鼠标）或 400ms（触摸）开始拖拽
- Visual placeholder during drag / 拖拽时显示占位符
- Auto-save order / 自动保存顺序

#### 4. **Configuration Management / 配置管理**

- **Export**: Download `user_defined_ports.json` / 导出：下载配置文件
- **Import**: Upload and restore configuration / 导入：上传并恢复配置
- **Persistence**: Survives firmware upgrades (if configured) / 持久化：固件升级后保留（如已配置）

### 🔧 Technical Implementation / 技术实现

#### New Dependencies / 新增依赖

```javascript
'require dom';   // DOM manipulation
'require poll';  // Polling control
```

#### New RPC Calls / 新增 RPC 调用

```javascript
var callWritePortConfig = rpc.declare({
    object: 'file',
    method: 'write',
    params: ['path', 'data']
});
```

#### Data Structure / 数据结构

```javascript
// 4IceG Enhanced Structure / 增强结构
{
    device: 'eth0',
    role: 'lan',
    netdev: <object>,
    label: 'LAN1',              // Custom label / 自定义标签
    originalLabel: 'eth0',      // Original label / 原始标签
    description: '客厅交换机'    // Description / 描述
}

// Official Basic Structure / 官方基础结构
{
    device: 'eth0',
    role: 'lan',
    netdev: <object>
}
```

### 📁 File Locations / 文件位置

| Component / 组件 | Path / 路径 |
|------------------|------------|
| **4IceG Script** | `package/Applications/4IceG/Port_status/29_ports.js` |
| **Official Script** | `feeds/luci/modules/luci-mod-status/htdocs/luci-static/resources/view/status/include/29_ports.js` |
| **User Config** | `/etc/user_defined_ports.json` |
| **ACL Config** | `/usr/share/rpcd/acl.d/luci-mod-status-index.json` |

### 🎯 Use Cases / 使用场景

**4IceG Version is ideal for / 4IceG 版本适用于:**

- 🏢 Enterprise networks with many ports / 拥有多个端口的企业网络
- 🏠 Home labs requiring clear port identification / 需要清晰端口标识的家庭实验室
- 🔧 Network administrators who frequently reconfigure / 经常重新配置的网络管理员
- 📝 Scenarios requiring port documentation / 需要端口文档的场景

**Official Version is sufficient for / 官方版本足够用于:**

- 🔍 Basic port status monitoring / 基础端口状态监控
- 📱 Simple home routers / 简单的家用路由器
- 💡 Users who don't need customization / 不需要自定义的用户

### ⚠️ Important Notes / 重要说明

1. **Permissions Required / 需要权限**
   - Read/Write access to `/etc/user_defined_ports.json`
   - Modified ACL configuration in `luci-mod-status-index.json`

2. **Browser Cache / 浏览器缓存**
   - Clear cache after installation / 安装后清除缓存
   - Hard refresh (Ctrl+F5) recommended / 建议强制刷新

3. **Backup Persistence / 备份持久化**
   - Add `/etc/user_defined_ports.json` to `/package/base-files/files/lib/upgrade/keep.d/base-files-essential`
   - Ensures settings survive sysupgrade / 确保设置在系统升级后保留
