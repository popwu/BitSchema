# BitSchema
BitSchema Protocol

一、协议概述
w协议是基于分层结构的轻量级数据传输协议，采用Apache Avro实现二进制序列化，
支持公钥基础设施（PKI）的数据签名验证机制。
协议采用双层嵌套设计，外层为传输信封协议，内层为业务数据子协议。

协议内容
{
协议格式:二进制bitcoin公钥
data:二层二进制数据
发布者公钥:二进制bitcoin公钥
签名:二进制签名
}

// 主协议Schema
{
  "type": "record",
  "name": "BitcoinEnvelope",
  "fields": [
    {"name": "protocol", "type": "bytes",  "doc": "协议版本标识（BTC/v1）"},
    {"name": "data",            "type": "bytes",   "doc": "子协议序列化数据"},
    {"name": "from_pubkey",   "type": "bytes",   "doc": "压缩格式SEC公钥"},
    {"name": "data_signature",   "type": "bytes",   "doc": "比特币标准签名"}
  ]
}

data:再又是子协议的Schema
