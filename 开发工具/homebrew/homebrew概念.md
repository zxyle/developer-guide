

## Concept
| 序号 | 概念    | 原意   | 作用                 |
| ---- | ------- | ------ | -------------------- |
| 1    | Formula | 配方   | 安装脚本             |
| 2    | Bottle  | 瓶子   | 编译二进制分发版     |
| 3    | Tap     | 水龙头 | 第三方软件仓库       |
| 4    | Cask    | 酒桶   | 大软件               |
| 5    | Cellar  | 地窖   | 本地安装软件包的位置 |


[参考文章](https://medium.com/@kkworden/a-beginners-guide-to-homebrew-4b665956a74)

## 流程
- Formula是软件包安装的脚本
- 以上可以做成bottle形式的二进制分发版, 用来加快安装速度
- Formula安装脚本存储在Tap第三方仓库(通常是github)
- Cask用来安装包含GUI的大软件 比如firefox
- Cellar是本地软件包安装的位置