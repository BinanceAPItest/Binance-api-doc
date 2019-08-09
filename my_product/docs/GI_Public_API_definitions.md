# Public API definitions
## Terminology
* `base asset` refers to the asset that is the `quantity` of a symbol.
* `quote asset` refers to the asset that is the `price` of a symbol.

## ENUM definitions
**Symbol status (status):**

* PRE_TRADING
* TRADING
* POST_TRADING
* END_OF_DAY
* HALT
* AUCTION_MATCH
* BREAK

**Symbol type:**

* SPOT

**Order status (status):**

* NEW
* PARTIALLY_FILLED
* FILLED
* CANCELED
* PENDING_CANCEL (currently unused)
* REJECTED
* EXPIRED

**Order types (orderTypes, type):**

* LIMIT
* MARKET
* STOP_LOSS
* STOP_LOSS_LIMIT
* TAKE_PROFIT
* TAKE_PROFIT_LIMIT
* LIMIT_MAKER

**Order side (side):**

* BUY
* SELL

**Time in force (timeInForce):**

* GTC
* IOC
* FOK

**Kline/Candlestick chart intervals:**

m -> minutes; h -> hours; d -> days; w -> weeks; M -> months

* 1m
* 3m
* 5m
* 15m
* 30m
* 1h
* 2h
* 4h
* 6h
* 8h
* 12h
* 1d
* 3d
* 1w
* 1M

**Rate limiters (rateLimitType)**
* REQUEST_WEIGHT

    ```json
    {
      "rateLimitType": "REQUEST_WEIGHT",
      "interval": "MINUTE",
      "intervalNum": 1,
      "limit": 1200
    }
    ```

* ORDERS

    ```json
    {
      "rateLimitType": "ORDERS",
      "interval": "SECOND",
      "intervalNum": 1,
      "limit": 10
    }
    ```
* RAW_REQUESTS

    ```json
    {
      "rateLimitType": "RAW_REQUESTS",
      "interval": "MINUTE",
      "intervalNum": 5,
      "limit": 5000
    }
    ```

**Rate limit intervals (interval)**

* SECOND
* MINUTE
* DAY
