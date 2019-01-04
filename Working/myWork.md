## 12/10
+ 安装项目运行环境、查看源码、了解项目目录结构
## 12/11
+ 签名模块
	+ 步骤：输入身份证--采集现场照片--扫描照片回执--采集指纹信息--输入手机号码--选择认证方式--用户签名确认--业务支付

+ code
	+ Router -> householdPolicies
	+ add 在step3添加签名模块 

## 12/12
+ 上午 完善签名模块 ---> 过于冗余（否定）
+ 下午 修改原软键盘样式 
	+ 问题：修改样式后需在首页进行刷新才能显示出修改的样式（直接跳路由无效）
+ 晚上 大佬帮忙修改签名模块 and 软键盘重新修改 （自己修改被废弃）
	+ 签名模块改进：获取签名 getSignature 直接放到公共组件，create 时执行，添加校验和弹窗提示
	+ 减少 handleSubmit （由两个减为一个），直接判断 this.step == 1时 this.step++ 

## 12/13
+ 上午开会 政户接口数据错乱及界面未完善问题
+ 下午 添加事项（人社模块）声音；一体机出问题，重装系统；加班 00：30

## 12/14
+ 10：00上班
+ 添加人社模块声音
+ 申报居住登记 修改样式（使用新组件）
	- 资格校验 --> 完善资料 --> 上传材料 --> 核对信息
+ 下午 完成路由跳转

## 12/15
+ 上午 完善申报居住登记流程（参照 机动车驾驶证遗失补证）
+ 身份证丢失换领 http://localhost:8081/#/idCardDamagedReplace/ReadMe
+ 申报居住登记 


## 12/17
+ 修改证书查询（3个）全屏 loading （使用个税查询）,使用图片文字方案代替 loading
+ 修改公积金查询loading （3个） 

## 12/18
+ 完善公积金查询loading （3个） 换成新组件
+ 申报居住登记 更换新组件

## 12/19
+ 残疾人证注销 ( cancellation-disability-certificat ) cancellationDisabilityCertificat  （参照idCardDamagedReplace 居民身份证损坏换领）
+ 残疾认证迁出 （ emigration-disability-certificat ）emigrationDisabilityCertificat 

## 12/20
+ 残疾人证注销 残疾认证迁出 表单验证规则（界面部分）
+ 医保个账划拨查询（原：职工医保个账划拨查询 ）（数据请求部分）

## 12/21
+ 职工医保个账划拨查询(employeeMedicalInsuranceAccountAllocationQuery) 数据查询渲染 分页 根据日期查询（已废）

## 12/22
+ 修改 失业保险待遇月报到查询 （Unemployed_Insurance_Treatment_Month_Report_Query）
+ moyu

## 12/24
+ 职工医保个账划拨查询(employeeMedicalInsuranceAccountAllocationQuery) 查询结果排序&&分页（重写）
+ 单位参保缴费状态查询 （ theUnitGinsengPaysCostStateQuery  the unit ginseng pays cost state query）
+ 职工医保个账划拨查询 添加全部查询字段

## 12/25
+ 修改个税组件（2）personalIncomeTaxListPrinting  personalIncomeTaxPayTaxesProof （完成）
+ 修改公积金组件 （2） query/qu1 handprint/ha1 （未完成）
+ 解决 单位参保缴费状态查询 冲突  （两个人同时做 代码合并 ）
+  职工医保个账划拨查询 添加未查到数据显示无结果页面

## 12/26
+ 修改公积金组件 （2） query/qu1 handprint/ha1
+ 法律服务机构查询（ lawyerServiceOrganizationQuery ） 法律服务人员查询( lawyerServicePeopleQuery ) --> index && OrganizationListSearch

## 12/27 (12.27 9:00 - 12.28 3:30)
+ 法律服务人员查询( lawyerServicePeopleQuery ) 数据渲染
+ 法律服务机构查询（ lawyerServiceOrganizationQuery ）数据渲染
	(律师事务所 --> id:100
	律师协会 --> id:115 type:1
	公证处 --> id:110
	公正协会 --> id:1115 type:2
	基层法律服务所 --> id:109
	法律援助机构 --> id:115 type:3
	人民调解委员会 --> id:130
	仲裁委员会 --> id:140
	司法鉴定机构 --> id:200
	公共法律服务中心 --> id:170)
+ mock 无法使用 main.js 里的 process.env.NODE_ENV === 'development' && require('./mock')  被注释

##  12/28 (14:30)
+ 完善 法律服务人员查询( lawyerServicePeopleQuery ) 数据渲染
	执业律师（代表、顾问） --> id:100
	律师实习人员 --> id:xxx  （未知）
	公证员 --> id:110
	司法鉴定人 --> id:120
	人民调解员 --> id:130

## 12/29 
完善 法律服务人员查询( lawyerServicePeopleQuery )

## 12/30
完善 法律服务人员查询( lawyerServicePeopleQuery ) 完成详细页 部分参数未找到 表格部分待优化  

## 1/2
修复 法律服务人员查询( lawyerServicePeopleQuery ) 专兼职显示问题、表格数据无法对接上（写mock测试）、双重滚动条
实习律师接口、处罚处分对应字段未找到、搜索接口未完成、

## 1/3
法律服务人员查询( lawyerServicePeopleQuery ) 分页&&搜索
机构名称  传参
"pagerOrgPersonParam.legalServiceOccupation": "100",
"pagerOrgPersonParam.pageSize”:”10”,
"pagerOrgPersonParam.currentPage”:”1”
"pagerOrgPersonParam.opiorgname:”1”

委托律师服务 界面构建

## 1/4
委托律师服务 ( entrustingLawyerService )  完善页面
委托司法鉴定 ( entrustedJudicialExpertise ) 完善页面