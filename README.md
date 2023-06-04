# git
git binary

# compare

|                  |       maze        |            objgraph            |
| ---------------- | ----------------- | ------------------------------ |
| 统计单位          | 字节数 + 个数      | 个数                           |
| 区分内建容器      | yes               | no                             |
| 分析所有 PyObject | yes               | no [only gc.get_objects()]     |
| 自动分析          | yes               | no 二次人肉分析                 |
| 事后分析          | yes               | no 需要在线上实时分析 有操作风险 |
| 反向引用图分类    | yes 凸显“泄漏”引用 | no                             |
| 分离模式视角      | yes               | yes                            |
| 合并模式视角      | yes               | no                             |
| size tree        | yes               | no                             |
|                  |                   |                                |
