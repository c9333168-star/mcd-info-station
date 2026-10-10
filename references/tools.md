# mcd-mcp 工具速查（麦麦情报站）

> 来源：麦当劳中国官方 MCP Server（`https://mcp.mcd.cn`，Streamable HTTP）。
> 工具名与官方一致，详见 https://github.com/M-China/mcd-mcp-server 。
> 限流：每 Token 600 次/分钟，超限返回 429。

## 时间

| Tool | 说明 | 要点 |
|---|---|---|
| `now-time-info` | 当前完整时间信息 | 每次会话开始先调用，作为一切"进行中/临期"判断的基准 |

## 活动日历

| Tool | 说明 | 要点 |
|---|---|---|
| `campaign-calendar` | 当月营销活动日历 | 返回进行中、往期、未来日期的活动；用 `now-time-info` 的结果对日期分档 |

## 优惠券

| Tool | 说明 | 要点 |
|---|---|---|
| `available-coupons` | 可领取的「麦麦省」券列表 | 白嫖清单 |
| `auto-bind-coupons` | 一键领取所有可领券 | 写操作，须用户显式授权 |
| `query-my-coupons` | 账户已有券 | 重点筛有效期 7 天内的临期券 |
| `query-store-coupons` | 指定门店可用券 | 需 `storeId`，与账号券可能不同 |

## 账户与抽奖

| Tool | 说明 | 要点 |
|---|---|---|
| `query-my-account` | 积分账户 | 含可用/累计/冻结/**即将过期**积分，临期积分是行动信号 |
| `query-lottery-info` | 积分抽奖活动信息 | 活动状态、奖池、消耗规则 |
| `draw-lottery` | 执行一次抽奖 | 写操作，消耗积分/次数，须授权 |
| `query-my-prizes` | 已中奖记录 | 分页，按中奖时间倒序 |

## 积分商城

| Tool | 说明 | 要点 |
|---|---|---|
| `mall-points-products` | 商城可兑换商品列表 | 兑换前置 |
| `mall-product-detail` | 商品详情 | 图片/积分/有效期/库存说明 |
| `mall-create-order` | 积分兑换下单 | 写操作，扣积分/库存，须授权 |
| `mall-order-list` / `mall-order-detail` | 商城订单查询 | 兑换后核对 |

## 主题活动（派对/品鉴会）

| Tool | 说明 | 要点 |
|---|---|---|
| `query-party-city` | 可参与城市列表 | 预约链路第一层 |
| `query-party-store` | 指定城市的门店列表 | 第二层 |
| `query-party-store-date` | 指定门店可预约日期 | 第三层 |
| `query-party-store-session` | 指定日期的场次 | 第四层 |
| `party-order-create` | 创建主题活动订单 | 写操作，须授权；四层信息齐备后才可调用 |

## 参考（联动用）

| Tool | 说明 | 要点 |
|---|---|---|
| `query-meals` / `query-meal-detail` | 菜单与套餐详情 | 活动对应餐品时使用 |
| `list-nutrition-foods` | 营养成分 | 新品/热量参考 |
| `query-nearby-stores` | 附近门店 | 需要门店位置的场景 |
