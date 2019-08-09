## Dust Transfer (USER_DATA)
```
Post /sapi/v1/asset/dust (HMAC SHA256)
```
Convert dust assets to BNB.

**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
asset | ARRAY | YES | The asset being converted. For example: asset=BTC&asset=USDT
recvWindow | LONG | NO |
timestamp | LONG | YES |


**Response:**
```javascript
{
    "totalServiceCharge":"0.02102542",
    "totalTransfered":"1.05127099",
    "transferResult":[
        {
            "amount":"0.03000000",
            "fromAsset":"ETH",
            "operateTime":1563368549307,
            "serviceChargeAmount":"0.00500000",
            "tranId":2970932918,
            "transferedAmount":"0.25000000"
        },
        {
            "amount":"0.09000000",
            "fromAsset":"LTC",
            "operateTime":1563368549404,
            "serviceChargeAmount":"0.01548000",
            "tranId":2970932918,
            "transferedAmount":"0.77400000"
        },
        {
            "amount":"248.61878453",
            "fromAsset":"TRX",
            "operateTime":1563368549489,
            "serviceChargeAmount":"0.00054542",
            "tranId":2970932918,
            "transferedAmount":"0.02727099"
        }
    ]
}
```

## Asset dividend record (USER_DATA)
```
Get /sapi/v1/asset/assetDividend (HMAC SHA256)
```
Query asset dividend record.

**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
asset | STRING | NO |
startTime | LONG | NO |
endTime | LONG | NO |
recvWindow | LONG | NO |
timestamp | LONG | YES |

**Response:**
```javascript
{
    "rows":[
        {
            "amount":"10.00000000",
            "asset":"BHFT",
            "divTime":1563189166000,
            "enInfo":"BHFT distribution",
            "tranId":2968885920
        },
        {
            "amount":"10.00000000",
            "asset":"BHFT",
            "divTime":1563189165000,
            "enInfo":"BHFT distribution",
            "tranId":2968885920
        }
    ],
    "total":2
}
```
-