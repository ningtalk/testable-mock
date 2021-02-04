# TestableMock

换种思路写Mock，让单元测试更简单。

无需初始化，不挑测试框架，甭管要换的是私有方法、静态方法、构造方法还是其他任何类的任何方法，也甭管要换的对象是怎么创建的。写好Mock定义，加个`@MockMethod`注解，一切统统搞定。

- 文档：https://alibaba.github.io/testable-mock/
- 国内文档镜像：http://freyrlin.gitee.io/testable-mock/

阅读[这里](https://mp.weixin.qq.com/s/KyU6Eu7mDkZU8FspfSqfMw)了解更多故事。

> 特别说明
> 1. 如遇到"Attempt to access non-static member in mock method"错误，参见[常见问题](https://alibaba.github.io/testable-mock/#/zh-cn/doc/frequently-asked-questions)第8条
> 2. 如果有遇到其他任何使用问题和建议，请直接在[Issue](https://github.com/alibaba/testable-mock/issues)中提出，也可通过[Pull Request](https://github.com/alibaba/testable-mock/pulls)提交您的代码，我们将在24小时内回复并处理

-----

## 版本计划

`TestableMock`正在持续迭代演进，以下版本计划可能在开发过程中发生调整

- `0.4` 当前版本，进行中的工作内容参考[Issue](https://github.com/alibaba/testable-mock/issues)清单
- `0.5` 实现以"独立Mock类"为单元的Mock方法复用机制，让测试类之间可以方便复用相同的Mock方法
- `0.6` 实现将Mock方法的默认生效范围缩小至当前被测类，避免Mock方法在测试类之间相互影响
- `1.0` 功能稳定，一个崭新的开始

## 目录结构

```bash
|-- testable-parent       ➜ 提供各子模块的公共父pom文件
|-- testable-all          ➜ 依赖聚合，便于一次性引用所有子模块功能
|-- testable-processor    ➜ 编译期代码预处理模块，提供测试辅助功能
|-- testable-agent        ➜ JavaAgent模块，提供Mock测试相关功能
|-- testable-core         ➜ 基础功能模块，提供Mock相关注解和工具类
|-- testable-maven-plugin ➜ Maven插件模块，用于简化JavaAgent注入
|-- demo
|   |-- java-demo         ➜ Java语言的示例代码
|   `-- kotlin-demo       ➜ Kotlin语言的示例代码
`-- docs                  ➜ 项目使用文档
```

## 构建项目

主项目使用JDK 1.6+和Maven 3+版本构建，其中`demo`子项目需要JDK 1.8+版本。

```bash
mvn clean install
```

## 本地生成文档

```bash
docsify serve docs
```

> TestableMock文档使用`docsify`工具生成，构建前请安装[nodejs](https://nodejs.org/en/download/)运行时，并使用`npm install -g docsify`命令安装文档生成工具。

