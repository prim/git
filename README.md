
|                  | postman memory profile |            objgraph            |
| ---------------- | ---------------------- | ------------------------------ |
| 统计单位          | 字节数 + 个数           | 个数                           |
| 区分内建容器      | yes                    | no                             |
| 分析所有 PyObject | yes                    | no [only gc.get_objects()]     |
| 自动分析          | yes                    | no 二次人肉分析                 |
| 事后分析          | yes                    | no 需要在线上实时分析 有操作风险 |
| 反向引用图分类    | yes 凸显“泄漏”引用      | no                             |
| 分离模式视角      | yes                    | yes                            |
| 合并模式视角      | yes                    | no                             |
| size tree        | yes                    | no                             |




|                            |                    postman memory profile                       |            tcmalloc/jemalloc prof             |
| -------------------------- | -------------------------------------------------- | --------------------------------------------- |
| 提前接入工作                | 无 <br>适合处理正式服务器突然发生的内存泄漏事故        | 限制 malloc 库的选择 <br>需要打开 profile 开关  |
| 运行时消耗                 | 无                                                 | 有额外的 CPU / 内存消耗                        |
| 使用方式                   | 命令行工具采集 或 postman平台直接点点点               | 调整命令行参数 <br>自行收集统计分析/生成统计结果 |
| 分析 .bss/pthread/mmap/... | yes                                                | no                                            |
| 扩展性                     | yes <br> 事后分析 <br>可事后定制分析规则             | no <br>实时采集/统计数据 <br>定制需要在事前完成 |
| 支持 python                | yes                                                | no <br>需要禁用 python obmalloc               |
| python 内存的区分度         | 高 <br>非常完善分类机制                              | 低 <br>需要额外写 python 解栈                  |
| 分析所有 malloc 的来源/用途 | 绝大部分 <br> 少数没有引用关系或特征的内存块分析不出来 | yes                                           |
