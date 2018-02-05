.. _market-api:

********************************************************************************
Market API
********************************************************************************

Market
------

    **GET /market**

        **Example response**::

            [
                {
                    "name": "BCCBTC",
                    "market_order_min_money": "0.001",
                    "stock_precision": 4,
                    "money": "BTC",
                    "maker_fee_rate": 0,
                    "order_min_vol": "0.001",
                    "money_precision": 6,
                    "market_order_enabled": false,
                    "stock": "BCC",
                    "enabled": true,
                    "taker_fee_rate": 0
                }
            ]

Market Depth
------------

**GET /market/{market}/depth**

    **Example response**::

            /market/BCCBTC/depth

            {
            "bids": [
                ["0.133", "0.0069"],
                ["0.132", "1"],
                ["0.13", "1"],
                ["0.122508", "1.3"],
                ["0.122001", "1.2"],
                ["0.122", "1"],
                ["0.12", "0.6151"],
                ["0.111001", "5"],
                ["0.111", "3.1927"],
                ["0.1022", "50"]],
            "asks": [
                ["0.1363", "1.5"],
                ["0.139999", "1.5"],
                ["0.14", "3"],
                ["0.156", "5.9824"],
                ["0.16", "5.0397"],
                ["0.199999", "5"],
                ["0.2", "40.4095"],
                ["0.22", "1.7496"],
                ["0.25", "1.035"],
                ["0.33", "3.1"]]
            }

           **URL**:

            *``market`` *(required) - market name, for example *(BCCBTC)*.
Market Ticker
-------------

**GET /market/{market}/ticker**

    **Example response**::

            /market/BCCBTC/ticker

                {
                    "high": "0.139999",
                    "ask": "0.1363",
                    "bid": "0.134",
                    "last": "0.1345",
                    "low": "0.1345"
                }

           **URL**:

            *``market`` *(required) - market name, for example *(BCCBTC)*.
Market Order Finished
---------------------

**GET /market/{market}/order/finished**

    **Example response**::

            /market/BCCBTC/order/finished?limit=10&offset=0

            {
              "records": [
                {
                  "ctime": 1516689377.805243,
                  "maker_fee": "0",
                  "price": "0.151",
                  "deal_fee": "0",
                  "id": 187,
                  "source": "bitpie.client",
                  "amount": "0.001",
                  "ftime": 1516689386.619962,
                  "user": 116480,
                  "deal_stock": "0.001",
                  "deal_money": "0.000151",
                  "type": 1,
                  "side": 1,
                  "market": "BCCBTC",
                  "taker_fee": "0"
                }
              ],
              "limit": 10,
              "offset": 0
            }

           **URL**:

            *``market`` *(required) - market name, for example *(BCCBTC)*.

        **Parameters**:
            * ``offset``*(optional)* *(int)* - sinceId.
            * ``limit`` *(optional)* *(int)* - limit.

Market Order Pending
--------------------

**GET /market/{market}/order/pending**

    **Example response**::

            /market/BTGBTC/order/pending?limit=10&offset=0
            {
                "records": [
                    {
                        "deal_fee": "0",
                        "ctime": 1517580449.685034,
                        "maker_fee": "0.001",
                        "price": "0.001254",
                        "deal_stock": "0",
                        "side": 2,     // 1：sell，2：buy
                        "source": "bitpie.client",
                        "amount": "30",
                        "user": 259285,
                        "mtime": 1517580449.685034,
                        "deal_money": "0",
                        "left": "30",
                        "type": 1,      // 1: limit order，2：market order
                        "id": 20321,
                        "market": "BTGBTC",
                        "taker_fee": "0.001"
                    }
                ],
                "total": 1,
                "limit": 10,
                "offset": 0
            }

           **URL**:

            *``market`` *(required) - market name, for example *(BCCBTC)*.

        **Parameters**:
            * ``offset``*(optional)* *(int)* - sinceId.
            * ``limit`` *(optional)* *(int)* - limit.

Market Order Details
--------------------

**GET /market/{market}/order/{orderId}/details**

    **Example response**::

            /market/BTGBTC/order/13479/details

                    {
            "records": [
                {
                    "fee": "0.0010194",
                    "deal": "0.0161197722",
                    "price": "0.015813",
                    "amount": "1.0194",
                    "role": 1,
                    "user": 259285,
                    "time": 1517224387.037182,
                    "deal_order_id": 13506,
                    "id": 5288
                }
            ],
            "limit": 20,
            "offset": 0
        }

        **URL**:
            * ``market`` *(required)*  - market name, for example *(BCCBTC)*.
            * ``orderId`` *(required)* - id,for example *(2168)*.

Market Order Cancel
-------------------

**POST /market/{market}/order/{orderId}/cancel**

    **Example response**::

            /market/BCCBTC/order/2168/cancel
                {
                    "deal_fee": "0",
                    "ctime": 1517799540.747482,
                    "maker_fee": "0.0006",
                    "price": "0.154",
                    "deal_stock": "0",
                    "side": 1,
                    "source": "expie.api.https",
                    "amount": "0.02",
                    "user": 100056,
                    "mtime": 1517799540.747482,
                    "deal_money": "0",
                    "left": "0.02",
                    "type": 1,
                    "id": 2168,
                    "market": "BCCBTC",
                    "taker_fee": "0.0006"
                }

        **URL**:
            * ``market`` *(required)*  - market name, for example *(BCCBTC)*.
            * ``orderId`` *(required)* - id,for example *(2168)*.

Market Order Place
------------------

**POST /market/{market}/order/place**

    **Example response**::

                /market/BCCBTC/order/place
                {
                    "deal_fee": "0",
                    "ctime": 1517801276.820693,
                    "maker_fee": "0.0006",
                    "price": "0.154",
                    "deal_stock": "0",
                    "side": 1,
                    "source": "expie.api.https",
                    "amount": "0.02",
                    "user": 100056,
                    "mtime": 1517801276.820693,
                    "deal_money": "0",
                    "left": "0.02",
                    "type": 1,
                    "id": 2169,
                    "market": "BCCBTC",
                    "taker_fee": "0.0006"
                }


            **URL**:
            *``market`` *(required) - market name, for example *(BCCBTC)*.

            **Parameters**:
            * ``side`` *(required)* *(int)* - trade type, for example *(1)*.
            * ``amount`` *(required)* *(float)* - count or amount.
            * ``price`` *(required)* *(float)* - transfer to address and value.

        .. note::
            * ``side`` 1: sell, 2: buy.
            * ``amount`` count or amount.
            * ``price`` price.
