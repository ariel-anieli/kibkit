# kibkit
Pulls CSV from Kibana visualization

## List dashboards
```
./kibkit -u USER:PSWD -H HOST -ld

73a133b0-7325-11ea-b36a-87ca4a6a28f0,dev_session
c3e418b0-7f23-11ea-9a41-e372321608d2,dev_session-requirements
ee00ecc0-8092-11ea-9a41-e372321608d2,req_sessions
6fd956d0-84ab-11ea-9a41-e372321608d2,beta_session-requirements
```

## Then visualizations within a dashboard
```
./kibkit -u USER:PSWD -H HOST -lv 6fd956d0-84ab-11ea-9a41-e372321608d2

beta_session-policy20
beta_session-policy20-proto
exp_session-duration
beta_session-duration
exp_sessionipsrc
exp_sessionipdst
beta_session-policy20throughput
beta_session-policy20volume
beta_session-policy20throughput-proto
beta_session-policy20setup
beta_session-proto20
beta_session-policy20volume-proto
beta_session-proto20throughput
beta_session-proto30throughput-rxtx
beta_session-proto20volume
beta_session-policy20duration-proto
beta_session-npuoffload-protocol
beta_session-nooffload-protocol
beta_session-ipunique
dev_session-policy30throughput-rxtx
```

## Hence, get visualization data in CSV
```
./kibkit -u USER:PSWD -H HOST -svd beta_session-ipunique,6fd956d0-84ab-11ea-9a41-e372321608d2

```

## Or, aggregations sent to Kibana
```
./kibkit -u USER:PSWD -H HOST -sva beta_session-ipunique,6fd956d0-84ab-11ea-9a41-e372321608d2 | python -mjson.tool
[
    {
        "id": "1",
        "enabled": true,
        "type": "cardinality",
        "schema": "metric",
        "params": {
            "field": "src_ip",
            "customLabel": "Unique IP SRC"
        }
    },
    {
        "id": "2",
        "enabled": true,
        "type": "cardinality",
        "schema": "metric",
        "params": {
            "field": "dst_ip",
            "customLabel": "Unique IP DST"
        }
    },
    {
        "id": "3",
        "enabled": true,
        "type": "terms",
        "schema": "segment",
        "params": {
            "field": "vd_policy_id.raw",
            "orderBy": "custom",
            "orderAgg": {
                "id": "3-orderAgg",
                "enabled": true,
                "type": "count",
                "schema": "orderAgg",
                "params": {}
            },
            "order": "desc",
            "size": 60,
            "otherBucket": false,
            "otherBucketLabel": "Other",
            "missingBucket": false,
            "missingBucketLabel": "Missing",
            "customLabel": "VDOM_Policy"
        }
    }
]
```
