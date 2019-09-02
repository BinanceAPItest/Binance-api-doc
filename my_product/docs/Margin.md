



## Margin account transfer (MARGIN)
```
Post /sapi/v1/margin/transfer 
```
Execute transfer between spot account and margin account.

**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
asset | STRING | YES | The asset being transferred, e.g., BTC
amount | DECIMAL | YES | The amount to be transferred
type | INT | YES | 1: transfer from main account to margin account 2: transfer from margin account to main account
recvWindow | LONG | NO  | The value cannot be greater than ```60000```
timestamp | LONG | YES


**Response:**

```javascript
{
    //transaction id
    "tranId": 100000001
}
```

## Margin account borrow (MARGIN)
```
Post /sapi/v1/margin/loan 
```
Apply for a loan.

**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
asset | STRING | YES | 
amount | DECIMAL | YES | 
recvWindow | LONG | NO | The value cannot be greater than ```60000```
timestamp | LONG | YES

**Response:**

```javascript
{
    //transaction id
    "tranId": 100000001
}
```

## Margin account repay (MARGIN)
```
Post /sapi/v1/margin/repay
```
Repay loan for margin account.

**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
asset | STRING | YES | 
amount | DECIMAL | YES | 
recvWindow | LONG | NO | The value cannot be greater than ```60000```
timestamp | LONG | YES

**Response:**

```javascript
{
    //transaction id
    "tranId": 100000001
}
```




## Query margin asset (MARKET_DATA)

```
Get /sapi/v1/margin/asset 
```

**Weight:**
5

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
asset | STRING | YES |

**Response:**

```javascript
{
      "assetFullName": "Binance Coin",
      "assetName": "BNB",
      "isBorrowable": false,
      "isMortgageable": true,
      "userMinBorrow": "0.00000000",
      "userMinRepay": "0.00000000"
}
```

## Query margin pair (MARKET_DATA)
```
Get /sapi/v1/margin/pair 
```

**Weight:**
5

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
symbol | STRING | YES |

**Response:**

```javascript
{
   "id":323355778339572400,
   "symbol":"BTCUSDT",
   "base":"BTC",
   "quote":"USDT",
   "isMarginTrade":true,
   "isBuyAllowed":true,
   "isSellAllowed":true
}
```










## Get all margin assets (MARKET_DATA)

```
Get /sapi/v1/margin/allAssets
```

**Weight:**
5

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
asset | STRING | YES |

**Response:**

```javascript
  [
      {
          "assetFullName": "USD coin",
          "assetName": "USDC",
          "isBorrowable": true,
          "isMortgageable": true,
          "userMinBorrow": "0.00000000",
          "userMinRepay": "0.00000000"
      },
      {
          "assetFullName": "BNB-coin",
          "assetName": "BNB",
          "isBorrowable": true,
          "isMortgageable": true,
          "userMinBorrow": "1.00000000",
          "userMinRepay": "0.00000000"
      },
      {
          "assetFullName": "udst",
          "assetName": "USDT",
          "isBorrowable": true,
          "isMortgageable": true,
          "userMinBorrow": "1.00000000",
          "userMinRepay": "0.00000000"
      },
      {
          "assetFullName": "etherum",
          "assetName": "ETH",
          "isBorrowable": true,
          "isMortgageable": true,
          "userMinBorrow": "0.00000000",
          "userMinRepay": "0.00000000"
      },
      {
          "assetFullName": "Bitcoin",
          "assetName": "BTC",
          "isBorrowable": true,
          "isMortgageable": true,
          "userMinBorrow": "0.00000000",
          "userMinRepay": "0.00000000"
      }
  ]
```

## Get all margin pairs (MARKET_DATA)
```
Get /sapi/v1/margin/allPairs 
```

**Weight:**
5

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
symbol | STRING | YES |

**Response:**

```javascript
[
	{
		"base": "BNB",
  		"id": 351637150141315861,
  		"isBuyAllowed": True,
  		"isMarginTrade": True,
  		"isSellAllowed": True,
  		"quote": "BTC",
  		"symbol": "BNBBTC"
  	},
 	{
 		"base": "TRX",
  		"id": 351637923235429141,
  		"isBuyAllowed": True,
  		"isMarginTrade": True,
  		"isSellAllowed": True,
  		"quote": "BTC",
  		"symbol": "TRXBTC"
  	},
 	{
 		"base": "XRP",
  		"id": 351638112213990165,
  		"isBuyAllowed": True,
  		"isMarginTrade": True,
  		"isSellAllowed": True,
  		"quote": "BTC",
  		"symbol": "XRPBTC"
  	},
 	{
 		"base": "ETH",
  		"id": 351638524530850581,
  		"isBuyAllowed": True,
  		"isMarginTrade": True,
  		"isSellAllowed": True,
  		"quote": "BTC",
  		"symbol": "ETHBTC"
  	},
 	{
 		"base": "BNB",
  		"id": 376870400832855109,
  		"isBuyAllowed": True,
  		"isMarginTrade": True,
  		"isSellAllowed": True,
  		"quote": "USDT",
  		"symbol": "BNBUSDT"
  },
]
```














## Query margin priceIndex (MARKET_DATA)
```
Get /sapi/v1/margin/priceIndex 
```

**Weight:**
5

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
symbol | STRING | YES |

**Response:**

```javascript
{
   "calcTime": 1562046418000,
   "price": "0.00333930",
   "symbol": "BNBBTC"
}
```








## Margin account new order (TRADE)
```
Post  /sapi/v1/margin/order
```
Post a new order for margin account.

**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
symbol | STRING | YES |
side |	ENUM |YES |	BUY<br>SELL
type | ENUM | YES	
quantity | DECIMAL |	YES	
price |	DECIMAL | NO	
stopPrice | DECIMAL | NO | Used with STOP_LOSS, STOP_LOSS_LIMIT, TAKE_PROFIT, and TAKE_PROFIT_LIMIT orders.
newClientOrderId | STRING | NO | A unique id for the order. Automatically generated if not sent.
icebergQty | DECIMAL | NO | Used with LIMIT, STOP_LOSS_LIMIT, and TAKE_PROFIT_LIMIT to create an iceberg order.
newOrderRespType | ENUM | NO | Set the response JSON. ACK, RESULT, or FULL; MARKET and LIMIT order types default to FULL, all other orders default to ACK.
timeInForce | ENUM | NO | GTC,IOC,FOK
recvWindow | LONG | NO | The value cannot be greater than ```60000```
timestamp | LONG | YES

**Response ACK:**

```javascript
{
  "symbol": "BTCUSDT",
  "orderId": 28,
  "clientOrderId": "6gCrw2kRUAF9CvJDGP16IP",
  "transactTime": 1507725176595
}
```
**Response RESULT:**

```javascript
{
  "symbol": "BTCUSDT",
  "orderId": 28,
  "clientOrderId": "6gCrw2kRUAF9CvJDGP16IP",
  "transactTime": 1507725176595,
  "price": "1.00000000",
  "origQty": "10.00000000",
  "executedQty": "10.00000000",
  "cummulativeQuoteQty": "10.00000000",
  "status": "FILLED",
  "timeInForce": "GTC",
  "type": "MARKET",
  "side": "SELL"
}
```
**Response FULL:**

```javascript
{
  "symbol": "BTCUSDT",
  "orderId": 28,
  "clientOrderId": "6gCrw2kRUAF9CvJDGP16IP",
  "transactTime": 1507725176595,
  "price": "1.00000000",
  "origQty": "10.00000000",
  "executedQty": "10.00000000",
  "cummulativeQuoteQty": "10.00000000",
  "status": "FILLED",
  "timeInForce": "GTC",
  "type": "MARKET",
  "side": "SELL",
  "fills": [
    {
      "price": "4000.00000000",
      "qty": "1.00000000",
      "commission": "4.00000000",
      "commissionAsset": "USDT"
    },
    {
      "price": "3999.00000000",
      "qty": "5.00000000",
      "commission": "19.99500000",
      "commissionAsset": "USDT"
    },
    {
      "price": "3998.00000000",
      "qty": "2.00000000",
      "commission": "7.99600000",
      "commissionAsset": "USDT"
    },
    {
      "price": "3997.00000000",
      "qty": "1.00000000",
      "commission": "3.99700000",
      "commissionAsset": "USDT"
    },
    {
      "price": "3995.00000000",
      "qty": "1.00000000",
      "commission": "3.99500000",
      "commissionAsset": "USDT"
    }
  ]
}
```

## Margin account cancel order (TRADE)
```
Delete /sapi/v1/margin/order
```
Cancel an active order for margin account.

**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
symbol | STRING | YES |
orderId | LONG | NO | 
origClientOrderId |	STRING | NO	
newClientOrderId |	STRING | NO | Used to uniquely identify this cancel. Automatically generated by default.
recvWindow | LONG | NO | The value cannot be greater than ```60000```
timestamp | LONG | YES

Either orderId or origClientOrderId must be sent.

**Response:**

```javascript
{
  "symbol": "LTCBTC",
  "orderId": 28,
  "origClientOrderId": "myOrder1",
  "clientOrderId": "cancelMyOrder1",
  "transactTime": 1507725176595,
  "price": "1.00000000",
  "origQty": "10.00000000",
  "executedQty": "8.00000000",
  "cummulativeQuoteQty": "8.00000000",
  "status": "CANCELED",
  "timeInForce": "GTC",
  "type": "LIMIT",
  "side": "SELL"
}
```




## Get transfer history (USER_DATA)
```
Get /sapi/v1/margin/transfer
```

**Weight:**s
5

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
asset |	STRING | No
type | STRING | YES | Tranfer Type: ROLL_IN, ROLL_OUT
startTime |	LONG |	NO	
endTime | LONG | NO	
current | LONG | NO | Currently querying page. Start from 1. Default:1
size |	LONG | NO |	Default:10 Max:100
recvWindow | LONG | NO | The value cannot be greater than ```60000```
timestamp | LONG | YES


**Response:**

```javascript
{
	"rows": [
  	{
  		"amount: "0.10000000",
   		"asset": "BNB",
   		"status": "CONFIRMED",
   		"timestamp": 1566898617,
   		"txId": 5240372201,
   		"type": "ROLL_IN"
  	},
  	{
  		"amount": "5.00000000",
   		"asset": "USDT",
   		"status": "CONFIRMED",
   		"timestamp": 1566888436,
   		"txId": 5239810406,
   		"type": "ROLL_OUT"
  	},
  	{
  		"amount": "1.00000000",
   		"asset": "EOS,
   		"status": "CONFIRMED",
   		"timestamp": 1566888403,
   		"txId": 5239808703,
   		"type": "ROLL_IN"
  	}
 	"total": 3
} 
```
* Response in descending order












## Query loan record (USER_DATA)
```
Get /sapi/v1/margin/loan
```

**Weight:**s
5

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
asset |	STRING | YES	
txId | LONG | NO | the tranId in POST /sapi/v1/margin/loan
startTime |	LONG |	NO	
endTime | LONG | NO	
current | LONG | NO | Currently querying page. Start from 1. Default:1
size |	LONG | NO |	Default:10 Max:100
recvWindow | LONG | NO | The value cannot be greater than ```60000```
timestamp | LONG | YES

* txId or startTime must be sent. txId takes precedence.

**Response:**

```javascript
{
  "rows": [
    {
      "asset": "BNB",
      "principal": "0.84624403",
      "timestamp": 1555056425000,
      //one of PENDING (pending to execution), CONFIRMED (successfully loaned), FAILED (execution failed, nothing happened to your account);
      "status": "CONFIRMED"
    }
  ],
  "total": 1
}
```
* Response in descending order


## Query repay record (USER_DATA)
```
Get /sapi/v1/margin/repay
```

**Weight:**
5

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
asset | STRING |	YES	
txId | LONG | NO | return of /sapi/v1/margin/repay 
startTime | LONG | NO	
endTime | LONG | NO	
current | LONG | NO	| Currently querying page. Start from 1. Default:1
size | LONG | NO | Default:10 Max:100
recvWindow | LONG | NO | The value cannot be greater than ```60000```
timestamp | LONG | YES

txId or startTime must be sent. txId takes precedence.


**Response:**

```javascript
{
     "rows": [
         {
             //Total amount repaid
             "amount": "14.00000000",
             "asset": "BNB",
             //Interest repaid
             "interest": "0.01866667",
             //Principal repaid
             "principal": "13.98133333",
             //one of PENDING (pending to execution), CONFIRMED (successfully loaned), FAILED (execution failed, nothing happened to your account);
             "status": "CONFIRMED",
             "timestamp": 1563438204000,
             "txId": 2970933056
         }
     ],
     "total": 1
}
```
* Response in descending order




## Get interest history (USER_DATA)
```
Get /sapi/v1/margin/interestHistory
```

**Weight:**s
5

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
asset |	STRING | No
startTime |	LONG |	NO	
endTime | LONG | NO	
current | LONG | NO | Currently querying page. Start from 1. Default:1
size |	LONG | NO |	Default:10 Max:100
recvWindow | LONG | NO | The value cannot be greater than ```60000```
timestamp | LONG | YES


**Response:**

```javascript
  {
      "rows": [
          {
              "asset": "BNB",
              "interest": "0.02414667",
              "interestAccuredTime": 1566813600,
              "interestRate": "0.01600000",
              "principal": "36.22000000",
              "type": "ON_BORROW"
          },
          {
              "asset": "BNB",
              "interest": "0.02019334",
              "interestAccuredTime": 1566813600,
              "interestRate": "0.01600000",
              "principal": "30.29000000",
              "type": "ON_BORROW"
          },
          {
              "asset": "BNB",
              "interest": "0.02098667",
              "interestAccuredTime": 1566813600,
              "interestRate": "0.01600000",
              "principal": "31.48000000",
              "type": "ON_BORROW"
          },
          {
              "asset": "BNB",
              "interest": "0.02483334",
              "interestAccuredTime": 1566806400,
              "interestRate": "0.01600000",
              "principal": "37.25000000",
              "type": "ON_BORROW"
          },
          {
              "asset": "BNB",
              "interest": "0.02165334",
              "interestAccuredTime": 1566806400,
              "interestRate": "0.01600000",
              "principal": "32.48000000",
              "type": "ON_BORROW"
          }
      ],
      "total": 5
  }
```
* Response in descending order



## Get Force Liquidation Record (USER_DATA)
```
Get /sapi/v1/margin/forceLiquidationRec
```

**Weight:**s
5

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
startTime |	LONG |	NO	
endTime | LONG | NO	
current | LONG | NO | Currently querying page. Start from 1. Default:1
size |	LONG | NO |	Default:10 Max:100
recvWindow | LONG | NO | The value cannot be greater than ```60000```
timestamp | LONG | YES


**Response:**

```javascript
  {
      "rows": [
          {
              "avgPrice": "0.00388359",
              "executedQty": "31.39000000",
              "orderId": 180015097,
              "price": "0.00388110",
              "qty": "31.39000000",
              "side": "SELL",
              "symbol": "BNBBTC",
              "timeInForce": "GTC",
              "updatedTime": 1558941374745
          }
      ],
      "total": 1
  }
```
* Response in descending order






## Query margin account details (USER_DATA)
```
Get /sapi/v1/margin/account
```

**Weight:**
5

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
recvWindow | LONG | NO | The value cannot be greater than ```60000```
timestamp | LONG | YES |

**Response:**

```javascript
{
      "borrowEnabled": true,
      "marginLevel": "11.64405625",
      "totalAssetOfBtc": "6.82728457",
      "totalLiabilityOfBtc": "0.58633215",
      "totalNetAssetOfBtc": "6.24095242",
      "tradeEnabled": true,
      "transferEnabled": true,
      "userAssets": [
          {
              "asset": "BTC",
              "borrowed": "0.00000000",
              "free": "0.00499500",
              "interest": "0.00000000",
              "locked": "0.00000000",
              "netAsset": "0.00499500"
          },
          {
              "asset": "BNB",
              "borrowed": "201.66666672",
              "free": "2346.50000000",
              "interest": "0.00000000",
              "locked": "0.00000000",
              "netAsset": "2144.83333328"
          },
          {
              "asset": "ETH",
              "borrowed": "0.00000000",
              "free": "0.00000000",
              "interest": "0.00000000",
              "locked": "0.00000000",
              "netAsset": "0.00000000"
          },
          {
              "asset": "USDT",
              "borrowed": "0.00000000",
              "free": "0.00000000",
              "interest": "0.00000000",
              "locked": "0.00000000",
              "netAsset": "0.00000000"
          }
      ]
}
```


## Query margin account's order (USER_DATA)

```
Get /sapi/v1/margin/order 
```

**Weight:**
5

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
symbol | STRING | YES |
orderId | STRING | NO |	
origClientOrderId | STRING | NO	|
recvWindow | LONG | NO | The value cannot be greater than ```60000```
timestamp | LONG | YES

Notes:

* Either orderId or origClientOrderId must be sent.
* For some historical orders cummulativeQuoteQty will be < 0, meaning the data is not available at this time.

**Response:**

```javascript
{
   "clientOrderId": "ZwfQzuDIGpceVhKW5DvCmO",
   "cummulativeQuoteQty": "0.00000000",
   "executedQty": "0.00000000",
   "icebergQty": "0.00000000",
   "isWorking": true,
   "orderId": 213205622,
   "origQty": "0.30000000",
   "price": "0.00493630",
   "side": "SELL",
   "status": "NEW",
   "stopPrice": "0.00000000",
   "symbol": "BNBBTC",
   "time": 1562133008725,
   "timeInForce": "GTC",
   "type": "LIMIT",
   "updateTime": 1562133008725
}
```

## Query margin account's open order (USER_DATA)
```
Get  /sapi/v1/margin/openOrders 
```

**Weight:**
10

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
symbol | STRING | NO |
recvWindow | LONG | NO | The value cannot be greater than ```60000```
timestamp | LONG | YES

* If the symbol is not sent, orders for all symbols will be returned in an array.
* When all symbols are returned, the number of requests counted against the rate limiter is equal to the number of symbols currently trading on the exchange.

**Response:**

```javascript
[
   {
       "clientOrderId": "qhcZw71gAkCCTv0t0k8LUK",
       "cummulativeQuoteQty": "0.00000000",
       "executedQty": "0.00000000",
       "icebergQty": "0.00000000",
       "isWorking": true,
       "orderId": 211842552,
       "origQty": "0.30000000",
       "price": "0.00475010",
       "side": "SELL",
       "status": "NEW",
       "stopPrice": "0.00000000",
       "symbol": "BNBBTC",
       "time": 1562040170089,
       "timeInForce": "GTC",
       "type": "LIMIT",
       "updateTime": 1562040170089
      }
]
```


## Query margin account's all order (USER_DATA)
```
Get /sapi/v1/margin/allOrders 
```

**Weight:**
5

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
symbol | STRING | YES |
orderId | LONG | NO	
startTime |	LONG | NO	
endTime | LONG | NO	
limit |	INT | NO | Default 500; max 1000.
recvWindow | LONG | NO | The value cannot be greater than ```60000```
timestamp | LONG | YES

Notes:

* If orderId is set, it will get orders >= that orderId. Otherwise most recent orders are returned.
* For some historical orders cummulativeQuoteQty will be < 0, meaning the data is not available at this time.

**Response:**

```javascript
[
      {
          "clientOrderId": "D2KDy4DIeS56PvkM13f8cP",
          "cummulativeQuoteQty": "0.00000000",
          "executedQty": "0.00000000",
          "icebergQty": "0.00000000",
          "isWorking": false,
          "orderId": 41295,
          "origQty": "5.31000000",
          "price": "0.22500000",
          "side": "SELL",
          "status": "CANCELED",
          "stopPrice": "0.18000000",
          "symbol": "BNBBTC",
          "time": 1565769338806,
          "timeInForce": "GTC",
          "type": "TAKE_PROFIT_LIMIT",
          "updateTime": 1565769342148
      },
      {
          "clientOrderId": "gXYtqhcEAs2Rn9SUD9nRKx",
          "cummulativeQuoteQty": "0.00000000",
          "executedQty": "0.00000000",
          "icebergQty": "1.00000000",
          "isWorking": true,
          "orderId": 41296,
          "origQty": "6.65000000",
          "price": "0.18000000",
          "side": "SELL",
          "status": "CANCELED",
          "stopPrice": "0.00000000",
          "symbol": "BNBBTC",
          "time": 1565769348687,
          "timeInForce": "GTC",
          "type": "LIMIT",
          "updateTime": 1565769352226
      },
      {
          "clientOrderId": "duDq1BqohhcMmdMs9FSuDy",
          "cummulativeQuoteQty": "0.39450000",
          "executedQty": "2.63000000",
          "icebergQty": "0.00000000",
          "isWorking": true,
          "orderId": 41297,
          "origQty": "2.63000000",
          "price": "0.00000000",
          "side": "SELL",
          "status": "FILLED",
          "stopPrice": "0.00000000",
          "symbol": "BNBBTC",
          "time": 1565769358139,
          "timeInForce": "GTC",
          "type": "MARKET",
          "updateTime": 1565769358139
      }

]
```

## Query margin account's trade list (USER_DATA)
```
Get  /sapi/v1/margin/myTrades 
```

**Weight:**
5

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
symbol | STRING | YES |
startTime |	LONG | NO	
endTime | LONG | NO	
fromId | LONG | NO | TradeId to fetch from. Default gets most recent trades.
limit |	INT | NO | Default 500; max 1000.
recvWindow | LONG | NO | The value cannot be greater than ```60000```
timestamp | LONG | YES

Notes:
* If fromId is set, it will get orders >= that fromId. Otherwise most recent orders are returned.


**Response:**

```javascript
[{
	"commission": "0.00006000",
	"commissionAsset": "BTC",
	"id": 34,
	"isBestMatch": true,
	"isBuyer": false,
	"isMaker": false,
	"orderId": 39324,
	"price": "0.02000000",
	"qty": "3.00000000",
	"symbol": "BNBBTC",
	"time": 1561973357171
},{
	"commission": "0.00002950",
	"commissionAsset": "BTC",
	"id": 32,
	"isBestMatch": true,
	"isBuyer": false,
	"isMaker": true,
	"orderId": 39319,
	"price": "0.00590000",
	"qty": "5.00000000",
	"symbol": "BNBBTC",
	"time": 1561964645345
}]
```

## Query max borrow (USER_DATA)
```
Get /sapi/v1/margin/maxBorrowable 
```

**Weight:**
5

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
asset | STRING | YES |
recvWindow | LONG | NO | The value cannot be greater than ```60000```
timestamp | LONG | YES

**Response:**

```javascript
{
    "amount": "1.69248805"
}
```

## Query max transfer-out amount (USER_DATA)
```
Get /sapi/v1/margin/maxTransferable 
```

**Weight:**
5

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
asset | STRING | YES |
recvWindow | LONG | NO | The value cannot be greater than ```60000```
timestamp | LONG | YES

**Response:**

```javascript
 {
      "amount": "3.59498107"
 }
```

## Start user data stream for margin account (USER_STREAM)
```
POST  /sapi/v1/userDataStream
```

**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
recvWindow | LONG | NO | The value cannot be greater than ```60000```
timestamp | LONG | YES |

**Response:**

```javascript
{"listenKey":  "T3ee22BIYuWqmvne0HNq2A2WsFlEtLhvWCtItw6ffhhdmjifQ2tRbuKkTHhr"}
```

## Delete user data stream for margin account  (USER_STREAM)
```
DELETE  /sapi/v1/userDataStream
```

**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
listenKey | STRING | YES |

**Response:**

```javascript
{}
```

## Ping user data stream for margin account  (USER_STREAM)
```
PUT  /sapi/v1/userDataStream
```

**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Description
------------ | ------------ | ------------ | ------------
listenKey | STRING | YES |

**Response:**

```javascript
{}
```
