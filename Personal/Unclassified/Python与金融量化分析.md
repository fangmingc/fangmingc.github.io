# Python与金融量化分析

## 股票
股票是股份公司发给出资人的一种凭证，股票持有者是股份公司的股东。

#### 股票的作用
- 出资证明、证明股东身份、对公司经营发表意见
- 公司分红、交易获利

###上市/IPO
企业通过证券交易所公开向社会增发股票以募集资金

### 融资、私募、风投

### 股票分类
- 按业绩分类
	- 蓝筹股：资本雄厚、信誉优良的公司的股票
	- 绩优股：业绩优良公司的股票
	- ST股：特别处理股票、连续两年亏损或每股净资产低于股票面值
- 按上市地区分类
	- A股：中国大陆上市（上海、深圳），人民币认购买卖（T+1，涨跌幅10%）
	- B股：中国大陆上市，外币认购买卖（T+1，T+3）
	- H股：中国香港上市（T+0，涨跌幅不设限制）
	- N股：美国纽约上市（T+0，涨跌幅不设限制）
	- S股：新加坡上市（T+0，涨跌幅不设限制）
- 交易规则：（政府规定）
	- T+0：
	- T+1：今日买不能今日卖，至少隔一天卖，涨跌幅
	- T+2：
	- T+3：

### 股票市场的构成
- 上市公司
- 投资者（包括机构投资者）
- 证监会、证券业协会、交易所
- 证券中介机构（券商）

#### 交易所
- 上海证券交易所：只有一个主板（泸指）
- 深圳证券交易所：
	- 主板：大型成熟企业（深成指）
	- 中小板：经营规模较小
	- 创业板：尚处于成长期的创业企业

### 影响股价的因素
- 公司自身隐私\*\*
	- 经营、营收、信用
- 行业因素
	- 行业在国民经济中的地位的变更
 - 市场因素\*\*
	- 投资者的动向
- 心理因素
- 经济因素
- 政治因素

### 股票买卖（A股）
- 委托买卖股票
	- 个人不能直接秒买，需要在券商开户，进行委托购买
- 股票交易日
	- 非法定节假日和非交易所休市日
- 股票交易时间
	- 9：15-9：25 开盘集合竞价时间
	- 9：30-11：30 前市，连续竞价时间
	- 13：00-15：00 后市，连续竞价时间
	- 14：57-15：00 深交所收盘集合竞价时间
- T+1交易制度
	- 股票面如当天不能卖出，要在买入后一个交易日才能卖出
- 涨停、跌停限制

### 金融分析
- 基本面分析：分析当前局势
	- 宏观经济面分析
		- 国家财政政策
		- 货币政策
	- 行业分析
	- 公司分析：
		- 财务数据
		- 业绩报告
- 技术面分析：各项技术指标
	- K线：当日的开盘价、收盘价、最低价、最高价
		- 分实体和影线，影线分为上影线和下影线
			- 上影线为最高价
			- 下影线为最低价
		- 阳线
			- 实体顶部为收盘价
			- 实体底部为开盘价
		- 阴线
			- 实体顶部为开盘价
			- 实体底部为收盘价
	- MA(均线)
		- 前几天的平均收盘价（一般有五天、六十天）
	- KDJ(随机指标)
	- MACD(指数平滑移动平均线)

## 金融量化投资
- 量化投资
	- 利用就三级树并且采用但一定的数学模型去时间投资理念，实现投资策略的过程
- 量化投资的优势

### 量化策略
- 量化策略
	- 输入
		- 行情数据
		- 财务数据
		- 自定义数据
		- 投资经验
	- 策略
		- 选股
		- 择时
		- 仓位管理
		- 止盈止损
	- 输出
		- 买入信号
		- 卖出信号
		- 交易费用
		- 收益

- 核心内容
	- 选股
	- 择时
	- 仓位管理
	- 止盈止损

- 策略的周期
	- 产生想法/学习知识
	- 实现策略：python
	- 检验策略：回测/模拟交易
	- 实盘交易
	- 优化策略/放弃策略

### 量化投资与Python
- 为什么选择Python
	- 其他选择Excel、SAS/SPSS、R
- 量化投资第三方相关模块
	- NumPy:数据批量计算
	- pandas：表计算与数据分析
	- Matplotlib：图表绘制
- 自己编写
	- NumPy+pandas+Matplotlib+...
- 在线平台：
	- 聚宽、优矿、米筐、Quantopian
- 开源框架
	- RQAlpha
	- QUANTAXIS



