# 命名规则

### 文件名

- 包含应用 `main` 函数的文件为整个项目的主文件，需要与应用名称简写相同。例如：`Gogs` 的主文件需命名为 `gogs.go`。

### 函数或方法

- 若函数或方法为判断类型（返回值主要为 `bool` 类型），则名称应以 `Has`, `Is`, `Can` 或 `Allow` 等判断性动词开头：

	```go
	func HasPrefix(name string, prefixes []string) bool { ...
	func IsEntry(name string, entries []string) bool { ...
	func CanManage(name string) bool { ...
	func AllowGitHook() bool { ...
	```
	
### 常量

- 常量均需使用全部大写字母组成，并使用下划线分词：

	```go
	const APP_VER = "0.3.5.0519 Alpha"
	```
	
- 如果是枚举类型的常量，需要先创建相应类型：

	```go
	type Scheme string
	
	const (
		HTTP  Scheme = "http"
		HTTPS Scheme = "https"
	)
	```

### 变量

- 变量命名基本上遵循相应的英文翻译。
- 在相对简单的环境（对象数量少、针对性强）中，可以将一些名称由完整单词简写为单个字母，例如：
	- `user` 可以简写为 `u`
	- `userId` 可以简写 `uid`
- 若变量类型为 `bool` 类型，则名称应以 `Has`, `Is`, `Can` 或 `Allow` 开头：

	```go
	var isExist bool
	var hasConflict bool
	var canManage bool
	var allowGitHook bool
	```
- 上条规则也适用于 ORM 模型：

	```go
	type Webhook struct {
		Id          	int64
		RepoId      	int64
		Url         	string 	`xorm:"TEXT"`
		ContentType 	int
		Secret      	string 	`xorm:"TEXT"`
		Events      	string 	`xorm:"TEXT"`
		*HookEvent  			`xorm:"-"`
		IsSsl       	bool
		IsActive    	bool
		HasAvatar   	bool
		CanManage   	bool
		AllowGitHook	bool
	}
	```

#### 变量命名惯例

- 代表某个用户：`u`
- 代表某个用户 ID：`uid`
- 代表某个索引：`idx`
- 代表某个值：`val`
