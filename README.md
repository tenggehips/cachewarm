# cachewarm

**规划缓存预热的顺序与资源。**

`cachewarm` —— 按命中率收益与预热成本排优先级，给出预热批次

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`cachewarm.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install tenggehips-cachewarm
```

装完直接用命令名调用：

```bash
cachewarm --help
```

也可以不用安装，直接把 `cachewarm.py` 拷走用——它只依赖标准库。

## 为什么需要它

预热顺序错了会挤掉更有价值的缓存

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 缓存预热策略 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python cachewarm.py --file input.txt
python cachewarm.py --text "示例内容"
python cachewarm.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 预算是静态比例分配，不考虑实际执行顺序。
- 不接真实队列，只做分配表。

## 跑测试

```bash
python test_cachewarm.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/tenggehips/cachewarm>

---

## 关于作者

tenggehips 做缓存预热策略相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://tenggehips.github.io>
- 仓库：<https://github.com/tenggehips/cachewarm>

## 许可

MIT，见 [LICENSE](LICENSE)。
