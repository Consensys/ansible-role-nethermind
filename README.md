# Ansible Role: Nethermind

### Description
Ansible role that will install, configure and runs [Nethermind](https://nethermind.io/): a .NET Core Ethereum Execution Layer Client built with performance and flexibility in mind

### Table of Contents
  - [Supported Platforms](#supported-platforms)
  - [Role Variables](#role-variables)
  - [Example Playbook](#example-playbook)
  - [License](#license)
  - [Author Information](#author-information)

### Supported Platforms
```
* MacOS
* Debian
* Ubuntu
* Redhat(CentOS/Fedora)
* Amazon
```

### Role Variables:

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file. The variables that are listed with just their ENV variable name as the description are corresponded by the ansible variable to set if you want to change it from the default which will be inserted into the config at run-time. Please refer to the nethermind [docs](https://docs.nethermind.io/nethermind/ethereum-client/configuration) for more information

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `nethermind_version` | "latest" |  Version of nethermind to install and run. All available versions are listed on the nethermind [solutions](https://github.com/NethermindEth/nethermind/releases) page. Omit the 'v' in the version. e.g. 1.4.0 |
| `nethermind_user` | nethermind | nethermind user |
| `nethermind_group` | nethermind | nethermind group |
| `nethermind_download_url` | ___unset___ | The download tar.gz file used. You can use this if you need to retrieve nethermind from a custom location such as an internal repository. |
| `nethermind_install_dir` | /opt/nethermind | Path to install to  |
| `nethermind_config_dir` | /etc/nethermind | Path for default configuration |
| `nethermind_data_dir` | /opt/nethermind/data | Path for data directory|
| `nethermind_log_dir` | /var/log/nethermind | Path for logs |
| `nethermind_managed_service` | true | Enables a systemd service (or launchd if on Darwin) |
| `nethermind_launchd_dir` | /Library/LaunchAgents | The default launchd directory  |
| `nethermind_systemd_dir` | /etc/systemd/system/ | The default systemd directory |
| `nethermind_systemd_state` | restarted | The default option for the systemd service state |
| `nethermind_config_base` | mainnet | The config base we want to use. Find a list [here](https://github.com/NethermindEth/nethermind/tree/master/src/Nethermind/Nethermind.Runner/configs). Omit the '.cfg' in the name. |
| `nethermind_cmdline_args` | [] | Extra command line args to pass for execution as list. e.g. ["--JsonRpc.EnginePort=8551"] |
| `nethermind_env_vars` | {} | Provide key value environment variables to pass in at run time |
| `nethermind_custom_config` | {} | Provide JSON object to override base config and any other passed values |
| `nethermind_allow_aura_private_chains` | false | NETHERMIND_AURACONFIG_ALLOWAURAPRIVATECHAINS |
| `nethermind_force_sealing` | true | NETHERMIND_AURACONFIG_FORCESEALING |
| `nethermind_minimum_2mln_block_gas_limit_contract` | false | NETHERMIND_AURACONFIG_MINIMUM2MLNGASPERBLOCKWHENUSINGBLOCKGASLIMITCONTRACT |
| `nethermind_tx_priority_config_path` | null | NETHERMIND_AURACONFIG_TXPRIORITYCONFIGFILEPATH |
| `nethermind_tx_priority_contract_address` | null | NETHERMIND_AURACONFIG_TXPRIORITYCONTRACTADDRESS |
| `nethermind_bloom_index` | true | NETHERMIND_BLOOMCONFIG_INDEX |
| `nethermind_bloom_index_level_bucket_sizes` | [4, 8, 8] | NETHERMIND_BLOOMCONFIG_INDEXLEVELBUCKETSIZES |
| `nethermind_bloom_migration` | false | NETHERMIND_BLOOMCONFIG_MIGRATION |
| `nethermind_bloom_migration_statistics` | false | NETHERMIND_BLOOMCONFIG_MIGRATIONSTATISTICS |
| `nethermind_ethstats_contact_email` | hello@nethermind.io | NETHERMIND_ETHSTATSCONFIG_CONTACT |
| `nethermind_ethstats_enabled` | false | NETHERMIND_ETHSTATSCONFIG_ENABLED |
| `nethermind_ethstats_name` | Nethermind | NETHERMIND_ETHSTATSCONFIG_NAME |
| `nethermind_ethstats_secret` | secret | NETHERMIND_ETHSTATSCONFIG_SECRET |
| `nethermind_ethstats_server` | ws://localhost:3000/api | NETHERMIND_ETHSTATSCONFIG_SERVER |
| `nethermind_health_checks_enabled` | false | NETHERMIND_HEALTHCHECKSCONFIG_ENABLED |
| `nethermind_health_checks_max_interval_without_processed_block` | null | NETHERMIND_HEALTHCHECKSCONFIG_MAXINTERVALWITHOUTPROCESSEDBLOCK |
| `nethermind_health_checks_max_interval_without_produced_block` | null | NETHERMIND_HEALTHCHECKSCONFIG_MAXINTERVALWITHOUTPRODUCEDBLOCK |
| `nethermind_health_checks_polling_interval` | 5 | NETHERMIND_HEALTHCHECKSCONFIG_POLLINGINTERVAL |
| `nethermind_health_checks_slug` | /health | NETHERMIND_HEALTHCHECKSCONFIG_SLUG |
| `nethermind_health_checks_ui_enabled` | false | NETHERMIND_HEALTHCHECKSCONFIG_UIENABLED |
| `nethermind_health_checks_webhooks_enabled` | false | NETHERMIND_HEALTHCHECKSCONFIG_WEBHOOKSENABLED |
| `nethermind_health_checks_webhooks_payload` | {"attachments":[{"color":"#FFCC00","pretext":"Health Check Status ","fields":[{"title":"Details","value":"More details available at /healthchecks-ui","short":false},{"title":"Description","value":"[[DESCRIPTIONS]]","short":false}]}]} | NETHERMIND_HEALTHCHECKSCONFIG_WEBHOOKSPAYLOAD |
| `nethermind_health_checks_webhooks_restore_payload` | {"attachments":[{"color":"#36a64f","pretext":"Health Check Status ","fields":[{"title":"Details","value":"More details available at /healthchecks-ui","short":false},{"title":"description","value":"The HealthCheck [[LIVENESS]] is recovered. All is up and running","short":false}]}]} | NETHERMIND_HEALTHCHECKSCONFIG_WEBHOOKSRESTOREPAYLOAD |
| `nethermind_health_checks_webhooks_uri` | null | NETHERMIND_HEALTHCHECKSCONFIG_WEBHOOKSURI |
| `nethermind_hive_enabled` | false | NETHERMIND_HIVECONFIG_ENABLED |
| `nethermind_hive_blocks_dir` | /blocks | NETHERMIND_HIVECONFIG_BLOCKSDIR |
| `nethermind_hive_chain_file` | /chain.rlp | NETHERMIND_HIVECONFIG_CHAINFILE |
| `nethermind_hive_genesis_file_path` | /genesis.json | NETHERMIND_HIVECONFIG_GENESISFILEPATH |
| `nethermind_hive_keys_dir` | /keys | NETHERMIND_HIVECONFIG_KEYSDIR |
| `nethermind_init_auto_dump` | Receipts | NETHERMIND_INITCONFIG_AUTODUMP |
| `nethermind_init_base_db_path` | db | NETHERMIND_INITCONFIG_BASEDBPATH |
| `nethermind_init_chainspec_path` | chainspec/foundation.json | NETHERMIND_INITCONFIG_CHAINSPECPATH |
| `nethermind_init_diagnostic_mode` | None | NETHERMIND_INITCONFIG_DIAGNOSTICMODE |
| `nethermind_init_discovery_enabled` | true | NETHERMIND_INITCONFIG_DISCOVERYENABLED |
| `nethermind_init_enable_unsecured_dev_wallet` | false | NETHERMIND_INITCONFIG_ENABLEUNSECUREDDEVWALLET |
| `nethermind_init_genesis_hash` | null | NETHERMIND_INITCONFIG_GENESISHASH |
| `nethermind_init_hive_chainspec_path` | chainspec/test.json | NETHERMIND_INITCONFIG_HIVECHAINSPECPATH |
| `nethermind_init_mining_enabled` | false | NETHERMIND_INITCONFIG_ISMINING |
| `nethermind_init_dev_wallet_in_memory` | false | NETHERMIND_INITCONFIG_KEEPDEVWALLETINMEMORY |
| `nethermind_init_log_directory` | logs | NETHERMIND_INITCONFIG_LOGDIRECTORY |
| `nethermind_init_log_filename` | "log.txt" | NETHERMIND_INITCONFIG_LOGFILENAME |
| `nethermind_init_log_rules` | null | NETHERMIND_INITCONFIG_LOGRULES |
| `nethermind_init_memory_hint` | null | NETHERMIND_INITCONFIG_MEMORYHINT |
| `nethermind_init_peer_manager_enable` | true | NETHERMIND_INITCONFIG_PEERMANAGERENABLED |
| `nethermind_init_processing_enable` | true | NETHERMIND_INITCONFIG_PROCESSINGENABLED |
| `nethermind_init_receipts_migration` | false | NETHERMIND_INITCONFIG_RECEIPTSMIGRATION |
| `nethermind_init_rpc_db_url` | false | NETHERMIND_INITCONFIG_RPCDBURL |
| `nethermind_init_static_nodes_path` | "Data/static-nodes.json" | NETHERMIND_INITCONFIG_STATICNODESPATH |
| `nethermind_init_store_receipts` | true | NETHERMIND_INITCONFIG_STORERECEIPTS |
| `nethermind_init_websockets_enable` | true | NETHERMIND_INITCONFIG_WEBSOCKETSENABLED |
| `nethermind_jsonrpc_additional_rpc_urls` | http;wss | NETHERMIND_JSONRPCCONFIG_ADDITIONALRPCURLS |
| `nethermind_jsonrpc_buffer_responses` | false | NETHERMIND_JSONRPCCONFIG_BUFFERRESPONSES |
| `nethermind_jsonrpc_calls_filters_file_path` | Data/jsonrpc.filter | NETHERMIND_JSONRPCCONFIG_CALLSFILTERFILEPATH |
| `nethermind_jsonrpc_enabled` | false | NETHERMIND_JSONRPCCONFIG_ENABLED |
| `nethermind_jsonrpc_enabled_modules` | [Eth, Subscribe, Trace, TxPool, Web3, Personal, Proof, Net, Parity, Health, Rpc] | NETHERMIND_JSONRPCCONFIG_ENGINEENABLEDMODULES |
| `nethermind_jsonrpc_engine_host` | 127.0.0.1 | NETHERMIND_JSONRPCCONFIG_ENGINEHOST |
| `nethermind_jsonrpc_engine_port` | null | NETHERMIND_JSONRPCCONFIG_ENGINEPORT |
| `nethermind_jsonrpc_eth_module_concurrent_instances` | __unset__ | NETHERMIND_JSONRPCCONFIG_ETHMODULECONCURRENTINSTANCES |
| `nethermind_jsonrpc_gas_cap` | 100000000 | NETHERMIND_JSONRPCCONFIG_GASCAP |
| `nethermind_jsonrpc_host` | 127.0.0.1 | NETHERMIND_JSONRPCCONFIG_HOST |
| `nethermind_jsonrpc_ipc_unix_domain_socket_path` | __unset__ | NETHERMIND_JSONRPCCONFIG_IPCUNIXDOMAINSOCKETPATH |
| `nethermind_jsonrpc_jwt_secret_path` | keystore/jwt-secret | NETHERMIND_JSONRPCCONFIG_JWTSECRETFILE |
| `nethermind_jsonrpc_max_logged_request_parameters_chars` | null | NETHERMIND_JSONRPCCONFIG_MAXLOGGEDREQUESTPARAMETERSCHARACTERS |
| `nethermind_jsonrpc_max_request_body_size` | 30000000 | NETHERMIND_JSONRPCCONFIG_MAXREQUESTBODYSIZE |
| `nethermind_jsonrpc_methods_logging_filtering` | [engine_newPayloadV1, engine_forkchoiceUpdatedV1] | NETHERMIND_JSONRPCCONFIG_METHODSLOGGINGFILTERING |
| `nethermind_jsonrpc_port` | 8545 | NETHERMIND_JSONRPCCONFIG_PORT |
| `nethermind_jsonrpc_port_interval_seconds` | 300 | NETHERMIND_JSONRPCCONFIG_REPORTINTERVALSECONDS |
| `nethermind_jsonrpc_rpc_recorder_base_path` | "logs/rpc.{counter}.txt" | NETHERMIND_JSONRPCCONFIG_RPCRECORDERBASEFILEPATH |
| `nethermind_jsonrpc_rpc_recorder_state` | None | NETHERMIND_JSONRPCCONFIG_RPCRECORDERSTATE |
| `nethermind_jsonrpc_timeout` | 20000 | NETHERMIND_JSONRPCCONFIG_TIMEOUT |
| `nethermind_jsonrpc_websockets_port` | 8545 | NETHERMIND_JSONRPCCONFIG_WEBSOCKETSPORT |
| `nethermind_keystore_block_author_account` | None | NETHERMIND_KEYSTORECONFIG_BLOCKAUTHORACCOUNT |
| `nethermind_keystore_cipher` | aes-128-ctr | NETHERMIND_KEYSTORECONFIG_CIPHER |
| `nethermind_keystore_enode_account` | None | NETHERMIND_KEYSTORECONFIG_ENODEACCOUNT |
| `nethermind_keystore_enode_key_file` | None | NETHERMIND_KEYSTORECONFIG_ENODEKEYFILE |
| `nethermind_keystore_iv_size` | 16 | NETHERMIND_KEYSTORECONFIG_IVSIZE |
| `nethermind_keystore_kdf` | scrypt | NETHERMIND_KEYSTORECONFIG_KDF |
| `nethermind_keystore_kdf_params_dklen` | 32 | NETHERMIND_KEYSTORECONFIG_KDFPARAMSDKLEN |
| `nethermind_keystore_kdf_params_n` | 262144 | NETHERMIND_KEYSTORECONFIG_KDFPARAMSN |
| `nethermind_keystore_kdf_params_p` | 1 | NETHERMIND_KEYSTORECONFIG_KDFPARAMSP |
| `nethermind_keystore_kdf_params_r` | 8 | NETHERMIND_KEYSTORECONFIG_KDFPARAMSR |
| `nethermind_keystore_kdf_params_saltlen` | 32 | NETHERMIND_KEYSTORECONFIG_KDFPARAMSSALTLEN |
| `nethermind_keystore_directory` | keystore | NETHERMIND_KEYSTORECONFIG_KEYSTOREDIRECTORY |
| `nethermind_keystore_encoding` | UTF-8 | NETHERMIND_KEYSTORECONFIG_KEYSTOREENCODING |
| `nethermind_keystore_password_files` | [] | NETHERMIND_KEYSTORECONFIG_PASSWORDFILES |
| `nethermind_keystore_passwords` | [] | NETHERMIND_KEYSTORECONFIG_PASSWORDS |
| `nethermind_keystore_symmetric_encryptor_block_size` | 128 | NETHERMIND_KEYSTORECONFIG_SYMMETRICENCRYPTERBLOCKSIZE |
| `nethermind_keystore_symmetric_encryptor_key_size` | 128 | NETHERMIND_KEYSTORECONFIG_SYMMETRICENCRYPTERKEYSIZE |
| `nethermind_keystore_test_node_key` | null | NETHERMIND_KEYSTORECONFIG_TESTNODEKEY |
| `nethermind_keystore_unlock_accounts` | [] | NETHERMIND_KEYSTORECONFIG_UNLOCKACCOUNTS |
| `nethermind_merge_builder_relay_url` | null | NETHERMIND_MERGECONFIG_BUILDERRELAYURL |
| `nethermind_merge_enabled` | false | NETHERMIND_MERGECONFIG_ENABLED |
| `nethermind_merge_final_total_difficulty` | null | NETHERMIND_MERGECONFIG_FINALTOTALDIFFICULTY |
| `nethermind_merge_seconds_per_slot` | 12 | NETHERMIND_MERGECONFIG_SECONDSPERSLOT |
| `nethermind_merge_terminal_block_hash` | null | NETHERMIND_MERGECONFIG_TERMINALBLOCKHASH |
| `nethermind_merge_terminal_block_number` | null | NETHERMIND_MERGECONFIG_TERMINALBLOCKNUMBER |
| `nethermind_merge_terminal_block_difficulty` | null | NETHERMIND_MERGECONFIG_TERMINALTOTALDIFFICULTY |
| `nethermind_metrics_enabled` | false | NETHERMIND_METRICSCONFIG_ENABLED |
| `nethermind_metrics_expose_port` | null | NETHERMIND_METRICSCONFIG_EXPOSEPORT |
| `nethermind_metrics_interval_seconds` | 5 | NETHERMIND_METRICSCONFIG_INTERVALSECONDS |
| `nethermind_metrics_node_name` | Nethermind | NETHERMIND_METRICSCONFIG_NODENAME |
| `nethermind_metrics_push_gateway_url` | "http://localhost:9091/metrics" | NETHERMIND_METRICSCONFIG_PUSHGATEWAYURL |
| `nethermind_mining_enabled` | false | NETHERMIND_MININGCONFIG_ENABLED |
| `nethermind_mining_min_gas_price` | 1 | NETHERMIND_MININGCONFIG_MINGASPRICE |
| `nethermind_mining_randomized_blocks` | false | NETHERMIND_MININGCONFIG_RANDOMIZEDBLOCKS |
| `nethermind_mining_target_block_gas_limit` | null | NETHERMIND_MININGCONFIG_TARGETBLOCKGASLIMIT |
| `nethermind_network_max_active_peers_max_count` | 50 | NETHERMIND_NETWORKCONFIG_ACTIVEPEERSMAXCOUNT |
| `nethermind_network_bootnodes` | [] | NETHERMIND_NETWORKCONFIG_BOOTNODES |
| `nethermind_network_diag_tracer_enabled` | false | NETHERMIND_NETWORKCONFIG_DIAGTRACERENABLED |
| `nethermind_network_discovery_port` | 30303 | NETHERMIND_NETWORKCONFIG_DISCOVERYPORT |
| `netermind_network_external_ip` | null | NETHERMIND_NETWORKCONFIG_EXTERNALIP |
| `nethermind_network_local_ip` | null | NETHERMIND_NETWORKCONFIG_LOCALIP |
| `nethermind_network_max_active_peers` | 50 | NETHERMIND_NETWORKCONFIG_MAXACTIVEPEERS |
| `nethermind_network_netty_arena_order` | 11 | NETHERMIND_NETWORKCONFIG_NETTYARENAORDER |
| `nethermind_network_only_static_peers` | false | NETHERMIND_NETWORKCONFIG_ONLYSTATICPEERS |
| `nethermind_network_p2p_port` | 30303 | NETHERMIND_NETWORKCONFIG_P2PPORT |
| `nethermind_network_priority_peers_max_count` | 0 | NETHERMIND_NETWORKCONFIG_PRIORITYPEERSMAXCOUNT |
| `nethermind_network_static_peers` | null | NETHERMIND_NETWORKCONFIG_STATICPEERS |
| `nethermind_pruning_cache_mb` | 1024 | NETHERMIND_PRUNINGCONFIG_CACHEMB |
| `nethermind_pruning_full_completion_behavior` | None | NETHERMIND_PRUNINGCONFIG_FULLPRUNINGCOMPLETIONBEHAVIOR |
| `nethermind_pruning_full_max_degree_parallelism` | 0 | NETHERMIND_PRUNINGCONFIG_FULLPRUNINGMAXDEGREEOFPARALLELISM |
| `nethermind_pruning_full_min_delay_hours` | 240 | NETHERMIND_PRUNINGCONFIG_FULLPRUNINGMINIMUMDELAYHOURS |
| `nethermind_pruning_full_threshold_mb` | 256000 | NETHERMIND_PRUNINGCONFIG_FULLPRUNINGTHRESHOLDMB |
| `nethermind_pruning_full_trigger` | Manual | NETHERMIND_PRUNINGCONFIG_FULLPRUNINGTRIGGER |
| `nethermind_pruning_mode` | Hybrid | NETHERMIND_PRUNINGCONFIG_MODE |
| `nethermind_pruning_persistence_mode` | 8192 | NETHERMIND_PRUNINGCONFIG_PERSISTENCEINTERVAL |
| `nethermind_seq_api_key` | null | NETHERMIND_SEQCONFIG_APIKEY |
| `nethermind_seq_min_level` | Off | NETHERMIND_SEQCONFIG_MINLEVEL |
| `nethermind_seq_server_url` | "http://localhost:5341" | NETHERMIND_SEQCONFIG_SERVERURL |
| `nethermind_sync_ancient_bodies_barrier` | 0 | NETHERMIND_SYNCCONFIG_ANCIENTBODIESBARRIER |
| `nethermind_sync_ancient_receipts_barrier` | 0 | NETHERMIND_SYNCCONFIG_ANCIENTRECEIPTSBARRIER |
| `nethermind_sync_download_bodies_fast_sync` | true | NETHERMIND_SYNCCONFIG_DOWNLOADBODIESINFASTSYNC |
| `nethermind_sync_download_headers_fast_sync` | true | NETHERMIND_SYNCCONFIG_DOWNLOADHEADERSINFASTSYNC |
| `nethermind_sync_download_receipts_fast_sync` | true | NETHERMIND_SYNCCONFIG_DOWNLOADRECEIPTSINFASTSYNC |
| `nethermind_sync_fast_blocks` | false | NETHERMIND_SYNCCONFIG_FASTBLOCKS |
| `nethermind_sync_fast_sync` | false | NETHERMIND_SYNCCONFIG_FASTSYNC |
| `nethermind_sync_fast_sync_catch_up_height_delta` | 8192 | NETHERMIND_SYNCCONFIG_FASTSYNCCATCHUPHEIGHTDELTA |
| `nethermind_sync_fix_receipts` | false | NETHERMIND_SYNCCONFIG_FIXRECEIPTS |
| `nethermind_sync_networking_enabled` | true | NETHERMIND_SYNCCONFIG_NETWORKINGENABLED |
| `nethermind_sync_pivot_hash` | null | NETHERMIND_SYNCCONFIG_PIVOTHASH |
| `nethermind_sync_pivot_number` | null | NETHERMIND_SYNCCONFIG_PIVOTNUMBER |
| `nethermind_sync_pivot_total_difficulty` | null | NETHERMIND_SYNCCONFIG_PIVOTTOTALDIFFICULTY |
| `nethermind_sync_snap_sync` | false | NETHERMIND_SYNCCONFIG_SNAPSYNC |
| `nethermind_sync_synchronization_enabled` | true | NETHERMIND_SYNCCONFIG_SYNCHRONIZATIONENABLED |
| `nethermind_sync_use_geth_limits_fast_blocks` | true | NETHERMIND_SYNCCONFIG_USEGETHLIMITSINFASTBLOCKS |
| `nethermind_sync_witness_protocol_enabled` | false | NETHERMIND_SYNCCONFIG_WITNESSPROTOCOLENABLED |
| `nethermind_txpool_gas_limit` | null | NETHERMIND_TXPOOLCONFIG_GASLIMIT |
| `nethermind_txpool_hash_cache_size` | null | NETHERMIND_TXPOOLCONFIG_HASHCACHESIZE |
| `nethermind_txpool_hash_cache_size` | 524288 | NETHERMIND_TXPOOLCONFIG_HASHCACHESIZE |
| `nethermind_txpool_peer_notification_threshold` | 5 | NETHERMIND_TXPOOLCONFIG_PEERNOTIFICATIONTHRESHOLD |
| `nethermind_txpool_size` | 2048 | NETHERMIND_TXPOOLCONFIG_SIZE |
| `nethermind_wallet_dev_accounts` | 10 | NETHERMIND_WALLETCONFIG_DEVACCOUNTS |

### Example Playbook

1. Default setup:
Install the role from galaxy
```
ansible-galaxy install consensys.nethermind
```

Create a requirements.yml with the following:
Replace `x.y.z` below with the version you would like to use from the nethermind [solutions](https://github.com/NethermindEth/nethermind/releases) page
```
---
- hosts: localhost
  connection: local
  force_handlers: True

  roles:
  - role: consensys.nethermind
    vars:
      nethermind_version: x.y.z

```

Run with ansible-playbook:
```
ansible-playbook -v /path/to/requirements.yml
```


1. Install via github

```
ansible-galaxy install git+https://github.com/ConsenSys/ansible-role-nethermind.git
```

Create a requirements.yml with the following:
Replace `x.y.z` below with the version you would like to use from the nethermind [solutions](https://github.com/NethermindEth/nethermind/releases) page
```
---
- hosts: localhost
  connection: local
  force_handlers: True

  roles:
  - role: ansible-role-nethermind
    vars:
      nethermind_version: x.y.z

```

Run with ansible-playbook:
```
ansible-playbook -v /path/to/requirements.yml
```


### License

Apache


### Author Information

Consensys, 2022