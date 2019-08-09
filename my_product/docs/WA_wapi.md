## Withdraw
```
POST /wapi/v3/withdraw.html (HMAC SHA256)
```
Submit a withdraw request.

**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
asset	|  STRING |	YES	
address	 | STRING | YES	
addressTag | STRING | NO | Secondary address identifier for coins like XRP,XMR etc.
amount | DECIMAL | YES	
name | STRING | NO | Description of the address
recvWindow | LONG | NO	
timestamp | LONG | YES	
**Response:**
```javascript
{
    "msg": "success",
    "success": true,
    "id":"7213fea8e94b4a5593d507237e5a555b"
}
```


## Deposit History (USER_DATA)
```
GET /wapi/v3/depositHistory.html (HMAC SHA256)
```
Fetch deposit history.

**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
asset | STRING | NO	
status | INT | NO | 0(0:pending,6: credited but cannot withdraw, 1:success)
startTime | LONG | NO	
endTime | LONG | NO	
recvWindow | LONG | NO	
timestamp | LONG | YES	


**Response:**
```javascript
{
    "depositList": [
        {
            "insertTime": 1508198532000,
            "amount": 0.04670582,
            "asset": "ETH",
            "address": "0x6915f16f8791d0a1cc2bf47c13a6b2a92000504b",
            "txId": "0xdf33b22bdb2b28b1f75ccd201a4a4m6e7g83jy5fc5d5a9d1340961598cfcb0a1",
            "status": 1
        },
        {
            "insertTime": 1508298532000,
            "amount": 1000,
            "asset": "XMR",
            "address": "463tWEBn5XZJSxLU34r6g7h8jtxuNcDbjLSjkn3XAXHCbLrTTErJrBWYgHJQyrCwkNgYvyV3z8zctJLPCZy24jvb3NiTcTJ",
            "addressTag": "342341222",
            "txId": "b3c6219639c8ae3f9cf010cdc24fw7f7yt8j1e063f9b4bd1a05cb44c4b6e2509",
            "status": 1
        }
    ],
    "success": true
}
```

## Withdraw History (USER_DATA)
```
GET /wapi/v3/withdrawHistory.html (HMAC SHA256)
```
Fetch withdraw history.

**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
asset | STRING | NO	
status | INT | NO | 0(0:Email Sent,1:Cancelled 2:Awaiting Approval 3:Rejected 4:Processing 5:Failure 6Completed)
startTime | LONG | NO	
endTime | LONG | NO	
recvWindow | LONG | NO	
timestamp | LONG | YES	


**Response:**
```javascript
{
    "withdrawList": [
        {
            "id":"7213fea8e94b4a5593d507237e5a555b",
            "amount": 1,
            "address": "0x6915f16f8791d0a1cc2bf47c13a6b2a92000504b",
            "asset": "ETH",
            "txId": "0xdf33b22bdb2b28b1f75ccd201a4a4m6e7g83jy5fc5d5a9d1340961598cfcb0a1",
            "applyTime": 1508198532000,
            "status": 4
        },
        {
            "id":"7213fea8e94b4a5534ggsd237e5a555b",
            "amount": 1000,
            "address": "463tWEBn5XZJSxLU34r6g7h8jtxuNcDbjLSjkn3XAXHCbLrTTErJrBWYgHJQyrCwkNgYvyV3z8zctJLPCZy24jvb3NiTcTJ",
            "addressTag": "342341222",
            "txId": "b3c6219639c8ae3f9cf010cdc24fw7f7yt8j1e063f9b4bd1a05cb44c4b6e2509",
            "asset": "XMR",
            "applyTime": 1508198532000,
            "status": 4
        }
    ],
    "success": true
}
```




## Deposit Address (USER_DATA)
```
GET  /wapi/v3/depositAddress.html (HMAC SHA256)
```
Fetch deposit address.

**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
asset | STRING | YES	
status | Boolean |NO
recvWindow | LONG | NO	
timestamp | LONG | YES	

**Response:**
```javascript
{
    "address": "0x6915f16f8791d0a1cc2bf47c13a6b2a92000504b",
    "success": true,
    "addressTag": "1231212",
    "asset": "BNB"
}

```

## Account Status (USER_DATA)
```
GET /wapi/v3/accountStatus.html
```
Fetch account status detail.

**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
recvWindow | LONG | NO	
timestamp | LONG | YES	

**Response:**
```javascript
{
    "msg": "Order failed:Low Order fill rate! Will be reactivated after 5 minutes.",
    "success": true,
    "objs": [
        "5"
    ]
}
```

## System Status (System)
```
GET /wapi/v3/systemStatus.html
```

Fetch system status.
**Response:**
```javascript
{ 
    "status": 0,              // 0: normal，1：system maintenance
    "msg": "normal"           // normal or system maintenance
}
```

## Account API Trading Status (USER_DATA)
```
GET /wapi/v3/apiTradingStatus.html
```
Fetch account api trading status detail.

For more details about our api trading rules, please refer to the link:https://support.binance.com/hc/en-us/articles/115003235691


**Weight:**
1


**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
recvWindow | LONG | NO  
timestamp | LONG | YES  

**Response:**
```javascript
{
    "success": true,     // Query result
    "status": {          // API trading status detail
        "isLocked": false,   // API trading function is locked or not
        "plannedRecoverTime": 0,  // If API trading function is locked, this is the planned recover time
        "triggerCondition": { 
            "GCR": 150,  // Number of GTC orders
            "IFER": 150, // Number of FOK/IOC orders
            "UFR": 300   // Number of orders
        },
        "indicators": {  // The indicators updated every 30 seconds
           "BTCUSDT": [  // The symbol
            {
            "i": "UFR",  // Unfilled Ratio (UFR)
            "c": 20,     // Count of all orders
            "v": 0.05,   // Current UFR value
            "t": 0.995   // Trigger UFR value
            },
            {
            "i": "IFER", // IOC/FOK Expiration Ratio (IFER)
            "c": 20,     // Count of FOK/IOC orders
            "v": 0.99,   // Current IFER value
            "t": 0.99    // Trigger IFER value
            },
            {
            "i": "GCR",  // GTC Cancellation Ratio (GCR)
            "c": 20,     // Count of GTC orders
            "v": 0.99,   // Current GCR value
            "t": 0.99    // Trigger GCR value
            }
            ],
            "ETHUSDT": [ 
            {
            "i": "UFR",
            "c": 20,
            "v": 0.05,
            "t": 0.995
            },
            {
            "i": "IFER",
            "c": 20,
            "v": 0.99,
            "t": 0.99
            },
            {
            "i": "GCR",
            "c": 20,
            "v": 0.99,
            "t": 0.99
            }
            ]
        },
        "updateTime": 1547630471725   // The query result return time
    }
}
```

## DustLog (USER_DATA)
```
GET /wapi/v3/userAssetDribbletLog.html   (HMAC SHA256)
```
Fetch small amounts of assets exchanged BNB records.


**Weight:**
1


**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
recvWindow | LONG | NO  
timestamp | LONG | YES  

**Response:**
```javascript
{
    "success": true, 
    "results": {
        "total": 2,   //Total counts of exchange
        "rows": [
            {
                "transfered_total": "0.00132256",//Total transfered BNB amount for this exchange.
                "service_charge_total": "0.00002699",   //Total service charge amount for this exchange.
                "tran_id": 4359321,
                "logs": [           //Details of  this exchange.
                    {
                        "tranId": 4359321,
                        "serviceChargeAmount": "0.000009",
                        "uid": "10000015",
                        "amount": "0.0009",
                        "operateTime": "2018-05-03 17:07:04",
                        "transferedAmount": "0.000441",
                        "fromAsset": "USDT"
                    },
                    {
                        "tranId": 4359321,
                        "serviceChargeAmount": "0.00001799",
                        "uid": "10000015",
                        "amount": "0.0009",
                        "operateTime": "2018-05-03 17:07:04",
                        "transferedAmount": "0.00088156",
                        "fromAsset": "ETH"
                    }
                ],
                "operate_time": "2018-05-03 17:07:04" //The time of this exchange.
            },
            {
                "transfered_total": "0.00058795",
                "service_charge_total": "0.000012",
                "tran_id": 4357015,
                "logs": [       // Details of  this exchange.
                    {
                        "tranId": 4357015,
                        "serviceChargeAmount": "0.00001",
                        "uid": "10000015",
                        "amount": "0.001",
                        "operateTime": "2018-05-02 13:52:24",
                        "transferedAmount": "0.00049",
                        "fromAsset": "USDT"
                    },
                    {
                        "tranId": 4357015,
                        "serviceChargeAmount": "0.000002",
                        "uid": "10000015",
                        "amount": "0.0001",
                        "operateTime": "2018-05-02 13:51:11",
                        "transferedAmount": "0.00009795",
                        "fromAsset": "ETH"
                    }
                ],
                "operate_time": "2018-05-02 13:51:11"
            }
        ]
    }
}
```

## Trade Fee (USER_DATA)
```
GET  /wapi/v3/tradeFee.html (HMAC SHA256)
```
Fetch trade fee.


**Weight:**
1


**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
recvWindow | LONG | NO  
timestamp | LONG | YES  
symbol | STRING | NO

**Response:**
```javascript
{
	"tradeFee": [{
		"symbol": "ADABNB",
		"maker": 0.9000,
		"taker": 1.0000
	}, {
		"symbol": "BNBBTC",
		"maker": 0.3000,
		"taker": 0.3000
	}],
	"success": true
}
```


## Asset Detail (USER_DATA)
```
GET  /wapi/v3/assetDetail.html (HMAC SHA256)
```
Fetch asset detail.


**Weight:**
1


**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
recvWindow | LONG | NO  
timestamp | LONG | YES  

**Response:**
```javascript
{
    "success": true,
    "assetDetail": {
        "CTR": {
            "minWithdrawAmount": "70.00000000", //min withdraw amount
            "depositStatus": false,//deposit status
            "withdrawFee": 35, // withdraw fee
            "withdrawStatus": true, //withdraw status
            "depositTip": "Delisted, Deposit Suspended" //reason
        },
        "SKY": {
            "minWithdrawAmount": "0.02000000",
            "depositStatus": true,
            "withdrawFee": 0.01,
            "withdrawStatus": true
        }	
    }
}
```


## Query Sub-account List(For Master Account)
```
GET   /wapi/v3/sub-account/list.html (HMAC SHA256)
```
Fetch sub account list.


**Weight:**
1


**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
email | STRING | NO | Sub-account email
status | STRING | NO | Sub-account status: enabled or disabled
page | INT | NO | Default value: 1
limit | INT | NO | Default value: 500
recvWindow | LONG | NO  
timestamp | LONG | YES  

**Response:**
```javascript
{
    "success":true,
    "subAccounts":[
        {
            "email":"123@test.com",
            "status":"enabled",
            "activated":true,
            "mobile":"91605290",
            "gAuth":true,
            "createTime":1544433328000
        },
        {
            "email":"321@test.com",
            "status":"disabled",
            "activated":true,
            "mobile":"22501238",
            "gAuth":true,
            "createTime":1544433328000
        }
    ]
}
```

## Query Sub-account Transfer History(For Master Account)
```
GET   /wapi/v3/sub-account/transfer/history.html (HMAC SHA256)
```
Fetch transfer history list


**Weight:**
1


**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
email | STRING | YES | Sub-account email
startTime | LONG | NO | Default return the history with in 100 days
endTime | LONG | NO | Default return the history with in 100 days
page | INT | NO | Default value: 1
limit | INT | NO | Default value: 500
recvWindow | LONG | NO  
timestamp | LONG | YES  

**Response:**
```javascript
{
    "success":true,
    "transfers":[
        {
            "from":"aaa@test.com",
            "to":"bbb@test.com",
            "asset":"BTC",
            "qty":"1",
            "time":1544433328000
        },
        {
            "from":"bbb@test.com",
            "to":"ccc@test.com",
            "asset":"ETH",
            "qty":"2",
            "time":1544433328000
        }
    ]
}
```

## Sub-account Transfer(For Master Account)
```
POST   /wapi/v3/sub-account/transfer.html (HMAC SHA256)
```
Execute sub-account transfer


**Weight:**
1


**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
fromEmail | STRING | YES | Sender email
toEmail | STRING | YES | Recipient email
asset | STRING | YES
amount | DECIMAL | YES
recvWindow | LONG | NO  
timestamp | LONG | YES  

**Response:**
```javascript
{
    "success":true,
    "txnId":"2966662589"
}

```


## Query Sub-account Assets(For Master Account)
```
GET   /wapi/v3/sub-account/assets.html (HMAC SHA256)
```
Fetch sub-account assets

**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
email | STRING | YES  | Sub account email
recvWindow | LONG | NO  
timestamp | LONG | YES  
symbol | STRING | NO

**Response:**
```javascript
{

    "success":true,
    "balances":[
        {
            "asset":"ADA",
            "free":10000,
            "locked":0
        },
        {
            "asset":"BNB",
            "free":10003,
            "locked":0
        },
        {
            "asset":"BTC",
            "free":11467.6399,
            "locked":0
        },
        {
            "asset":"ETH",
            "free":10004.995,
            "locked":0
        },
        {
            "asset":"USDT",
            "free":11652.14213,
            "locked":0
        }
    ]
}
```

