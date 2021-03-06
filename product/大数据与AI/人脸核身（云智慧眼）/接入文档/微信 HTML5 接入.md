## 接入方式
### 原生 HTML5（浮层模式）
微信公众号浮层模式（可选择读数字、光线两种活体检测模式）是基于微信原生的体验，符合以下行业要求的客户可以 [申请使用](https://cloud.tencent.com/apply/p/shcgszvmppc)，审核通过后，即可对接浮层模式。
* 政务：政府机构或事业单位
* 金融：银行、保险
* 医疗：公立医疗机构
* 运营商：电信运营商
* 教育：公立教育机构
* 交通：航空、客运、网约车、交通卡、共享交通、轨道交通、租车
* 旅游：酒店
* 物流：快递、邮政、物流

使用流程：
![图片](https://main.qcloudimg.com/raw/db44c1a56a56f066fc6148fb9055dcfb.png)

### 通用 HTML5
微信公众号是使用人脸核身·云智慧眼产品的主要场景之一，人脸核身·云智慧眼产品为您提供用于微信公众号的 HTML5接口。
使用流程：
![图片](https://main.qcloudimg.com/raw/7a2cc25e7e5cbfc7bab3c815d7d53838.png)

## HTML5接入流程
![](https://main.qcloudimg.com/raw/e6140897733e231526aae3c5aae4a701.png)
1. 前置流程：
   - [创建 API 密钥](https://console.cloud.tencent.com/cam/capi)（SecretId 和 SecretKey）
   - 审批发起的核身请求
2. 客户后端调用实名核身鉴权 API DetectAuth 接口进行核身流程开启前鉴权，获取业务流水号（BizToken）与微信跳转 URL。
>!只有传入的 TerminalType 为`weixinh5`或`weixinh5native`时才会返回微信跳转URL。
拉取核身结果（GetDetectInfo）时需要提供客户后端 BizToken，请妥善保管。

3. 根据客户自身需求，按照不同的方式跳转进入人脸核身·云智慧眼流程。
   - 微信原生 HTML5模式（浮层模式）：客户后端将步骤2中得到的 URL 返回给客户前端，让前端跳转至此 URL 即可。
   - 微信公众号通用 HTML5模式：客户后端将步骤2中得到的 URL 返回给客户前端，让前端跳转至此 URL 即可。
4. 人脸核身完成后，流程会回调至客户侧（HTML5类型以回调地址形式返回），此时客户后端即可凭借回调中提供的 BizToken 调用获取实名核身结果信息 GetDetectInfo 接口去获取本次核身的详细信息。


