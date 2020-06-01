# kibkit
Pulls CSV from Kibana visualization

## Lists dashboards
```
./kibkit -u USER:PSWD -H HOST -fd

73a133b0-7325-11ea-b36a-87ca4a6a28f0,dev_session
c3e418b0-7f23-11ea-9a41-e372321608d2,dev_session-requirements
ee00ecc0-8092-11ea-9a41-e372321608d2,req_sessions
6fd956d0-84ab-11ea-9a41-e372321608d2,beta_session-requirements
```

## Then visualizations within a dashboard
```
./kibkit -u USER:PSWD -H HOST -fd -ld 6fd956d0-84ab-11ea-9a41-e372321608d2

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

## Hence, CSV a visualization
```
./kibkit -u USER:PSWD -H HOST -fd -sv beta_session-ipunique,6fd956d0-84ab-11ea-9a41-e372321608d2
```
