# mongodb开启replica sets

## 一、前言

mongodb针对存储高可用方面提供了以下三种方式

1. Master-Slave主从结构
2. Relica Set副本集方式
3. Sharding分片技术

使用mongodb的change stream进行数据监听时需要开启副本集的模式

## 二、配置

1. 可以选择在配置文件进行配置

   ![image-20211215124935146](https://raw.githubusercontent.com/bluechaplin/image-repository/master/Dec.2021/202112151249194.png)

   ```yaml
   replication:
     oplogSizeMB: 50
     replSetName: scrm
   ```

2. 可以在启动程序后面指定参数值

## 三、初始化

1. 进入任意一个节点进行集群的初始化

   ```json
   rs.initiate(
       {
           // 配置中的复制集名称
           "_id": "scrm",
           "members": [
               // 主节点
               {
                   "_id": 0,
                   "host": "127.0.0.1:27017"
               }
               // 子节点
               ......
           ]
       }
   )
   ```

2. 查看集群状态

   ```shell
   rs.status();
   -----------
   {
     set: 'scrm',
     date: 2021-12-15T04:02:56.874Z,
     myState: 1,
     term: Long("1"),
     syncSourceHost: '',
     syncSourceId: -1,
     heartbeatIntervalMillis: Long("2000"),
     majorityVoteCount: 1,
     writeMajorityCount: 1,
     votingMembersCount: 1,
     writableVotingMembersCount: 1,
     optimes: {
       lastCommittedOpTime: { ts: Timestamp({ t: 1639540976, i: 1 }), t: Long("1") },
       lastCommittedWallTime: 2021-12-15T04:02:56.538Z,
       readConcernMajorityOpTime: { ts: Timestamp({ t: 1639540976, i: 1 }), t: Long("1") },
       appliedOpTime: { ts: Timestamp({ t: 1639540976, i: 1 }), t: Long("1") },
       durableOpTime: { ts: Timestamp({ t: 1639540976, i: 1 }), t: Long("1") },
       lastAppliedWallTime: 2021-12-15T04:02:56.538Z,
       lastDurableWallTime: 2021-12-15T04:02:56.538Z
     },
     lastStableRecoveryTimestamp: Timestamp({ t: 1639540966, i: 1 }),
     electionCandidateMetrics: {
       lastElectionReason: 'electionTimeout',
       lastElectionDate: 2021-12-15T03:59:46.494Z,
       electionTerm: Long("1"),
       lastCommittedOpTimeAtElection: { ts: Timestamp({ t: 0, i: 0 }), t: Long("-1") },
       lastSeenOpTimeAtElection: { ts: Timestamp({ t: 1639540786, i: 1 }), t: Long("-1") },
       numVotesNeeded: 1,
       priorityAtElection: 1,
       electionTimeoutMillis: Long("10000"),
       newTermStartDate: 2021-12-15T03:59:46.506Z,
       wMajorityWriteAvailabilityDate: 2021-12-15T03:59:46.517Z
     },
     members: [
       {
         _id: 0,
         name: '127.0.0.1:27017',
         health: 1,
         state: 1,
         stateStr: 'PRIMARY',
         uptime: 406,
         optime: [Object],
         optimeDate: 2021-12-15T04:02:56.000Z,
         syncSourceHost: '',
         syncSourceId: -1,
         infoMessage: '',
         electionTime: Timestamp({ t: 1639540786, i: 2 }),
         electionDate: 2021-12-15T03:59:46.000Z,
         configVersion: 1,
         configTerm: 1,
         self: true,
         lastHeartbeatMessage: ''
       }
     ],
     ok: 1,
     '$clusterTime': {
       clusterTime: Timestamp({ t: 1639540976, i: 1 }),
       signature: {
         hash: Binary(Buffer.from("0000000000000000000000000000000000000000", "hex"), 0),
         keyId: Long("0")
       }
     },
     operationTime: Timestamp({ t: 1639540976, i: 1 })
   }
   ```

