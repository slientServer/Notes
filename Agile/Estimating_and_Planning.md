# 敏捷估计与规划
## 1. 规划的目的
### 1.1 规划的原因
- 减少风险
- 降低不确定性
- 提供更好的决策支持
- 建立信任
- 传递信息

## 2. 规划失败的原因
- 传统规划问题
	- 大约2/3项目会显著超预算
	- 产品中64%的功能很少或从不会被使用
	- 一般项目花费的时间会超出进度表100%
- 传统规划失败的原因
	- 基于活动而不是基于功能进行规划
	- 多任务处理导致更多的延迟
	- 不按优先级开发功能
	- 忽视了不确定性
	- 把估计当做承诺
	
## 3. 敏捷方法
### 3.1 项目的敏捷开发方法
- 敏捷小组作为一个整体工作
- 按短迭代周期工作
- 每次迭代交付一些成果
- 关注业务优先级
- 敏捷小组进行检查和调整

## 4. 使用故事点估计规模
规模的估计和持续时间的估计是相对独立的。
### 4.1 故事点是相对的
- 首先选取认为最小的故事作为1
- 其它的故事点可以基于1来估计
- 故事点反应的是项目的规模
- 每个team的估计是不同的

### 4.2 速度
- 速度是对开发小组的进度率的度量
- 敏捷估计的关键是先估算规模，之后推算出持续时间

## 5. 使用理想日进行估计

- 理想时间和耗用时间是不同的
- 利用理想时间进行估计可以体现用户故事的规模

## 6. 估计方法

- 回报渐减法则
- 将要做此工作的人对工作的估计比其他人作出的更准确
- 将要做或可能做的人共同估计
- 估计的尺度
	- 斐波那契数列
- 得到估计值得方法
	- 专家意见
	- 类比
	- 裂解
- 规划扑克

## 重估

- 只在用户故事的相对规模发生变化的时候进行全部重估
- 对于用户故事未全部完成的情况
	- 应该获取已完成部分的点数，对于未完成的部分可以在下次迭代中进行重估
	- 更好的选择是避免在一次迭中出现未完成的故事
	- 用户故事应该足够小

## 8. 故事点和理想日之间的抉择
- 故事点的优势
	- 有助于驱动跨功能的行为
		- 故事点估计的是项目的整体规模
		- 理想日需要考虑不同人员的身份
	- 故事点的估计不会过期
	- 故事点是对规模的纯粹估量
	- 故事点估计通常更快
	- 我的理想日不等于您的理想日
- 理想日的优势
	- 理想日在小组意外更容易解释
	- 理想日估计更容易开始

## 9. 确定主题的优先级
- 需要考虑的因素
	- 经济价值
	- 开发成本
	- 学习的知识
		- 项目的知识
		- 产品的知识
	- 风险
		- 处理顺序：高风险高价值、低风险高价值、低风险低价值、高风险低价值
## 10. 确定经济优先级

- 收入来源
	- 新收入
	- 增量收入
	- 留存收入
	- 操作效率
- 经济指标
	- 现值
		- 要在将来达到某一指定数值需要现在在银行存入的数值就是现值
		- 把将来的金额推回现值的过程称之为贴现（discount）
		- 公司对将来的金额进行体现的利率称之为机会成本（opportunity cost）
	- 净现值
		- 这算成当前价值的价值
	- 投资收益率
		- 内部收益率（Internal Rate of Return）或 Return on Investment
	- 回收期
		- 赚回投资需要的时间
	- 贴现回收期

## 11. 确定合意性优先级

- 客户满意的Kano模型
	- 阈值功能
	- 线性功能
	- 兴奋点和惊喜点
		- 增加产品的满意度，有可能增加额外的价格
- 相对权重
	- 收益和惩罚对比

## 12. 分割用户故事

- 分割的原因
	- 太大，超出迭代范围
	- 可以获取更加精确的估计
- 分割方法
	- 按照用户故事所支持的数据边界进行分割
	- 按照操作边界进行分割
	- 去除横切考虑
	- 不用满足性能考虑
	- 分割具有混合优先级的故事
	- 不要把故事分割成任务
	- 避免相关的变化的诱惑
	- 组合用户故事

## 13. 发布规划基础
- 确定满意条件
	- 日期驱动
	- 功能驱动
- 估计用户故事的规模
- 选择迭代周期
- 估计速度
	- 最好使用最近表现出来的速度
- 确定用户故事优先级
- 选择用户故事和发布日期

## 14. 迭代规划
- 速度驱动（Velocity Driven）
	- 调整优先级
	- 确定目标速度
	- 确定迭代目标
	- 选择用户故事
	- 分解用户故事成为单独的任务
	- 对任务进行估计
- 承诺驱动（Commitment Driven）

# 15. 选择迭代长度
- 需要考虑的因素
	- 发布的总时间长度
	- 不确定性的多少
	- 获得反馈的难易程度
	- 不用外部反馈，自行工作的意愿
	- 迭代的系统开销
	- 紧迫感的产生速度有多快

# 16. 估计速度
估计速度最好是一个范围。
- 使用历史值（平均值的60%-160%）
- 进行一次迭代
- 作出预测

# 17. 为不确定性缓冲计划

- 功能缓冲
- 进度缓冲
- 缓冲区的计算方法（至少反映到20%）
	- 平方和的平方根（多余10个用户故事）
	- 固定50%
- 多个缓冲区
- 进度缓冲区不是填料

#18. 规划多小组的项目
敏捷小组一般不超过7-10人。
- 为估计建立共同的基准
- 更早给用户故事添加细节
- 前瞻计划
- 在计划中加入馈送缓冲区

#19. 监督发布计划的执行

- 对未完成的工作计算速度的问题
	- 非常困难
	- 破坏开发小组与客户小组的信任
	- 导致需要处理工作的堆积
- 发布耗散图（burndown chat）
- 发布耗散条形图
- 停车场图

#20. 监督迭代计划的执行

- 任务板
- 不要跟踪个人速度
- 不要跟踪已完成工作量，而要跟踪剩余工作量

#21. 与计划有关的沟通

- 计划相关沟通是诚实的、频繁的、双向的
- 迭代小结

#22. 敏捷规划有效的原因

- 规划就是尝试找到一种解决产品开发(功能、资源、进度)问题的最佳方案
- 如何实现
	- 经常进行重规划
	- 对规模和持续时间的估计是独立的
	- 在不同层次上制定计划
	- 基于功能而不是基于任务制定计划
	- 小故事保持工作流畅（周转时间）
	- 每次迭代都要消除处理中的工作
	- 在小组层次跟踪
	- 承认不确定性并为之做计划
- 敏捷估计和规划的12条指导原则
	- 让整个小组参与
	- 在不同层次上进行规划
	- 使用不同的度量单位，让对工作量和持续时间的估计独立
	- 用功能或者日期来体现不确定性
	- 经常重规划
	- 跟踪进度并沟通
	- 承认学习的重要性
	- 规划具有适度规模的功能
	- 确定功能优先级
	- 把估计和计划建立在事实上
	- 保留一些松弛度
	- 通过前瞻计划协调多个小组

#23. 案例分析

---