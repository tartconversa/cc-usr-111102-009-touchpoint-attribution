# 巡游与演唱触点的路径归因稳定性

本项目保存百货多业态经营研究的合成资料及输入读取工具。当前程序只解析文件并显示输入类型与记录数量，不进行统计分析、模型训练、优化求解或业务推荐。所有记录均为虚构，不能用于陈述真实商场经营结果。

## 输入约定

每行表示完整匿名旅程，touches 是按时刻排序的触点序列，converted 是终点，left_truncated 标明未知起点。重复触点并非重复上报，是否折叠由配置决定。

fixtures 为资料目录，src/journey_reader.py 为读取器，tests 为格式读取测试。输入在运行中保持不变；研究计算结果可写入独立的 .workspace-output 目录。

## 本地操作

Python 3.11 及以上版本，现有读取工具只依赖标准库，不需要下载第三方包。进入项目根目录：

    python -m src.journey_reader fixtures/journeys.jsonl

编译检查：

    python -m compileall -q src tests

格式读取测试：

    python -m unittest discover -s tests -v

## 固定运行环境

    docker build -t touchpoint-attribution:local .
    docker run --rm touchpoint-attribution:local

容器默认运行输入测试。镜像使用完整内容摘要固定，研究输入随项目一起复制。
