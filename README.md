#### 一，是什么

PEC (产品中心) 按照系统设计规划属于**信贷基础域范畴(BEC,DEC,REC,PEC,FCC)**

#### 二，有什么功能

##### 1、模版管理
<img width="1223" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/76c0eda8-6009-4621-9a4f-404b7e0f2133">

##### 2、配置要素信息
<img width="1220" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/47f6e38c-7914-4e99-ab17-89319a3c64eb">

##### 3、配置产品信息
<img width="1223" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/9cf717a1-be77-42b9-8138-02cd0ddfa71b">

##### 4、配置资方信息
<img width="1222" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/73b098ed-ad76-4635-8b33-742c215c8b77">

##### 5、配置担保方信息

<img width="1219" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/2fad9ac0-54a3-4d85-91bf-74b2fd7a0bbe">

##### 6、定价管理
######      6.1 产品定价
<img width="1219" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/38832e95-ff98-4606-8745-d6c60e6f9827">

######      6.2 资方定价   
<img width="1220" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/27083bc1-b6eb-4c0d-8d48-45ac15fd5d20">

##### 7、配置费项
<img width="1221" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/c01a14cb-fa7e-438e-aa25-1e0b26564f38">

##### 8、渠道关系管理
<img width="1218" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/52350642-30a1-4199-bbe9-b0a2a50c305c">

##### 9、信托计划配置
<img width="1216" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/bb0a8f68-5fe5-49d3-a3da-b6316b0aa231">

##### 10、资方关系配置
<img width="1223" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/8a62bb0f-0d5b-49a3-80d2-e775dbcfd6ae">

#### 三，表关系
##### 产品关系
![pec-产品关系 产品关系 -2023425173410](https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/95b3fc36-41f4-483b-a7d0-d3808d119511)

##### 资方关系
![pec-资方关系 资方关系 -2023425173410](https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/98bb0b4b-3fab-4fe7-8dce-fc4e429d02e8)

#### 四，使用场景
##### 1、贷前试算
调PEC根据用户等级、标签、借款期次、资方编码、渠道、还款方式等查询合适的产品定价，再通过定价结果调用 FCC试算进行算费。
<img width="1220" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/b4b77037-d678-4e2b-a8b1-915b49f39450">

##### 2、资管路由配置
资方业务规则配置根据产品代码查询支持的产品期次
<img width="1191" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/d473b071-9466-4690-bc11-3166cc55f1e1">

##### 3、贷中进件创建标的
查询产品定价镜像、资方还款公式、清分公式等信息落入标的系统 BEC标的表。业务发生时刻落库的数据，使用的是在PEC中当时的镜像编号，可用于回溯。
<img width="1221" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/77c6f999-39d7-4d92-b0a8-936d6843af67">

##### 4、贷后提前结清限制
查询要素中的提前结清方式，提前结清手机尾号开放范围，订单开放范围
<img width="1221" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/6d5f955c-46d6-433c-812f-1cab94875381">
<img width="955" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/ac22992f-a145-416d-9777-187085a7ad5b">

##### 5、OMC运营管理

###### 5.1 初始化定价
<img width="944" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/d9a6e01f-9ac5-4be8-8840-f013e8d096f0">

###### 5.2 变价
<img width="947" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/87b02e8d-da3b-4c14-9dca-433165d1781d">

##### 6、FCC计算
通过定价镜像编号查询费项，要素(如:产品年天数,分期周期单位,分期周期数值,多资方宽限期,提前结清方式)进行运算
PEC要素：
<img width="957" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/a6896bfd-9e86-4cfb-85b3-20542cb6a9f6">

FCC部分代码：
<img width="955" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/038f371b-f711-4c2e-a509-15efddaba72d">

生成债务债权宽限时期，**宽限期只是对客不展示逾期费项，而不是不计算逾期费项，**逾期费项也会配置宽限天数；费项介绍可到[查询费项](#3、查询费项)
<img width="957" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/3a63ec0e-9b4b-465e-8594-d83d4d5f4cc5">

##### 7、LSC-JOB批扣
查询要素逾期持续批扣期数，逾期账龄小于逾期持续批扣期数进行批扣
<img width="955" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/8c9ac3a6-68dd-4994-8494-a129b6caa6de">

#### 五，重要接口
##### 1、查询合适的产品定价
​      com.gomefinance.consumerfinance.pec.facade.ProductFacade#querySuitableProductPricing
``` mysql
一，查询资方关系，是否存在父子资方：
SELECT *
FROM t_pec_capital_relation
WHERE f_capital_code = 'C5024'
limit 1;

二，查询活动关系：
SELECT *
FROM t_pec_conf_relation
WHERE f_status = 0
AND f_type = 2
AND f_code = 'HD20200925F24'
limit 1;

三，查询渠道关系，定价初始化时会适配渠道：
SELECT *
FROM t_pec_conf_relation
WHERE f_status = 0
AND f_type = 1
AND f_code = '10000000'
limit 1;

四，查询产品定价:
select *
from t_pec_product_pricing
WHERE f_product_code = '5551'
  AND f_total_stage = 6
  AND f_rank_level = 'A'
  AND f_repayment_way = 1
  AND FIND_IN_SET('10000000', f_channel_type) > 0
  AND f_product_price_status = 0
  AND (f_capital_code = 'C5024' or f_capital_code = "")
  AND (FIND_IN_SET('C0001', f_consumer_label) > 0 OR f_consumer_label = '')
  AND f_activity_code = ''
ORDER BY f_capital_code DESC,
         f_consumer_label DESC,
         f_activity_code ASC
LIMIT 1;
```

###### 常见的问题
​一，进件到FCC生成债务债权时报空指针异常，如：南京银行只有A等级的定价，但进件时测试环境没改用户等级，还是B等级；虽然PEC没有异常，返回的定价是兜的定价保证试算不出问题，但进件就会报错；
<img width="958" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/764debd7-c0bd-4443-9eee-080250c58bb9"> 
​       
二，期次对应不上，如：新网银行进件依赖资方的还款计划，测试环境挡板配置的是9期，但进件是12期；传给PEC的参数也是12期A等级；
<img width="945" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/b85952aa-8b46-47b5-a716-18bcb55ecf38">

##### 2、查询合适的资方定价

​     com.gomefinance.consumerfinance.pec.facade.CapitalFacade#querySuitableCapitalPricing

```mysql
一，查询资方关系，是否存在父子资方：
SELECT *
FROM t_pec_capital_relation
WHERE f_capital_code = 'C5024'
limit 1;
二，查询资方定价
SELECT *
FROM t_pec_capital_pricing
WHERE f_capital_code = 'C5024'
  and ( -- 资方定价相同，不区分档次，使用f_match_type = 0
        -- 资方定价按产品或档次不相同时，使用f_match_type >0
        -- 1，使用要求    
        -- 1.1，资方定价使用 f_match_type = 0 f_match_target_no=空，代偿方定价使用 f_match_type = 4
        -- 1.2，资方定价使用 f_match_type = 2 f_match_target_no=产品code，代偿方定价使用 f_match_type = 5
        -- 1.3，资方定价使用 f_match_type = 3 f_match_target_no=产品定价编号，代偿方定价使用 f_match_type = 3 或 f_match_type = 4
        -- 2，使用说明
        -- 2.1 f_match_type = 0 对应所有档次
        f_match_type = 0
        -- 2.2 f_match_type = 1 对应业务线code
        OR (f_match_type = 1 AND f_match_target_no = 'MJ') 
        -- 2.3 f_match_type = 2 对应产品code
        OR (f_match_type = 2 AND f_match_target_no = '5551') 
        -- 2.4 f_match_type = 3 对应档次的产品定价编号
        OR (f_match_type = 3 AND f_match_target_no = '0550a03dcb5645c78518493c2dbbcec4')
        -- 2.5 f_match_type = 4 对应资方code
        OR (f_match_type = 4 AND f_match_target_no = 'C5024')
        -- 2.6 f_match_type = 5 对应产品code+资方code
        OR (f_match_type = 5 AND f_match_target_no = CONCAT('5551', '+', 'C5024')) 
      )
ORDER BY f_capital_code desc, f_match_type desc, f_year_rate ASC
LIMIT 0,1;
```

##### 3、查询费项

​       产品费项
​       com.gomefinance.consumerfinance.pec.facade.ProductFacade#queryProductPricingFee

```mysql
select *
from t_pec_pricing_fee
where f_pricing_type = 1
  AND f_pricing_mirror_no = 'e0b16d04c70542eb9d24f126a9dfa5f7';
```

​       资方费项 
​       com.gomefinance.consumerfinance.pec.facade.CapitalFacade#queryCapitalPricingByPricingNo

```mysql
select *
from t_pec_pricing_fee
where f_pricing_type = 2
  AND f_pricing_mirror_no = '0d53d05215a34011848ec0e0dc401b69';
```

###### 常见问题

​      逾期费项宽限天数和要素配置的宽限期天数分管不同的功能；逾期费项配置几天就几天后开始计算，过了宽限天数逾期几天就计算几天。

##### 4、查询提前结清利率(适用于4%千一切换场景)

​      com.gomefinance.consumerfinance.pec.facade.ProductFacade#queryPreSettleRate
<img width="953" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/cadd9699-ab08-4211-875b-4443c290f631">

###### 第一版：按资方维度
​    单一资方所有产品，共享提前结清百4时，配置**CAPITAL_PRE_SETTLE_RATE_FEE_CODE** 要素

​    要素值举例1：SERVICE_FEE（服务费）

​    要素值举例2： （利息）
<img width="955" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/4e718dce-b35d-4447-97b7-46c9d736513d">

###### 第二版：按资方+产品+费项维度

   单一资方5551产品支持百4,  6901 产品不支持百4情况时，配置 **CAPITAL_PRODUCT_PRE_SETTLE_RATE** 要素
   要素值：[{"preSettleRate":{"name":"5551","value":"SERVICE_FEE"}}]
<img width="943" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/c81815a7-d411-4379-9ce2-229b3963ab9b">

###### 第三版：按资方+产品+费项维度 默认定价由千一换成了0.065%

​    单一资方5551产品支持0.065%(即:以前的千一换成了0.065%)配置 **CAPITAL_PRODUCT_PRE_SETTLE_RATE** 要素
​    要素值：[{"defaultPreSettleRate":{"name":"5551","value":"SERVICE_FEE"}}]
<img width="959" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/b3f072ad-4965-4f00-981a-c31978e7378b">

###### 第四版：按资方+产品+等级

​    单一资方5551产品千一和百四配置 **CAPITAL_MILLI_AND_FOURPERCENT_PRE_SETTLE_RATE** 要素
​    要素值：[{"milliPreSettleRate":[{"name":"5551-A","value":"SERVICE_FEE"}]},{"fourPercentPreSettleRate":[{"name":"5551-B,C,D","value":"SERVICE_FEE_TWO"}]}]
<img width="1054" alt="image" src="https://github.com/kunzhao3/fuzzy-pancake/assets/25682938/3e50c8cf-e234-4f3c-a4f2-bf2f25802e9c">

###### 常见问题：

​      一， **CAPITAL_PRE_SETTLE_RATE_FEE_CODE**(按资方维度)和**CAPITAL_PRODUCT_PRE_SETTLE_RATE**(按资方+产品+费项维度)**不能共存**只能按场景配置一个；
​      二，  **CAPITAL_PRE_SETTLE_RATE_FEE_CODE**(按资方维度)和**CAPITAL_PRODUCT_PRE_SETTLE_RATE**(按资方+产品+费项维度)
​              都配置，优先**CAPITAL_PRODUCT_PRE_SETTLE_RATE**(按资方+产品维度+费项)
​      三，**CAPITAL_PRODUCT_PRE_SETTLE_RATE**(按资方+产品维度+费项)，**相同产品，相同费项**
​              如果一个资方但不同产品，5551要默认0.065%，5551还要支持4%，
​              配置了 [{"preSettleRate":{"name":"5551","value":"SERVICE_FEE"}}]
​              也配置了 [{"defaultPreSettleRate":{"name":"5551","value":"SERVICE_FEE"}}]
​              即：

```json
      [
        {"defaultPreSettleRate":{"name":"5551","value":"SERVICE_FEE"}},
        {"preSettleRate":{"name":"5551","value":"SERVICE_FEE"}}
      ]
```
​              优先 [{"defaultPreSettleRate":{"name":"5551","value":"SERVICE_FEE"}}]
​     四，如果一个资方但不同产品，5551要默认0.065%，6901支持4%，**不同产品相同费项**，那配置就可以是这样
​              **CAPITAL_PRODUCT_PRE_SETTLE_RATE**(按资方+产品维度+费项)

```json
      [
        {"defaultPreSettleRate":{"name":"5551","value":"SERVICE_FEE"}},
        {"preSettleRate":{"name":"6901","value":"SERVICE_FEE"}}
      ]
```

​     五，如果一个资方不同产品，5551要默认0.065%，6901支持4%，**不同产品不同费项，费项里都没利息**，如：5551是担保费，6901是服务费
​           **CAPITAL_PRODUCT_PRE_SETTLE_RATE**(按资方+产品维度+费项)

```json
       [
         {"defaultPreSettleRate":{"name":"5551","value":"GUARANTEE_FEE"}},
         {"preSettleRate":{"name":"6901","value":"SERVICE_FEE"}}
       ]
```

