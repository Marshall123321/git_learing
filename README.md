# Auspice Embed 命令行工具

将 Auspice 的 Web 查看工具和 JSON 数据结合,
并打包成单个 HTML 页面的命令行工具.

## 安装说明

需要使用 Python 3.7 或以上版本.
在 [Release 页面](http://192.168.2.4:8099/hrj/auspice/-/releases)
查看版本并复制 .whl 安装包的 URL,
然后在 Python 虚拟环境中执行如下命令安装.
安装后得到 auspice_embed 命令行工具.

```bash
pip install "<安装包 URL>"
```

## 运行说明

单独运行 `auspice_embed` 命令可查看帮助,
第一个参数是输入文件路径, 第二个参数是输出文件路径
(可选, 默认是 output.html).

```
Usage:
  auspice_embed auspice.json [output.html]
```

## 翻译说明

页面中的文本字符串通过 `src/locales` 目录下的配置文件翻译为中文,
修改翻译文本后需要重新构建前端代码.
配置文件中的文本可能不全, 需要手动添加.
另外页面中有部分文本未暴露给 i18n 接口, 需要修改代码.

## 开发说明

需要使用 Python 3.7 或以上版本, 以及 Node 16.

### Auspice 前端

修改过的 Auspice 前端代码位于 `src` 目录下,
去除了代码中的 js 异步加载逻辑并修改了 JSON 数据读取逻辑.
通过 `npm install` 安装依赖,
通过 `npm run build` 命令构建前端代码,
通过 `npm run dev` 命令运行开发模式
(该模式使用了 `loadData-dev.js` 中的样例数据).

### Auspice Embed 工具

命令行工具使用 Python 编写, 代码位于 `auspice_embed` 目录下.
该工具基于编译好的前端代码来实现打包功能.
通过 `npm run dev:py` 安装开发模式,
通过 `npm run build:py` 构建 wheel 安装包.
