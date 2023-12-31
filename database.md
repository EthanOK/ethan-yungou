## DB Name: aggregator_ethan
```
CREATE DATABASE `aggregator_ethan` /*!40100 DEFAULT CHARACTER SET utf8 */;
```

-- aggregator_ethan.cross_chain_log definition


```

CREATE TABLE `cross_chain_log` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `address` varchar(100) NOT NULL,
  `amount` varchar(100) NOT NULL,
  `fromChainId` varchar(100) NOT NULL,
  `toChainId` varchar(100) NOT NULL,
  `ccType` varchar(100) NOT NULL COMMENT '跨链类型\r\n1：MINT\r\n2：BURN',
  `createTime` varchar(100) NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=41 DEFAULT CHARSET=utf8mb4 COMMENT='跨链用户表';

```


-- aggregator_ethan.cross_chain_user definition


```

CREATE TABLE `cross_chain_user` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `chainId` varchar(100) NOT NULL,
  `account` varchar(100) NOT NULL,
  `balance` varchar(100) DEFAULT NULL,
  `updateTime` varchar(100) NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `cross_chain_user_UN` (`chainId`,`account`)
) ENGINE=InnoDB AUTO_INCREMENT=10 DEFAULT CHARSET=utf8mb4 COMMENT='跨链用户表';

```

-- aggregator_ethan.event_participate_lb definition

```

CREATE TABLE `event_participate_lb` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `account` varchar(100) CHARACTER SET utf16le NOT NULL,
  `issueId` bigint(20) unsigned NOT NULL,
  `count` bigint(20) NOT NULL,
  `numberCurrent` bigint(20) unsigned NOT NULL,
  `timeParticipate` bigint(20) unsigned NOT NULL,
  `transactionHash` varchar(100) CHARACTER SET utf16le NOT NULL COMMENT 'keccak256( abi.encodePacked(issueId,numberCurrent))',
  `blockNumber` bigint(20) unsigned NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `event_participate_lb_UN` (`transactionHash`),
  KEY `event_participate_lb_blockNumber_IDX` (`blockNumber`) USING BTREE
) ENGINE=InnoDB AUTO_INCREMENT=49 DEFAULT CHARSET=utf8mb4;

```

-- aggregator_ethan.event_staking_ygme definition

```
CREATE TABLE `event_staking_ygme` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `account` varchar(100) NOT NULL,
  `nftContract` varchar(100) NOT NULL,
  `tokenId` varchar(100) NOT NULL,
  `startTime` int(11) NOT NULL,
  `endTime` int(11) NOT NULL,
  `pledgeType` int(11) NOT NULL COMMENT '1:staking\r\n\r\n2:unstake',
  `blockNumber` int(11) NOT NULL,
  `transactionHash` varchar(100) NOT NULL,
  PRIMARY KEY (`id`),
  KEY `event_staking_ygme_account_IDX` (`account`) USING BTREE
) ENGINE=InnoDB AUTO_INCREMENT=4294 DEFAULT CHARSET=utf8mb4;

```

-- aggregator_ethan.event_transfer_erc20 definition
```

CREATE TABLE `event_transfer_erc20` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `token` varchar(100) NOT NULL,
  `fromAddress` varchar(100) NOT NULL,
  `toAddress` varchar(100) NOT NULL,
  `value` varchar(100) NOT NULL,
  `blockNumber` varchar(100) NOT NULL,
  `transactionHash` varchar(100) NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `event_transfer_erc20_UN` (`token`,`fromAddress`,`toAddress`,`value`,`blockNumber`,`transactionHash`)
) ENGINE=InnoDB AUTO_INCREMENT=413 DEFAULT CHARSET=utf8mb4;
```

-- aggregator_ethan.event_transfer_erc721 definition

```

CREATE TABLE `event_transfer_erc721` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `token` varchar(100) NOT NULL,
  `tokenId` varchar(100) NOT NULL,
  `fromAddress` varchar(100) NOT NULL,
  `toAddress` varchar(100) NOT NULL,
  `blockNumber` varchar(100) NOT NULL,
  `chainId` int(10) unsigned DEFAULT NULL,
  `transactionHash` varchar(100) NOT NULL,
  `encodeDataHash` varchar(100) DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `event_transfer_erc721_UN` (`token`,`tokenId`,`fromAddress`,`toAddress`,`blockNumber`,`transactionHash`),
  KEY `event_transfer_erc721_token_IDX` (`token`,`tokenId`) USING BTREE
) ENGINE=InnoDB AUTO_INCREMENT=80934 DEFAULT CHARSET=utf8mb4;
```

-- aggregator_ethan.event_transfer_erc721_bsc definition

```

CREATE TABLE `event_transfer_erc721_bsc` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `token` varchar(100) NOT NULL,
  `tokenId` varchar(100) NOT NULL,
  `fromAddress` varchar(100) NOT NULL,
  `toAddress` varchar(100) NOT NULL,
  `blockNumber` varchar(100) NOT NULL,
  `transactionHash` varchar(100) NOT NULL,
  `encodeDataHash` varchar(100) NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `event_transfer_erc721_bsc_UN` (`token`,`tokenId`,`fromAddress`,`toAddress`,`blockNumber`,`transactionHash`),
  KEY `event_transfer_erc721_token_IDX` (`token`,`tokenId`) USING BTREE
) ENGINE=InnoDB AUTO_INCREMENT=44881 DEFAULT CHARSET=utf8mb4;
```

-- aggregator_ethan.event_withdraw_ygdiv definition
```
CREATE TABLE `event_withdraw_ygdiv` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `orderId` varchar(100) CHARACTER SET utf16 COLLATE utf16_croatian_ci NOT NULL,
  `coinAddress` varchar(100) CHARACTER SET utf16le NOT NULL,
  `account` varchar(100) CHARACTER SET utf16le NOT NULL,
  `amount` varchar(100) CHARACTER SET utf16 COLLATE utf16_croatian_ci NOT NULL,
  `blockNumber` bigint(20) unsigned NOT NULL,
  `transactionHash` varchar(100) CHARACTER SET utf16 COLLATE utf16_croatian_ci NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `event_withdraw_ygdiv_UN` (`orderId`)
) ENGINE=InnoDB AUTO_INCREMENT=27 DEFAULT CHARSET=utf8mb4 COMMENT='YunGouDividend\r\nhttps://etherscan.io/address/0x4643b06debe49fce229a77ebc9e7c5c036b2cedc';
```

-- aggregator_ethan.`system` definition
```
CREATE TABLE `system` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `key` varchar(100) CHARACTER SET utf8 DEFAULT NULL,
  `value` varchar(100) CHARACTER SET utf8 DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=7 DEFAULT CHARSET=utf8mb4;
```

-- aggregator_ethan.yg_user_token definition
```
CREATE TABLE `yg_user_token` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `user_address` varchar(55) NOT NULL DEFAULT '' COMMENT '用户钱包地址',
  `user_token` text NOT NULL COMMENT '用户登录token',
  `deleted` tinyint(1) NOT NULL DEFAULT '0' COMMENT '逻辑删除',
  `create_time` int(11) NOT NULL DEFAULT '0' COMMENT '创建时间',
  `update_time` int(11) NOT NULL DEFAULT '0' COMMENT '更新时间',
  `chain_id` int(11) DEFAULT NULL COMMENT 'chain id',
  PRIMARY KEY (`id`) USING BTREE,
  KEY `user_address` (`user_address`) USING BTREE,
  KEY `deleted` (`deleted`) USING BTREE
) ENGINE=InnoDB AUTO_INCREMENT=119 DEFAULT CHARSET=utf8mb4 ROW_FORMAT=DYNAMIC COMMENT='用户登录token表';
```