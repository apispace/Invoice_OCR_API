# APISpace 介绍
**本 API 服务由 [APISpace（apispace.com）](https://www.apispace.com/?utm_source=github&utm_term=fapiaoocr) 提供。**

APISpace 是 Eolink 旗下专业的 API 开放与交易平台，为广大企业以及个人开发者提供多维度、全方位的API接口，覆盖短信验证、天气查询、快递物流、OCR文字识别等海量 API 服务，帮助用户快速获取数据，降低获取数据的成本和难度，提升开发效率。

APISpace 提供15种开发语言的代码示例，分别是：
- Java(OK HTTP)
- HTTP
- cURL
- 微信小程序
- PHP(pecl_http)、PHP(cURL)
- Python(http.client)、Python(Requests)
- JavaScript(Jquery AJAX)、JavaScript(XHR)
- NodeJS(Native)、NodeJS(Request)
- Ruby(Net:Http)
- Shell(Httpie)、Shell(cUrl)

# 增值税发票识别OCR
识别增值税普票、机动车发票、火车票、PDF电子票、行程单等类型发表的所有关键字段，包括发票基本信息、销售方及购买方信息、商品信息、价税信息等，其中五要素识别准确率超过99%。

**使用该产品前，您需要通过 [https://www.apispace.com/eolink/api/fapiao/introduction](https://www.apispace.com/eolink/api/fapiao/introduction?utm_source=github&utm_term=fapiaoocr) 申请API服务**

本文档末尾提供了 Python(Requests) 的调用代码示例，可以前往文档末尾查看。

更多代码示例：[https://www.apispace.com/eolink/api/fapiao/guidence/](https://www.apispace.com/eolink/api/fapiao/guidence/?utm_source=github&utm_term=fapiaoocr)

### 应用场景

1.  #### 财税报销

快速识别录入增值税普票或专票各字段信息，应用于企业税务核算及内部报销等场景，有效减少人工核算工作量，实现财税报销的自动化。

2.  #### 发票验真

智能识别发票代码、号码、开具金额、开票日期四个关键字段，以便快速接入税务机关发票查验平台进行真伪查验，有效降低人力成本，控制业务风险。

3.  #### 账单记录

对发票金额、开票日期等信息进行自动识别和录入，应用于理财记账场景，帮助用户快速录入账单信息，降低用户输入成本，提升使用体验。

### 图片示例

1.  拍摄图片的时候需要 正着拍摄，保持图片清晰，没有杂物，这样可以保证达到最高的识别率。
1.  拍摄的时候需要直接拍摄被识别的对象，不要拍摄屏幕上的识别对象，否则会因为频闪问题影响识别率。

![image](https://user-images.githubusercontent.com/36323798/223982209-132e1928-6cd8-467c-9548-94837850ec67.png)


### 返回示例

```
{
    "result": {
        "QRcode_content": "01,01,330XXXX130,50XXXX51,1327.43,20200813,,86BA,",
        "QRcode_location": [
            [68, 77],
            [273, 77],
            [273, 281],
            [68, 281]
        ],
        "invoice_code": "33XXXX4130",
        "machine_code": "",
        "check_code": "",
        "title": "浙江增值税专用发票",
        "invoice_number": "50XXXX51",
        "print_invoice_code": "3300194130",
        "print_invoice_number": "50708251",
        "invoice_date": "2020年08月13日",
        "buyer_name": "杭州XXXX有限公司",
        "buyer_tax_number": "91330101MA28X2CC84",
        "buyer_contact_info": "浙江省航XXXXXXXXXXX商铺0571-56279728",
        "buyer_bank_account_info": "航州联合XXXXXXXXXXX网下沙支行201000179490762",
        "password_area": "59/12<08-49>03>0->2<2-88*XXXXXXXXXXXXXXXXX80-9/5-921-669/6<>*8+90>7/64/58-10><6+2>050/7+1",
        "total_amount_pretax": "￥1327.43",
        "total_tax": "￥172.57",
        "total_amount_inwords": "壹仟伍佰圆整",
        "total_amount": "￥1500.00",
        "seller_name": "杭州乾XXXXXXXXX限公司",
        "seller_tax_number": "91330106MA2GNB0M08",
        "seller_contact_info": "杭州市西XXXXXXXXXX室15058921697",
        "seller_bank_account_info": "建设银行XXXXXXXXXXXXXX8300000571",
        "payee": "段国华",
        "checker": "段国华",
        "payer": "段国华"
    },
    "log_id": "16710XXXXXXXX8447450712"
}
```

### 服务保障
![image](https://user-images.githubusercontent.com/36323798/223982312-e0da54c1-76b1-43c0-a109-fcb7dcded995.png)

### Python(Requests) 调用代码示例

```
import requests

url = "https://eolink.o.apispace.com/fapiao/addvaluedinvoiceOCR"

payload = {"image":"","url":"https://data-apibee.apispace.com/license/16782741889795037be0f-2909-4f99-9dee-d8a8d46349cd","type":"0"}

headers = {
    "X-APISpace-Token":"",
    "Authorization-Type":"apikey",
    "Content-Type":""
}

response=requests.request("POST", url, data=json.dumps(payload), headers=headers)

print(response.text)

```
