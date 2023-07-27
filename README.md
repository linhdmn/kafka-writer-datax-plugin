<h1 align="center">
  Kafka Writer Plugin for DataX
</h1>
<h3 align="center">
  Author: Linh Doan
</h3>

<h3 align="center">
  Contributor: Dien Vo 
</h3>
<p align="center">
  <a href="./LICENSE.md">
    <img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="Gatsby is released under the MIT license." />
  </a>
</p>

# Introduction
## DataX Reference
https://github.com/alibaba/DataX

## Use case
DataX only support parse list of User defined type to string so it can not iterate the list and migrate to the target table. In this case, we highly recommend that using queue like kafka to handle logic in application layer

# Job example

```json
{
  "job": {
    "content": [
      {
        "reader": {
          "name": "cassandrareader",
          "parameter": {
            "host": "<cassandra-host>",
            "port": 9042,
            "username": "<username>",
            "password": "<pass>",
            "consitancyLevel": "ONE",
            "useSSL": false,
            "keyspace": "<keyspace>",
            "table": "<your_table>",
            "column": [
              "col1",
              "col2",
              "col3"
            ]
          }
        },
        "writer": {
          "name": "kafkawriter",
          "parameter": {
            "isSilence": true,
            "topic": "<your_topic>",
            "brokers": "<your_broker_addresses>",
            "column": [
              "col1",
              "col2",
              "col3"
            ]
          }
        }
      }
    ],
    "setting": {
      "speed": {
        "channel": "10"
      }
    }
  }
}

```

