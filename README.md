# i18n

i18n of golang

#### 使用方法

- 下载i18n

```go
go get -u github.com/itmisx/i18n
```

* 定义 code 语言包

```go
var langPack1 = map[string]map[interface{}]interface{}{
	"zh-cn": {
		1000: "输入有误",
	},
	"en-us": {
		1000: "Input error",
	},
}
```

* 定义key 语言包，支持多级嵌套

```go
var langPack2 = map[string]map[interface{}]interface{}{
	"zh-cn": {
		"author": "smally84",
		"user": map[string]string{
			"name": "姓名",
			"sex":  "性别",
		},
	},
	"en-us": {
		"user": map[string]string{
			"name": "name",
			"sex":  "sex",
		},
	},
}
```

* 定义语言模板

```go
var langPack3 = map[string]map[interface{}]interface{}{
	"zh-cn": {
		"hello{name}": "你好{name}",
	},
	"en-us": {
		"hello{name}": "hello{name}",
	},
}
```

#### 加载语言包

```go
i18n.LoadLangPack(langPack1, langPack2, langPack3)
```

#### 翻译

```go
fmt.Println(T("zh-cn", 1000)) # 输出：输入有误
fmt.Println(T("zh-cn", "user.name")) # 输出：姓名
fmt.Println(T("zh-cn", "hello{name}", map[string]string{"name": "world"})) # 输出：helloword
```
