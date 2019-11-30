# 融租易（个人ETC） - 便携机 - 对外接口文档

诚泰科技

[TOC]

*基础路径* : /openjoin/etc

*请求头内容*:
	
**除register、sendSms的注册类型，接口外，其他的接口的请求 head 中都必须传入 User-Identity="123456",这个值在调用register接口时会返回；**

```
接口请求的Content-Type为：application/json

接口响应的内容格式为：
{
    "code":200,
    "message":"",
    "result":object,
    "timestamp": 1558419633567 
}
```




## 1、账户接口

### 1.1、**实名注册接口**

 * 接口地址 : /register
 * 接口说明 : 实名注册
 * 请求方式 : POST
 * 请求参数 :  
 
| 名称 | 类型 | 说明 | 是否必填 |   
|:---:|:---:|:---:|:---:| 
| name | String | 姓名 | 是 |  
| gender | String | 性别(男、女) | 是 |  
| nation | String | 民族(汉、回等) | 否 |  
| age | String | 年龄 |否 |    
| birthdate | String | 出生日期(格式：yyyy-MM-dd)| 是 |     
| address | String | 户籍地址 | 否 |    
| idNo | String | 身份证号 | 是 |     
| issuedby | String | 签发机关 | 否 |    
| startDate | String | 有效期开始时间(格式：yyyy-MM-dd) | 是 |     
| validthru | String | 有效期止(格式：yyyy-MM-dd) | 是 |    
| phone | String | 手机号 | 是 |     
| smsCode | String | 手机验证码 | 是 |     
| bankEMID | String | 银行员工编号 | 否 |    
| qlEMID | String | 齐鲁员工编号 | 否 |    
| channel | String | 进件渠道(固定值：XXXXX) | 是 |   
 * 请求参数示例 :  
```
json
{
	"name": "吕刘浩",
	"gender": "男",
	"nation": "汉",
	"age": null,
	"birthdate": "1989-11-09",
	"address": "上海市地球村民族路XX号",
	"idNo": "411xxxxx********",
	"issuedby": "XXX公安局",
	"startDate": "2015-12-31",
	"validthru": "2035-12-31",
	"phone": "1851652XXXX",
	"smsCode":"123456",
	"bankEMID":"123456",
	"qlEMID":"123",
	"channel": "XXXXXX"
}
```
 * 响应参数 :  

| 名称 | 类型 | 说明 | 是否必填 |    
|:---:|:---:|:---:|:---:|
| result | String | 用户ID | 是 |     

 * 响应参数示例：

```
{
	"code": 200,
	"message": "success",
	"result":  "123456",
	"timestamp": 1558419633567
}
```
## 2、产品相关

### 2.1、**获取个人ETC产品介绍**

 * 接口地址 : /product/getProductIntroduction
 * 接口说明 : 查看etc产品介绍信息
 * 请求方式 : GET
 * 请求参数 : 无

 * 返回结果数据 :  

| 名称 | 类型 | 说明 |
|:---:|:---:|:---:|
| className                       | String  | 分类名称 |
| claimIntroduction               | String  | 摘要介绍 |
| detailIntroduction              | String  | 详细介绍 |
| classCode                       | String  | 分类编码 |
| sort                            | Integer | 排序	  |
| childrens                       | Object  | 子集	  |
| childrens.className             | String  | 分类名称 |
| childrens.classCode             | String  | 分类编码 |
| childrens.claimIntroduction     | String  | 摘要介绍 |
| childrens.detailIntroduction    | String  | 详细介绍 |
| childrens.sort                  | Integer | 排序  	  |
| childrens.parentId              | Long    | 上级ID	  |
| childrens.productId             | Long    | 产品ID	  |

 * 响应结果示例：

```
{
	"code": 200,
	"message": "",
	"result": [
		{
			"checked": false,
			"childrens": [],
			"claimIntroduction": "每日结算前一天通行费",
			"classCode": "etc_personal_margin_single_week",
			"className": "通行费-次日结",
			"customerId": 0,
			"detailIntroduction": "每日结算前一天通行费",
			"id": "3",
			"parentId": "1",
			"processIId": "",
			"productId": "16",
			"remark": "",
			"sort": 1,
			"value": "",
			"vehicleCashDeposit": 0,
			"vehicleId": ""
		},
		{
			"checked": false,
			"childrens": [],
			"claimIntroduction": "次周一出账单,周二扣款,每周10元/车",
			"classCode": "etc_personal_single_week",
			"className": "通行费-单周结",
			"customerId": 0,
			"detailIntroduction": "次周一出账单,周二扣款,每周10元/车",
			"id": "6",
			"parentId": "2",
			"processIId": "",
			"productId": "13",
			"remark": "",
			"sort": 1,
			"value": "",
			"vehicleCashDeposit": 0,
			"vehicleId": ""
		},
		{
			"checked": false,
			"childrens": [],
			"claimIntroduction": "双周后 周一出账单,周二扣款,每双周35元/车",
			"classCode": "etc_personal_double_week",
			"className": "通行费-双周结",
			"customerId": 0,
			"detailIntroduction": "每周15元/车, 周二扣款,每周35元/车",
			"id": "7",
			"parentId": "2",
			"processIId": "",
			"productId": "14",
			"remark": "",
			"sort": 2,
			"value": "",
			"vehicleCashDeposit": 0,
			"vehicleId": ""
		},
		{
			"checked": false,
			"childrens": [],
			"claimIntroduction": "次月1号出账单,5号扣款,通行费的1%",
			"classCode": "etc_personal_month",
			"className": "通行费-单月结",
			"customerId": 0,
			"detailIntroduction": "次月1号出账单,5号扣款,通行费的1%",
			"id": "8",
			"parentId": "2",
			"processIId": "",
			"productId": "15",
			"remark": "",
			"sort": 3,
			"value": "",
			"vehicleCashDeposit": 0,
			"vehicleId": ""
		}
	],
	"timestamp": "1571723636589"
}
```

### 2.2、**选择产品之后创建意向信息**

 * 接口地址 : /product/createProductIntention
 * 接口说明 : 创建申请意向信息
 * 请求方式 : POST
 * 请求参数 : 
 
 * 请求参数 ：
 
| 名称 | 类型 | 说明 | 是否必填 |
|:---:|:---:|:---:|:---:|
| productId | Long | 产品ID | 是|

请求示例 :  

```
{
    "productId":13
}
```

 * 返回结果数据 :  

| 名称 | 类型 | 说明 |
|:---:|:---:|:---:|
| result | Long | 客户意向ID |


响应结果示例：

```
{
    "code": 200,
    "message": "success",
    "result": 257,
    "timestamp": 1561981319515
}
``` 
### 2.3、**查询客户的意向信息**

 * 接口地址 : /product/getIndividualEtcIntention
 * 接口说明 : 获取用户的意向信息，回显之前保存的信息
 * 请求方式 : GET
 * 请求参数 : 
  
| 名称 | 类型 | 说明 | 是否必填 |    
|:---:|:---:|:---:|:---:|   
| intentionId | Long | 意向客户ID | 是 |  
请求示例 :  

```
{
    "intentionId": "307"
}
```

 * 返回结果数据 :  

| 名称 | 类型 | 说明 |
|:---:|:---:|:---:|
| intentionId         | Long   | 意向客户ID |
| customerCode        | String | 意向客户编号 |
| productId           | Long   | 产品ID |
| vehicleStatus       | String | 车辆状态 (默认“X0”)|
| bailAmount          | Bigdecimal | 保证金金额（默认0） |  
| userAuthStatus      | Long   | 身份认证状态( 0 [未认证] 1 [已认证]) |
| maritalStatus       | String | 婚姻状态(1001[已婚已育] 1002[已婚未育] 1003[未婚] 1004[离异] 1005[单身] 1006[无法核实] 1007[丧偶] 1008[已婚]) |
| mailingAddressId    | Long   | 邮寄地址ID|
| bankAccount         | Object | 银行卡信息 |
| bankAccount.accountNum | String | 卡号 |
| contacts            | Object | 紧急联系人信息|
| contacts.name       | String | 联系人名字|
| contacts.order      | String | 联系人序号（第几个联系人）|
| contacts.province   | String | 省 |
| contacts.city       | String | 市 |
| contacts.county     | String | 区 |
| contacts.relationType | String |关系（2001[父母]2002[兄弟]2003[姐妹]2004[子女]2005[亲属]2006[朋友]2007[夫妻]）|
| userAddress         | Object | 邮寄地址信息|
| userAddress.province   | String | 省 |
| userAddress.city       | String | 市 |
| userAddress.county     | String | 区 |


响应结果示例：

```
{
    "code": 200,
    "message": "success",
    "result": {
        "accessoryStatus": null,
        "bankAccount": {
            "accountNum": "1233141234",
            "bankCode": "12341234123",
            "bankType": "中国银行上海分行",
            "customerCode": "CT2019070118023434555344",
            "holderCardId": "510602197801157023",
            "holderCardType": "1",
            "holderName": "大白兔",
            "holderPhone": "17091260912",
            "id": 1,
            "intentionId": 257,
            "openingBank": "中国建设银行",
        },
        "contacts": [
            {
                "cardDueDate": null,
                "cardId": null,
                "cardType": null,
                "city": "石家庄市",
                "contactNo": "18317065688",
                "county": "长安区",
                "customerCode": "CT2019070118023434555344",
                "gender": null,
                "homeAddr": "华夏东路",
                "id": 48,
                "inputChannel": 1,
                "name": "杨可修改",
                "order": 0,
                "province": "河北省",
                "relationType": "2004",
                "relationTypeName": null,
                "telephone": null
            },
            {
                "cardDueDate": null,
                "cardId": null,
                "cardType": null,
                "city": "石家庄市",
                "contactNo": "18317065616",
                "county": "长安区",
                "customerCode": "CT2019070118023434555344",
                "delFlag": false,
                "gender": null,
                "homeAddr": "华夏东路2222222",
                "id": 49,
                "inputChannel": 1,
                "name": "宋某人",
                "order": 1,
                "province": "河北省",
                "relationType": "2007",
                "relationTypeName": null,
                "telephone": null
            }
        ],
        "customerCode": "CT2019070118023434555344",
        "intentionId": 257,
        "mailingAddressId": 1,
        "maritalStatus": "1001",
        "productId": 13,
        "userAddress": {
            "city": "上海",
            "contactName": "zs",
            "contactNo": "19000010002",
            "county": "浦东新区",
            "detailAddr": "世纪大道1号101室",
            "id": 1,
            "province": "上海",
            "remark": null,
            "telephone": "70020002",
            "userId": 0
        },
        "userAuthStatus": 1,
        "vehicleStatus": "X0"
    },
    "timestamp": 1562071898943
}
``` 
### 2.4、**更新用户意向内容**

 * 接口地址 : /product/saveProductIntention
 * 接口说明 : 更新意向内容，在婚姻状态、邮寄地址、开票手机号变更时调用
 * 请求方式 : POST
 * 请求参数 : 
  
| 名称 | 类型 | 说明 | 是否必填 |    
|:---:|:---:|:---:|:---:|   
| intentionId        | Long   | 意向客户ID | 是 |    
| productId          | Long   | 产品ID | 是 |   
| mailingAddressId   | Long   | 邮寄地址ID| 否 |   
| maritalStatus      | String | 婚姻状态(1001[已婚已育] 1002[已婚未育] 1003[未婚] 1004[离异] 1005[单身] 1006[无法核实] 1007[丧偶] 1008[已婚]) | 否 |   
| invoicePhoneNumber   | String   | 开票手机号| 否 | 

 
请求示例 :  

```
json
{
	"intentionId":"257",
	"maritalStatus":"1001",
	"productId":"13",
	"mailingAddressId":"1",
    "invoicePhoneNumber":"18516527295"
}
```

 * 返回结果数据 :  

| 名称 | 类型 | 说明 |
|:---:|:---:|:---:|
| result  | Long   | 意向客户ID |



响应结果示例：

```
{
    "code": 200,
    "message": "success",
    "result": 257,
    "timestamp": 1562071466146
}
``` 



## 3、车辆相关

### 3.1、**已绑定车辆查询**

 * 接口地址 : /vehicle/getVehicleList
 * 接口说明 : 已绑定车辆的明细信息查询
 * 请求方式 : GET
 * 请求参数 :  

| 名称 | 类型 | 说明 | 是否必填 |
|:---:|:---:|:---:|:---:|    
| phone | String | 用户手机号 | 是|
| code | String | 客户编号 | 是|

 * 返回结果数据 :  

| 名称 | 类型 | 说明 |
|:---:|:---:|:---:|
| productId |String | 产品id | 是  |  
| plateNo |String | 车牌号 | 是   |
| headColor |String | 车辆颜色 | 是   |
| plateColor |String | 车牌颜色 | 是   |
| vin |String | 车架号 | 是   |
| vehicleType |String | 车辆类型 | 是 |  
| holdType |String | 拥有类型 | 否   |
| brand |String | 车辆品牌 | 否   |
| userProperty |String | 使用性质 | 是   |
| engineNo |String | 发动机号 | 是   |
| registDate |String | 注册日期 | 否   |
| certificationDate |String | 发证日期 | 是   |
| certificationAuthority |String | 发证机关 | 否   |
| drivingLicenseFront |String | 行驶证正面图片地址(调用图片上传返回) | 是  |
| drivingLicenseReverse |String | 行驶证反面图片地址(调用图片上传返回) | 是  |
| vehicleHeadUrl |String | 车头图片地址(调用图片上传返回) | 是  |
| loadNo |String | 核载人数 | 否   |
| totalMass |String | 总质量 | 否   |
| curbMass |String | 整备质量 | 否   |
| loadMass |String | 核载质量 | 是   |
| extendSize |String | 外扩尺寸 | 否   |
| tractionMass |String | 牵引质量 | 否   |
| fileNumber |String | 档案编号 | 否   |
| medicalRecord |String | 体检记录 | 否   |
| wheelNumber |String | 车轮数 | 否   |
| axleNumber |String | 车轴数 | 否   |
| axleBase |String | 轴距 | 否   |
| checkEnd |String | 检查截至日期 | 否   |
| isIllegal | String | 是否违章 0 否 1 是 | 否   |
| model |String | 车型(1-一型客车，2-二型客车，3-三型客车，4-四型客车，11-一型货车，12-二型货车，13-三型货车，14-四型货车，15-五型货车) | 是  | 
| vehicleOriginType |String | 车辆录入种类 1：个人ETC录入车辆 2企业ETC录入车辆 | 否  | 
| ownerAddress |String | 车辆所有人地址 | 否   |
| ownerName |String | 车辆所有人姓名 | 否   |
| ownerCardType |String | 机动车所有人证件类型（101-身份证含临时身份证 102-护照 103-港澳居民来往内地通行证 104-台湾居民来往大陆通行证 105-军官证 106-武警警察身份证	201-统一社会信用代码证书 202-组织机构代码证 203-营业执照204-事业单位法人证书 205-社会团体法人登记证书 206-律师事物所执业许可证） | 否  | 
| ownerIdentityCard |String | 机动车所有人证件号 | 否   |
| ownerContactPhone |String | 机动车所有人联系人电话 | 否   |
| outsideDimensionsL |String | 外扩尺寸长 | 否   |
| outsideDimensionsW |String | 外扩尺寸宽 | 否   |
| outsideDimensionsH |String | 外扩尺寸高 | 否   |
| vehicleCashDeposit |String | 车辆保证金 | 否   |
| remark |String | 备注 | 否   |


 * 响应结果示例：

```
{
  "code": 200,
  "message": "success",
  "result": [
    {
      "axleBase": null,
      "axleNumber": "4",
      "batchNo": "20190730102258",
      "brand": null,
      "cashDepositCommit": "0",
      "certificationAuthority": null,
      "certificationDate": null,
      "checkEndDate": null,
      "checked": false,
      "checkedStatus": "0",
      "code": "CTCLY2NYU2YP",
      "commitStatus": "2",
      "curbMass": null,
      "customerId": null,
      "drivingLicenseFront": "https://testfile.lianrongbao.cn/public/images/20190730/20190730102233_646.jpg",
      "drivingLicenseReverse": "https://testfile.lianrongbao.cn/public/images/20190730/20190730102224_394.jpg",
      "engineNo": null,
      "extendSize": null,
      "fileNumber": null,
      "headColor": "1",
      "holdType": null,
      "id": "52",
      "isDrivingLicense": null,
      "isIllegal": 0,
      "loadMass": "200",
      "loadNo": null,
      "medicalRecord": null,
      "model": "二型客车",
      "ocrId": "123",
      "outsideDimensionsH": null,
      "outsideDimensionsL": null,
      "outsideDimensionsW": null,
      "ownerAddress": "山东省邹平平县明集镇驻地",
      "ownerCardType": 101,
      "ownerContactPhone": null,
      "ownerIdentityCard": null,
      "ownerName": null,
      "plateColor": "2",
      "plateNo": "鲁M18350",
      "processIId": null,
      "productIId": null,
      "productId": "16",
      "registDate": null,
      "registrationStatus": null,
      "registrationUrl": "",
      "remark": null,
      "status": 0,
      "statusDesc": null,
      "totalMass": null,
      "tractionMass": null,
      "userId": null,
      "userProperty": "货运",
      "vehicleCashDeposit": 4000,
      "vehicleHeadStatus": null,
      "vehicleHeadUrl": ",https://testfile.lianrongbao.cn/public/images/20190730/20190730102254_922.jpg",
      "vehicleId": null,
      "vehicleType": "重型半挂牵引车",
      "vehicleVariety": null,
      "vin": "LFWRKUMF89AC27197",
      "wheelNumber": "14"
    }
  ],
  "timestamp": 1562047777093
}
``` 

### 3.2、**保存车辆信息**

 * 接口地址 : /vehicle/saveVehicle
 * 接口说明 : 对当前账户下添加车辆，如果传入ID参数则进行修改
 * 请求方式 : POST
 * 备注：需要校验车辆是否被绑定过。是否已关联产品。是否超过数量限制
 * 请求参数 : 

| 名称 | 类型 | 说明 | 是否必填 |
|:---:|:---:|:---:|:---:|    
| productId |String | 产品id | 是  |  
| plateNo |String | 车牌号 | 是   |
| headColor |String | 车辆颜色 | 是   |
| plateColor |String | 车牌颜色 | 是   |
| vin |String | 车架号 | 是   |
| vehicleType |String | 车辆类型 | 是 |  
| holdType |String | 拥有类型 | 否   |
| brand |String | 车辆品牌 | 否   |
| userProperty |String | 使用性质 | 是   |
| engineNo |String | 发动机号 | 是   |
| registDate |String | 注册日期 | 否   |
| certificationDate |String | 发证日期 | 是   |
| certificationAuthority |String | 发证机关 | 否   |
| drivingLicenseFront |String | 行驶证正面图片地址(调用图片上传返回) | 是  |
| drivingLicenseReverse |String | 行驶证反面图片地址(调用图片上传返回) | 是  |
| vehicleHeadUrl |String | 车头图片地址(调用图片上传返回) | 是  |
| loadNo |String | 核载人数 | 否   |
| totalMass |String | 总质量 | 否   |
| curbMass |String | 整备质量 | 否   |
| loadMass |String | 核载质量 | 是   |
| extendSize |String | 外扩尺寸 | 否   |
| tractionMass |String | 牵引质量 | 否   |
| fileNumber |String | 档案编号 | 否   |
| medicalRecord |String | 体检记录 | 否   |
| wheelNumber |String | 车轮数 | 否   |
| axleNumber |String | 车轴数 | 否   |
| axleBase |String | 轴距 | 否   |
| checkEnd |String | 检查截至日期 | 否   |
| isIllegal | String | 是否违章 0 否 1 是 | 否   |
| model |String | 车型(1-一型客车，2-二型客车，3-三型客车，4-四型客车，11-一型货车，12-二型货车，13-三型货车，14-四型货车，15-五型货车) | 是  | 
| vehicleOriginType |String | 车辆录入种类 1：个人ETC录入车辆 2企业ETC录入车辆 | 否  | 
| ownerAddress |String | 车辆所有人地址 | 否   |
| ownerName |String | 车辆所有人姓名 | 否   |
| ownerCardType |String | 机动车所有人证件类型（101-身份证含临时身份证 102-护照 103-港澳居民来往内地通行证 104-台湾居民来往大陆通行证 105-军官证 106-武警警察身份证	201-统一社会信用代码证书 202-组织机构代码证 203-营业执照204-事业单位法人证书 205-社会团体法人登记证书 206-律师事物所执业许可证） | 否  | 
| ownerIdentityCard |String | 机动车所有人证件号 | 否   |
| ownerContactPhone |String | 机动车所有人联系人电话 | 否   |
| outsideDimensionsL |String | 外扩尺寸长 | 否   |
| outsideDimensionsW |String | 外扩尺寸宽 | 否   |
| outsideDimensionsH |String | 外扩尺寸高 | 否   |
| vehicleCashDeposit |String | 车辆保证金 | 否   |
| remark |String | 备注 | 否   |
| code | String | 客户编号(意向信息查询中获取) | 是|   

 * 请求示例 :  

```
{
      "axleBase": null,
      "axleNumber": "4",
      "batchNo": "20190730102258",
      "brand": null,
      "cashDepositCommit": "0",
      "certificationAuthority": null,
      "certificationDate": null,
      "checkEndDate": null,
      "checked": false,
      "checkedStatus": "0",
      "code": "CTCLY2NYU2YP",
      "commitStatus": "2",
      "createTime": "2019-07-30 10:22:59",
      "curbMass": null,
      "customerId": null,
      "drivingLicenseFront": "https://testfile.lianrongbao.cn/public/images/20190730/20190730102233_646.jpg",
      "drivingLicenseReverse": "https://testfile.lianrongbao.cn/public/images/20190730/20190730102224_394.jpg",
      "engineNo": null,
      "extendSize": null,
      "fileNumber": null,
      "headColor": "1",
      "holdType": null,
      "id": "52",
      "isDrivingLicense": null,
      "isIllegal": 0,
      "loadMass": "200",
      "loadNo": null,
      "medicalRecord": null,
      "model": "二型客车",
      "ocrId": "123",
      "outsideDimensionsH": null,
      "outsideDimensionsL": null,
      "outsideDimensionsW": null,
      "ownerAddress": "山东省邹平平县明集镇驻地",
      "ownerCardType": 101,
      "ownerContactPhone": null,
      "ownerIdentityCard": null,
      "ownerName": null,
      "plateColor": "2",
      "plateNo": "鲁M18350",
      "processIId": null,
      "productIId": null,
      "productId": "16",
      "registDate": null,
      "registrationStatus": null,
      "registrationUrl": "",
      "remark": null,
      "status": 0,
      "statusDesc": null,
      "totalMass": null,
      "tractionMass": null,
      "userId": null,
      "userProperty": "货运",
      "vehicleCashDeposit": 4000,
      "vehicleHeadStatus": null,
      "vehicleHeadUrl": ",https://testfile.lianrongbao.cn/public/images/20190730/20190730102254_922.jpg",
      "vehicleId": null,
      "vehicleType": "重型半挂牵引车",
      "vehicleVariety": null,
      "vin": "LFWRKUMF89AC27197",
      "wheelNumber": "14",
	  "userId"："123456",
	  "code":"CTCXXXXXXX"
}
```

 * 返回结果数据:

| 名称 | 类型 | 说明 |   
|:---:|:---:|:---:|
| vehicleId | String   | 车辆ID |    

 * 响应结果示例：

```
{
    "code": 200,
    "message": "success",
    "result": {
        "vehicleId": "123456",
    },
    "timestamp": 1562071898943
}
``` 

### 3.3、**车辆信息删除**

 * 接口地址 : /vehicle/removeVehicle
 * 接口说明 : 删除已添加的车辆信息
 * 请求方式 : POST
 * 备注：已绑定产品的不准删除、已申请通过的不准删除。
 * 请求参数 : 
  
| 名称 | 类型 | 说明 | 是否必填 |    
|:---:|:---:|:---:|:---:|    
| vehicleId  | String   | 车辆ID | 是 |    
 
 * 请求示例 :  

```
json
{
	"vehicleId":"257"
}
```

 * 返回结果数据 :  

| 名称 | 类型 | 说明 |   
|:---:|:---:|:---:|   
| result  | boolean   | 删除结果 |


 * 响应结果示例：

```
{
    "code": 200,
    "message": "success",
    "result": true,
    "timestamp": 1562071466146
}
``` 


## 4、支付相关

### 4.1、**支付方式查询**

 * 接口地址 : /pay/getPayWays
 * 接口说明 : 查询ETC产品对应的支持的支付方式列表
 * 请求方式 : GET
 * 请求参数 : 
  
| 名称 | 类型 | 说明 | 是否必填 |    
|:---:|:---:|:---:|:---:|
| productId | Long | ETC产品ID | 是 |  


 * 响应参数 : 
 
| 名称 | 类型 | 说明 |
|:---:|:---:|:---:|
| id | String | 支付方式ID |
| activity | String | 活动描述 |
| customerSourceChannel | String | 客户渠道 |
| description | String | 支付方式描述 |
| payWayClassCode | String | 支付方式分类编码(recommend:推荐；other：其他；) |
| payWayCode | String | 支付方式编码 |
| payWayIcon | String | 图标地址 |
| payWayName | String | 支付方式名称 |
| payWayTypeCode | String | 支付方式类型编码 |
| productId | String | 产品ID |

 * 返回结果示例：

```
{
	"code": 200,
	"message": "success",
	"result": {
		"other": [{
				"activity": null,
				"customerSourceChannel": null,
				"description": null,
				"id": "4",
				"payWayClassCode": "other",
				"payWayCode": "CITIC",
				"payWayIcon": "https://file.lianrongbao.cn/static/etc/personal/images/4.png",
				"payWayName": "中信银行",
				"payWayTypeCode": "unionPay",
				"productId": "13"
			},
			{
				"activity": null,
				"customerSourceChannel": null,
				"description": null,
				"id": "5",
				"payWayClassCode": "other",
				"payWayCode": "BOS",
				"payWayIcon": "https://file.lianrongbao.cn/static/etc/personal/images/3.png",
				"payWayName": "上海银行",
				"payWayTypeCode": "unionPay",
				"productId": "13"
			},
			{
				"activity": null,
				"customerSourceChannel": null,
				"description": null,
				"id": "6",
				"payWayClassCode": "other",
				"payWayCode": "CEB",
				"payWayIcon": "https://file.lianrongbao.cn/static/etc/personal/images/6.png",
				"payWayName": "光大银行",
				"payWayTypeCode": "unionPay",
				"productId": "13"
			},
			{
				"activity": null,
				"customerSourceChannel": null,
				"description": null,
				"id": "7",
				"payWayClassCode": "other",
				"payWayCode": "SPDB",
				"payWayIcon": "https://file.lianrongbao.cn/static/etc/personal/images/1.png",
				"payWayName": "浦发银行",
				"payWayTypeCode": "unionPay",
				"productId": "13"
			},
			{
				"activity": null,
				"customerSourceChannel": null,
				"description": null,
				"id": "8",
				"payWayClassCode": "other",
				"payWayCode": "CIB",
				"payWayIcon": "https://file.lianrongbao.cn/static/etc/personal/images/8.png",
				"payWayName": "兴业银行",
				"payWayTypeCode": "unionPay",
				"productId": "13"
			}
		],
		"recommend": [{
				"activity": "送10万元意外伤害险",
				"customerSourceChannel": null,
				"description": "本支付方式工商银行将为您免费提供一年期10万元保额意外伤害保险。只要绑定工行卡，并且鲁通卡制卡成功保险即可发放，次月1日生效。",
				"id": "1",
				"payWayClassCode": "recommend",
				"payWayCode": "ICBC_E_WALLET",
				"payWayIcon": "https://file.lianrongbao.cn/static/etc/personal/images/2.png",
				"payWayName": "工行信用卡+工行e钱包",
				"payWayTypeCode": "ICBC_eWallet",
				"productId": "13"
			},
			{
				"activity": null,
				"customerSourceChannel": null,
				"description": "支持建设银行借记卡(支持山东、湖北、河北、安徽、北京、云南、内蒙古、甘肃、广西、贵州借记卡)",
				"id": "2",
				"payWayClassCode": "recommend",
				"payWayCode": "CCB",
				"payWayIcon": "https://file.lianrongbao.cn/static/etc/personal/images/7.png",
				"payWayName": "中国建设银行",
				"payWayTypeCode": "CCB",
				"productId": "13"
			},
			{
				"activity": null,
				"customerSourceChannel": null,
				"description": null,
				"id": "3",
				"payWayClassCode": "recommend",
				"payWayCode": "ABC",
				"payWayIcon": "https://file.lianrongbao.cn/static/etc/personal/images/5.png",
				"payWayName": "中国农业银行",
				"payWayTypeCode": "ABC",
				"productId": "13"
			}
		]
	},
	"timestamp": "1571034191218"
}
```
### 4.2、**查询还款银行卡**

 * 接口地址 : /pay/getBindedBankInfo
 * 接口说明 : 查询意向客户的还款银行卡信息
 * 请求方式 : GET
 * 请求参数 : 
  
| 名称 | 类型 | 说明 | 是否必填 |    
|:---:|:---:|:---:|:---:|   
| intentionId | Long | 意向客户ID | 是 |  

 * 返回结果数据 :  

| 名称 | 类型 | 说明 |
|:---:|:---:|:---:|
| id         | Long   | 还款银行卡ID |
| intentionId         | String  | 意向客户ID |
| bankType            | String  | 所属银行 |
| bankCode            | String  | 银行行号 |    
| accountNum          | String  | 卡号|  
| openingBank         | String  | 开户行|  
| holderCardId        | String  | 持卡人证件ID| 
| holderCardType      | String  | 持卡人证件类型(1001[身份证] 1002[军人证] 1003[港澳居民来往内地通行证] 1004[台湾同胞来往内地通行证] 1005[外国人居留证] 1006[其他个人证件])| 
| holderName          | String  | 持卡人姓名|
| holderPhone         | String  | 持卡人手机号|  

响应结果示例：

```
{
    "code": 200,
    "message": "success",
    "result": [
        {
            "accountNum": "1233141234",
            "bankCode": "12341234123",
            "bankType": "中国银行上海分行",
            "customerCode": "CT2019070118023434555344",
            "holderCardId": "510602197801157023",
            "holderCardType": "1",
            "holderName": "大白兔",
            "holderPhone": "17091260912",
            "id": 1,
            "intentionId": 257,
            "openingBank": "中国建设银行",
            "remark": null
        }
    ],
    "timestamp": 1562072996350
}
``` 



### 4.3、**绑定银联银行卡**

 * 接口地址 : /pay/bindBankAccount
 * 接口说明 : 保存意向客户的还款银行卡信息
 * 请求方式 : POST
 * 请求参数 : 
  
| 名称 | 类型 | 说明 | 是否必填 |     
|:---:|:---:|:---:|:---:|
| intentionId | String | 意向ID | 是|  
| accountINum | String  | 银行卡号|是|  
| partner     | String  | 银行合作方(ICBC.工商银行，ABC.农业银行，CCB.建设银行，BOC.中国银行， PSBC.中国邮政储蓄银行，BOCOM.交通银行)|是|  
| cardId      | String  | 持卡人证件ID|是|    
| cardType    | String  | 持卡人证件类型(1001[身份证] 1002[军人证] 1003[港澳居民来往内地通行证] 1004[台湾同胞来往内地通行证] 1005[外国人居留证] 1006[其他个人证件])|是|    
| mobileNo    | String  | 银行预留手机号|是|     
| customerName| String  | 客户姓名|是|     
| smsCode     | String  | 短信验证码|是|   
| smsSendNo   | String  | 短信验证码编号|是|   

 
 * 请求示例 :  

```
json
{
	"intentionId":"123456",
    "accountINum": "1233141234",
    "partner": "CCB",
    "cardId": "510602197801157023",
    "cardType": "1001",
    "mobileNo": "18516521234",
    "customerName":"吕刘浩",
    "smsCode":"123456",
    "smsSendNo":"654312"
}
```

 * 返回结果数据 :  

| 名称 | 类型 | 说明 |      
|:---:|:---:|:---:|
| result  | Long   | 还款银行卡ID |


 * 响应结果示例：

```
{
    "code": 200,
    "message": "success",
    "result": 1,
    "timestamp": 1561983984855
}
```  

### 4.4、**查询二类户开户结果**

 * 接口地址 : /getOpenCardProgress
 * 接口说明 : 查询二类户开户结果(工行小额免密签约前提接口)
 * 请求方式 : POST
 * 备注：获取二类户的开户结果。
 * 请求参数 : 
  
| 名称 | 类型 | 说明 | 是否必填 |     
|:---:|:---:|:---:|:---:|
| applyId  | String  | 绑定银行卡接口返回的ID |是|     

 
 * 请求示例 :  

```
json
{
    "applyId": "1233141234"
}
```

 * 返回结果数据 :  

| 名称 | 类型 | 说明 |      
|:---:|:---:|:---:|
| result  | Long   | 二类户开户结果 |


 * 响应结果示例：

```
{
    "code": 200,
    "message": "success",
    "result": 1,
    "timestamp": 1561983984855
}
```  



### 4.5、**小额免密签约(工行)**

 * 接口地址 : /smallFreeSign
 * 接口说明 : 小额免密签约
 * 请求方式 : POST
 * 备注：先开通工行二类户、然后在开通二类户的小额免密支付
 * 请求参数 : 
  
| 名称 | 类型 | 说明 | 是否必填 |     
|:---:|:---:|:---:|:---:|
| id  | String  | 绑定银行卡接口返回的ID |是|     
| smsCode  | String  | 短信验证码|是|     

 
 * 请求示例 :  

```
json
{
    "id": "1233141234",
    "smsCode": "123465"
}
```

 * 返回结果数据 :  

| 名称 | 类型 | 说明 |   
|:---:|:---:|:---:|
| result  | Boolean   | 签约结果 |


 * 响应结果示例：

```
{
    "code": 200,
    "message": "success",
    "result": true,
    "timestamp": 1561983984855
}
```  

## 5、邮寄地址


### 5.1、**邮寄地址查询**

 * 接口地址 : /address/getAddressList
 * 接口说明 : 邮寄地址查询
 * 请求方式 : GET
 * 请求参数 : 无
 * 返回结果 :  

| 名称 | 类型 | 说明  |
|:---:|:---:|:---:|
|contactName|String|姓名 |  
|contactNo|String|联系电话(移动电话)   |
|telephone|String|固定电话   |
|province|String|省   |
|city|String|市   |
|county|String|县   |
|detailAddr|String|详细地址   |
|remark|String|备注   |
|id|Long|地址ID   |

 * 响应结果示例：

```
{
    "code": 200,
    "message": "success",
    "result": [
        {
            "city": "上海",
            "contactName": "zs",
            "contactNo": "19000010002",
            "county": "浦东新区",
            "detailAddr": "世纪大道1号101室",
            "id": 1,
            "province": "上海",
            "remark": null,
            "telephone": "70020002"
        }
    ],
    "timestamp": 1561711458466
}
```

### 5.2、**邮寄地址-保存**

 * 接口地址 : /address/save
 * 接口说明 : 邮寄地址-保存
 * 请求方式 : post
 * 请求参数 :  
 
| 名称 | 类型 | 说明 | 是否必填 |     
|:---:|:---:|:---:|:---:|  
|contactName|String|姓名| 是|     
|contactNo|String|联系电话(移动电话)| 是|        
|telephone|String|固定电话   | 否|     
|province|String|省    | 是|     
|city|String|市   | 是|     
|county|String|县   | 是|     
|detailAddr|String|详细地址   | 是|     
|remark|String|备注   | 否|     
|id|Long|地址ID(此值为空则新增、非空则修改)   | 否|     

 * 请求示例 :  
```
json
{
	"city": "上海",
	"contactName": "zs",
	"contactNo": "19000010002",
	"county": "浦东新区",
	"detailAddr": "世纪大道1号101室",
	"province": "上海",
	"telephone": "70020002",
}
```
 * 返回结果数据 :  

| 名称 | 类型 | 说明 |   
|:---:|:---:|:---:|
| result | Long | 地址ID |

 * 响应结果示例：

```
{
    "code": 200,
    "message": "success",
    "result": "1234",
    "timestamp": 1561711302833
}
```

### 5.3、**邮寄地址删除**

 * 接口地址 : /address/remove
 * 接口说明 : 删除已添加的邮寄地址
 * 请求方式 : POST
 * 请求参数 : 
  
| 名称 | 类型 | 说明 | 是否必填 |    
|:---:|:---:|:---:|:---:|    
| addressId  | String   | 地址ID | 是 |      
 
 * 请求示例 :  

```
json
{
	"addressId":"257"
}
```

 * 返回结果数据 :  

| 名称 | 类型 | 说明 |   
|:---:|:---:|:---:|   
| result  | boolean   | 删除结果 |


 * 响应结果示例：

```
{
    "code": 200,
    "message": "success",
    "result": true,
    "timestamp": 1562071466146
}
``` 
## 6、紧急联系人

### 6.1、**紧急联系人-添加**

 * 接口地址 : /contract/save
 * 接口说明 : 紧急联系人-添加【联系人添加之前必须先调用意向信息保存接口。保存婚姻状态】
 * 请求方式 : POST
 * 请求参数 :  
 
| 名称 | 类型 | 说明 | 是否必填 |    
|:---:|:---:|:---:|:---:|   
|customerCode | String | 客户编号 | 是|     
|relationType|String|关系类型:个人（2001.父母,2002.兄弟,2003.姐妹,2004.子女,2005.亲属,2006.朋友,2007.夫妻）   | 是| 
|name|String|联系人姓名   | 是|  
|contactNo|String|联系电话(移动电话)   | 是| 

* 请求示例 :  

```
{
    "customerCode":"CTXXXXXX",
	"name": "张三",
	"contactNo": "18516527456",
	"relationType": "2001"
}
```  

* 响应参数 :  
| 名称 | 类型 | 说明 | 是否必填 |    
|:---:|:---:|:---:|:---:|   
| result | String | 联系人ID | 是|      


 * 响应结果示例：   
    

```
{
    "code": 200,
    "message": "success",
    "result": "115566",
    "timestamp": 1561708333903
}
```

### 6.2、**紧急联系人-获取**

 * 接口地址 : /contact/getContacts
 * 接口说明 : 紧急联系人-获取全部
 * 请求方式 : GET
 * 请求参数 :  
 
| 名称 | 类型 | 说明 | 是否必填 |    
|:---:|:---:|:---:|:---:|   
| customerCode | String | 客户编号 | 是|    

 * 请求示例 :  
```
json
{
	"customerCode":"CTCXXXXXXX"
}
```

 * 返回结果数据 :  

| 名称 | 类型 | 说明 |
|:---:|:---:|:---:|
|relationType|String|关系类型:个人（2001.父母,2002.兄弟,2003.姐妹,2004.子女,2005.亲属,2006.朋友,2007.夫妻）|
|name|String|联系人姓名|
|contactNo|String|联系电话(移动电话)|
|order|Integer|紧急联系人顺序|
|relationTypeName|String|关系类型名称|
|id|Integer|ID|

 * 响应结果示例：

```
{
    "code": 200,
    "message": "success",
    "result": [
        {

            "id": 1,
            "name": "张三",
			"contactNo":"1851652XXXX",
            "order": 0,
            "relationType": "2001",
			"relationTypeName":"父母"
        },
        {
            "id": 2,
            "name": "李四",
			"contactNo":"1851652XXXX",
            "order": 1,
            "relationType": "2002",
			"relationTypeName":"兄弟"
        }
    ],
    "timestamp": 1561708954010
}
```

## 7、相关协议内容获取

### 7.1、**获取ETC合同模板**

 * 接口地址 : /getIndividualEtcContract
 * 接口说明 : 申请ETC产品--获取ETC合同模板，将模板信息返回
 * 请求方式 : GET
 * 请求参数 : 
  
| 名称 | 类型 | 说明 | 是否必填 |    
|:---:|:---:|:---:|:---:|   
| productId     | Long   | 产品ID | 是|

 * 请求示例 :  

```
http://xxx:9000/individualetc/getIndividualEtcContract?productId=13
```

 * 返回结果数据 :  

| 名称 | 类型 | 说明 |
|:---:|:---:|:---:|
| id            | Long   | 模板ID       |
| templateName  | String | 模板名称     |
| templateCode  | String | 模板编号     |
| templatePdfPath | String | PDF模板的路径 |

 * 响应结果示例：

```
{
    "code": 200,
    "message": "success",
    "result": [
        {
            "id": 1,
            "templateCode": "etc.person.credit.authorization",
            "templateName": "《个人征信授权协议书》",
            "templatePdfPath": "http://10.10.116.16:8081/static/etc/contract/template/etc_person_credit_authorization.pdf",
            "templateType": "1001"
        },
        {
            "id": 2,
            "templateCode": "etc.fee.withhold.agreement",
            "templateName": "《先行通ETC用户费用代扣服务协议（20190712）》",
            "templatePdfPath": "http://10.10.116.16:8081/static/etc/contract/template/etc_fee_withhold_agreement.pdf",
            "templateType": "1001"
        }
    ],
    "timestamp": 1563675720623
}
``` 


### 7.2、**申请ETC产品--生成ETC合同模板**
 
 * 接口地址 : /signIndividualEtcContract
 * 接口说明 : ETC合同签订
 * 请求方式 : POST
 * 请求参数 :  
  
| 名称 | 类型 | 说明 | 是否必填 |    
|:---:|:---:|:---:|:---:|   
| intentionId | String | 意向ID | 是|  
     
 * 请求示例 : 
  
 ```
 {
    "intentionId": "123456"
 }
 ```
 
 * 响应参数 :  
    
| 名称 | 类型 | 说明 |  
|:---:|:---:|:---:|
| id                  | Long   | 生成待签合同模板ID | 
| contractPath        | String | 合同模板的路径     |  
| templateName        | String | 合同模板名称       |    
     
- 响应参数示例：  
```
 {
     "code": 200,
     "message": "success",
     "result": [
         {
             "contractPath": "http://10.10.116.16:8081/public/files/20190721/20190721101319_774.pdf",
             "id": 25,
             "templateName": "《个人征信授权协议书》"
         },
         {
             "contractPath": "http://10.10.116.16:8081/public/files/20190721/20190721101321_637.pdf",
             "id": 26,
             "templateName": "《先行通ETC用户费用代扣服务协议（20190712）》",

         }
     ],
     "timestamp": 1563675206738
 }
```  

## 8、base64图片上传


 * 接口地址 : /uploadBase64
 * 接口说明 : 图片上传
 * 请求方式 : POST
 * 请求头类型： Content-Type=application/x-www-form-urlencoded
 * 请求地址示例：http://XXXXXX:10882/uploadBase64
 * 请求参数 : img
  
| 名称 | 类型 | 说明 | 是否必填 |    
|:---:|:---:|:---:|:---:|   
| img  | String  | 图片的base64格式   |是|

 * 返回结果数据 :  

| 名称 | 类型 | 说明 |
|:---:|:---:|:---:|
| message  | String   | 结果msg |
| path  | String   | 图片地址 |
| success  | String   | 上传是否成功 |


响应结果示例：

```
{
	"code": 200,
	"message": "success",
	"result": {
		"message": "上传成功",
		"path": "http://localhost:8081/public/images/20191101/20191101144535_471.png",
		"paths": [],
		"success": true
	},
	"timestamp": "1572590735546"
}
``` 


## 9、发送短信验证码

 * 接口地址 : /sendSms
 * 接口说明 : 发送短信验证码
 * 请求方式 : POST
 * 请求参数 : 
  
| 名称 | 类型 | 说明 | 是否必填 |    
|:---:|:---:|:---:|:---:|   
| accountINum  | String  | 银行卡号(绑定银行卡时发送验证码必传)   |否|
| mobileNo     | String  | 预留手机号 |是|     
| smsType      | String  | 验证码类型(REGISTER-注册，FREE_SIGN-工行小额免密支付，CCB_SMS-建行验证码，ICBC_SMS-工行验证码，ICBC_BANKII_SMS-工行二类户验证码，BOC_SMS-中国银行验证码，ABC_SMS-农行验证码，UNIONPAY_SMS-银联验证码) |是|   
| occupation     | String  | 职业(1.公务员 2.事业单位员工 3.公司员工 4.军人警察 5.工人 6.农民 7.管理人员 8.技术人员 9.私营业主 10.文体明星 11.自由职业者 12.学生 13.无职业) |否|     
| foreverFlag     | String  | 身份证是否长期有效(0-否，1-是) |否|     
| validityPeriod     | String  | 身份证失效日期(当foreverFlag为0时必输)yyyy-MM-dd |否|     
| signDate     | String  | 发证日期(yyyy-MM-dd) |否|     



 
请求示例 :  

```
json
{
	"accountINum": "6216261000000000018",
    "mobileNo": "15150511740",
	"smsType":"REGISTER",
    "occupation":"3",
    "foreverFlag":"1",
    "validityPeriod":"2030-12-31",
    "signDate":"2030-12-31"
}
```

 * 返回结果数据 :  

| 名称 | 类型 | 说明 |
|:---:|:---:|:---:|
| result  | String   | 短信ID(验证接口回传) |


响应结果示例：

```
{
    "code": 200,
    "message": "success",
    "result": "200",
    "timestamp": 1561983984855
}
``` 

## 10、工行二类户验证码验证

 * 接口地址 : /checkBankIISmsCode
 * 接口说明 : 工行二类户验证码验证
 * 请求方式 : POST
 * 请求参数 : 
  
| 名称 | 类型 | 说明 | 是否必填 |    
|:---:|:---:|:---:|:---:|   
|id     | String  | 短信发送接口返回的ID |是|     
|smsCode| String  | 短信验证码 |是|     
 
请求示例 :  

```
json
{
	"id": "123465",
	"smsCode":"123456"
}
```

 * 返回结果数据 :  

| 名称 | 类型 | 说明 |
|:---:|:---:|:---:|
| result  | boolean   | 验证成功与否 |


响应结果示例：

```
{
    "code": 200,
    "message": "success",
    "result": true,
    "timestamp": 1561983984855
}
``` 


## 11、申请ETC产品--提交

 * 接口地址 : /product/commitIndividualEtcIntention
 * 接口说明 : 提交申办产品
 * 请求方式 : POST
 * 请求参数 : 
  
| 名称 | 类型 | 说明 | 是否必填 |     
|:---:|:---:|:---:|:---:|   
| productId  | Long   | 产品ID | 是|   
| vehicleIds  | Array| 车辆IDS  | 是 |    
| intentionId  | Long| 意向信息ID  | 是 |    
 
请求示例 :  

```
json
{
	"intentionId": "123456",
	"productId": "13",
	"vehicleIds": [12, 13]
}
```

 * 返回结果数据 :  

| 名称 | 类型 | 说明 |
|:---:|:---:|:---:|
| result  | Long   | 申请ID |

 * 响应结果示例：

```
{
    "code": 200,
    "message": "success",
    "result": 257,
    "timestamp": 1562071466146
}
``` 

