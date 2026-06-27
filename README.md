# icqq-rust-onebot

> [!WARNING] 温馨提示
> 请勿相信docs和readme中关于本项目的任何信息，除非你确认它们是最新的。
> 目前项目处于高速迭代阶段，任何一个环境都可能出现问题，请务必在使用前自行测试。

基于 Rust 实现的 QQ OneBot 11 协议端。功能上基本是 **go-cqhttp 的超集**，并**独有** QQ 频道、漫游表情、好友分组、设备型号、企点等能力。

- **100+ API**：消息收发、群管理、合并转发、媒体上传、好友/群请求处理、QQ 频道等。
- **多种传输**：HTTP、正向 WebSocket、反向 WebSocket。
- **跨平台**：Linux / Windows / macOS（x64 与 arm64）。

## 下载

前往 [Releases](https://github.com/icqqjs/icqq-rust-onebot-releases/releases) 下载对应平台的预编译二进制：

| 平台 | 文件名 |
|------|--------|
| Linux x64 | `icqq-rs-linux.tar.gz` |
| Linux arm64 | `icqq-rs-linux-arm64.tar.gz` |
| Windows x64 | `icqq-rs-windows.tar.gz` |
| Windows arm64 | `icqq-rs-windows-arm64.tar.gz` |
| macOS arm64 | `icqq-rs-macos.tar.gz` |
| macOS x64 | `icqq-rs-macos-x64.tar.gz` |

## 文档

文档站点：<https://icqqjs.zhin.dev>

---

## API 覆盖对照（vs go-cqhttp / NapCat / LLOneBot）

> ✅ 已实现 · ◐ 部分/别名 · — 未实现。每个 API 单独一行。参考版本：go-cqhttp、NapCat、LLOneBot 7.0.0。
> 本仓基本是 **go-cqhttp 超集**，并**独有** QQ 频道（列表/成员/频道/发消息）/ 漫游表情 / 好友分组 / 设备型号 / 企点等。

### 消息收发 / 历史

| 动作 | 本仓 | gocq | NapCat | LLOneBot |
| ---- |:--:|:--:|:--:|:--:|
| send_private_msg | ✅ | ✅ | ✅ | ✅ |
| send_group_msg | ✅ | ✅ | ✅ | ✅ |
| send_msg | ✅ | ✅ | ✅ | ✅ |
| send_forward_msg | ✅ | ✅ | ✅ | ✅ |
| send_group_forward_msg | ✅ | ✅ | ✅ | ✅ |
| send_private_forward_msg | ✅ | ✅ | ✅ | ✅ |
| send_guild_channel_msg | ✅ | ✅ | — | — |
| get_guild_msg | — | ✅ | — | — |
| get_msg | ✅ | ✅ | ✅ | ✅ |
| get_forward_msg | ✅ | ✅ | ✅ | ✅ |
| delete_msg | ✅ | ✅ | ✅ | ✅ |
| get_group_msg_history | ✅ | ✅ | ✅ | ✅ |
| get_friend_msg_history | ✅ | — | ✅ | ✅ |
| mark_msg_as_read | ✅ | ✅ | ✅ | ✅ |
| mark_private_msg_as_read | ✅ | — | ✅ | — |
| mark_group_msg_as_read | ✅ | — | ✅ | — |
| forward_friend_single_msg | ✅ | — | ✅ | ✅ |
| forward_group_single_msg | ✅ | — | ✅ | ✅ |
| set_msg_emoji_like | ✅ | — | ✅ | ✅ |
| unset_msg_emoji_like | ✅ | — | — | ✅ |
| handle_quick_operation | ✅ | ✅ | ✅ | ✅ |
| get_word_slices | ✅ | ✅ | — | — |
| voice_msg_to_text | — | — | — | ✅ |
| get_recommend_face | — | — | — | ✅ |
| send_group_ai_record | — | — | ✅ | ✅ |
| get_ai_characters | — | — | ✅ | ✅ |
| get_ai_record | — | — | ✅ | — |

### 戳一戳（poke）

| 动作 | 本仓 | gocq | NapCat | LLOneBot |
| ---- |:--:|:--:|:--:|:--:|
| send_poke | ✅ | — | ✅ | ✅ |
| group_poke | ✅ | — | ✅ | ✅ |
| friend_poke | ✅ | — | ✅ | ✅ |

### 群管理

| 动作 | 本仓 | gocq | NapCat | LLOneBot |
| ---- |:--:|:--:|:--:|:--:|
| set_group_card | ✅ | ✅ | ✅ | ✅ |
| set_group_kick | ✅ | ✅ | ✅ | ✅ |
| set_group_ban | ✅ | ✅ | ✅ | ✅ |
| set_group_whole_ban | ✅ | ✅ | ✅ | ✅ |
| set_group_admin | ✅ | ✅ | ✅ | ✅ |
| set_group_name | ✅ | ✅ | ✅ | ✅ |
| set_group_leave | ✅ | ✅ | ✅ | ✅ |
| set_group_special_title | ✅ | ✅ | ✅ | ✅ |
| set_group_anonymous | ✅ | ✅ | — | — |
| set_group_anonymous_ban | ✅ | ✅ | — | — |
| set_group_msg_mask | ✅ | — | — | ✅ |
| get_group_msg_mask | ✅ | — | — | — |
| set_group_portrait | ✅ | ✅ | ✅ | ✅ |
| set_group_remark | ✅ | — | ✅ | ✅ |
| set_group_kick_members | ✅ | — | ✅ | — |
| batch_delete_group_member | — | — | — | ✅ |
| get_group_shut_list | ✅ | — | ✅ | ✅ |
| set_group_add_option | — | — | ✅ | — |
| set_group_robot_add_option | — | — | ✅ | — |
| set_group_search | — | — | ✅ | — |
| set_group_sign | — | — | ✅ | — |
| set_group_todo | — | — | ✅ | — |
| get_group_ignored_notifies | — | — | ✅ | — |
| get_group_ignore_add_request | — | — | ✅ | ✅ |

### 群信息

| 动作 | 本仓 | gocq | NapCat | LLOneBot |
| ---- |:--:|:--:|:--:|:--:|
| get_group_info | ✅ | ✅ | ✅ | ✅ |
| get_group_list | ✅ | ✅ | ✅ | ✅ |
| get_group_member_info | ✅ | ✅ | ✅ | ✅ |
| get_group_member_list | ✅ | ✅ | ✅ | ✅ |
| get_group_honor_info | ✅ | ✅ | ✅ | ✅ |
| get_group_at_all_remain | ✅ | ✅ | ✅ | ✅ |
| get_group_system_msg | ✅ | ✅ | ✅ | ✅ |
| get_group_info_ex | — | — | ✅ | — |
| get_group_detail_info | — | — | ✅ | — |

### 群文件

| 动作 | 本仓 | gocq | NapCat | LLOneBot |
| ---- |:--:|:--:|:--:|:--:|
| get_group_file_system_info | ✅ | ✅ | ✅ | ✅ |
| get_group_root_files | ✅ | ✅ | ✅ | ✅ |
| get_group_files_by_folder | ✅ | ✅ | ✅ | ✅ |
| get_group_file_url | ✅ | ✅ | ✅ | ✅ |
| delete_group_file | ✅ | ✅ | ✅ | ✅ |
| create_group_file_folder | ✅ | ✅ | ✅ | ✅ |
| delete_group_folder | ✅ | ✅ | ✅ | ✅ |
| upload_group_file | ✅ | ✅ | ✅ | ✅ |
| upload_private_file | ✅ | ✅ | ✅ | ✅ |
| move_group_file | ✅ | — | ✅ | ✅ |
| rename_group_file | ✅ | — | ✅ | ✅ |
| rename_group_file_folder | ✅ | — | — | ✅ |
| get_private_file_url | ✅ | — | ✅ | ✅ |
| trans_group_file | — | — | ✅ | — |
| set_group_file_forever | — | — | — | ✅ |
| get_file | — | — | ✅ | ✅ |

### 群通知 / 精华 / 点赞

| 动作 | 本仓 | gocq | NapCat | LLOneBot |
| ---- |:--:|:--:|:--:|:--:|
| set_essence_msg | ✅ | ✅ | ✅ | ✅ |
| delete_essence_msg | ✅ | ✅ | ✅ | ✅ |
| get_essence_msg_list | ✅ | ✅ | ✅ | — |
| send_group_notice | ✅ | ✅ | ✅ | ✅ |
| _send_group_notice | ✅ | ✅ | ✅ | ✅ |
| get_group_notice | ✅ | ✅ | ✅ | — |
| _get_group_notice | ✅ | ✅ | — | ✅ |
| _del_group_notice | ✅ | ✅ | ✅ | ✅ |
| send_group_sign | ✅ | ✅ | ✅ | ✅ |
| send_like | ✅ | — | ✅ | ✅ |

### 请求处理

| 动作 | 本仓 | gocq | NapCat | LLOneBot |
| ---- |:--:|:--:|:--:|:--:|
| set_friend_add_request | ✅ | ✅ | ✅ | ✅ |
| set_group_add_request | ✅ | ✅ | ✅ | ✅ |
| get_doubt_friends_add_request | — | — | ✅ | ✅ |
| set_doubt_friends_add_request | — | — | ✅ | ✅ |

### 好友 / 陌生人 / 资料

| 动作 | 本仓 | gocq | NapCat | LLOneBot |
| ---- |:--:|:--:|:--:|:--:|
| get_friend_list | ✅ | ✅ | ✅ | ✅ |
| delete_friend | ✅ | ✅ | ✅ | ✅ |
| get_stranger_info | ✅ | ✅ | ✅ | ✅ |
| get_unidirectional_friend_list | ✅ | ✅ | ✅ | — |
| delete_unidirectional_friend | ✅ | ✅ | — | — |
| add_friend_category | ✅ | — | — | — |
| delete_friend_category | ✅ | — | — | — |
| rename_friend_category | ✅ | — | — | — |
| set_friend_remark | ✅ | — | ✅ | ✅ |
| set_friend_category | ✅ | — | — | ✅ |
| set_friend_msg_mask | ✅ | — | — | — |
| get_friend_msg_mask | ✅ | — | — | — |
| get_friends_with_category | ✅ | — | ✅ | ✅ |
| get_recent_contact | — | — | ✅ | — |
| get_qq_avatar | ✅ | — | — | ✅ |
| get_profile_like | — | — | ✅ | ✅ |
| get_profile_like_me | — | — | — | ✅ |
| fetch_emoji_like | — | — | ✅ | ✅ |
| fetch_custom_face | — | — | ✅ | ✅ |
| set_input_status | — | — | ✅ | ✅ |
| get_user_status | ✅ | — | ✅ | — |

### 账号 / 资料 / 状态

| 动作 | 本仓 | gocq | NapCat | LLOneBot |
| ---- |:--:|:--:|:--:|:--:|
| get_login_info | ✅ | ✅ | ✅ | ✅ |
| set_qq_profile | ✅ | ✅ | ✅ | ✅ |
| set_qq_avatar | ✅ | — | ✅ | ✅ |
| set_self_longnick | ✅ | — | ✅ | — |
| set_online_status | ✅ | — | ✅ | ✅ |
| set_diy_online_status | — | — | ✅ | — |
| get_roaming_stamp | ✅ | — | — | — |
| delete_stamp | ✅ | — | — | — |
| get_clientkey | ✅ | — | ✅ | — |
| get_robot_uin_range | — | — | ✅ | ✅ |

### 媒体 / 工具

| 动作 | 本仓 | gocq | NapCat | LLOneBot |
| ---- |:--:|:--:|:--:|:--:|
| ocr_image | ✅ | ✅ | ✅ | ✅ |
| ocr | ✅ | — | — | — |
| get_image | ✅ | ✅ | ✅ | ✅ |
| get_record | ✅ | — | ✅ | ✅ |
| get_rkey | ✅ | — | ✅ | ✅ |
| can_send_image | ✅ | ✅ | ✅ | ✅ |
| can_send_record | ✅ | ✅ | ✅ | ✅ |
| check_url_safely | ✅ | ✅ | ✅ | — |
| download_file | ✅ | ✅ | ✅ | ✅ |
| translate_en2zh | — | — | ✅ | — |
| get_mini_app_ark | — | — | ✅ | — |
| send_ark_share | — | — | ✅ | — |
| send_group_ark_share | — | — | ✅ | — |
| scan_qrcode | — | — | — | ✅ |

### 元信息 / 运维 / 凭据 / 设备

| 动作 | 本仓 | gocq | NapCat | LLOneBot |
| ---- |:--:|:--:|:--:|:--:|
| get_status | ✅ | ✅ | ✅ | ✅ |
| get_version_info | ✅ | ✅ | ✅ | ✅ |
| get_online_clients | ✅ | ✅ | ✅ | — |
| get_supported_actions | ✅ | ✅ | — | — |
| set_restart | ✅ | — | ✅ | ✅ |
| clean_cache | ✅ | — | ✅ | ✅ |
| reload_event_filter | ✅ | ✅ | — | — |
| get_cookies | ✅ | ✅ | ✅ | ✅ |
| get_credentials | ✅ | ✅ | ✅ | ✅ |
| get_csrf_token | ✅ | ✅ | ✅ | ✅ |
| get_model_show | ✅ | ✅ | — | — |
| _get_model_show | ✅ | ✅ | — | — |
| set_model_show | ✅ | ✅ | — | — |
| _set_model_show | ✅ | ✅ | — | — |
| qidian_get_account_info | ✅ | ✅ | — | — |

### QQ 频道（Guild，本仓独有大块）

| 动作 | 本仓 | gocq | NapCat | LLOneBot |
| ---- |:--:|:--:|:--:|:--:|
| get_guild_service_profile | ✅ | ✅ | ◐ | — |
| get_guild_list | ✅ | ✅ | ◐ | — |
| get_guild_member_list | ✅ | ✅ | — | — |
| get_guild_channel_list | ✅ | ✅ | — | — |
| get_guild_member_profile | — | ✅ | — | — |
| get_guild_meta_by_guest | — | ✅ | — | — |
| get_guild_roles | — | ✅ | — | — |
| create_guild_role | — | ✅ | — | — |
| delete_guild_role | — | ✅ | — | — |
| update_guild_role | — | ✅ | — | — |
| set_guild_member_role | — | ✅ | — | — |
| get_topic_channel_feeds | — | ✅ | — | — |

### NapCat 私有扩展（强绑定 NTQQ 注入，本仓不计划支持）

| 动作 | 本仓 | gocq | NapCat | LLOneBot |
| ---- |:--:|:--:|:--:|:--:|
| send_packet | — | — | ✅ | ✅ |
| get_packet_status / nc_get_packet_status | — | — | ✅ | — |
| nc_get_rkey / get_rkey_server | — | — | ✅ | — |
| nc_get_user_status | — | — | ✅ | — |
| get_emoji_likes | — | — | ✅ | — |
| get_collection_list / create_collection | — | — | ✅ | — |
| upload_image_to_qun_album / get_qun_album_list | — | — | ✅ | — |
| get_group_album_media_list / del_group_album_media / do_group_album_comment / set_group_album_media_like | — | — | ✅ | — |
| create_flash_task / download_fileset / get_fileset_id / get_fileset_info / get_flash_file_list / get_flash_file_url / get_share_link | — | — | ✅ | — |
| send_online_file / send_online_folder / receive_online_file / refuse_online_file / cancel_online_file / get_online_file_msg | — | — | ✅ | — |
| download_file_stream / download_file_image_stream / download_file_record_stream / upload_file_stream / clean_stream_temp_file / test_download_stream | — | — | ✅ | — |
| click_inline_keyboard_button / bot_exit / test_auto_register_01 / test_auto_register_02 | — | — | ✅ | — |

### LLOneBot 私有扩展（强绑定 LLOneBot 运行时，本仓不计划支持）

| 动作 | 本仓 | gocq | NapCat | LLOneBot |
| ---- |:--:|:--:|:--:|:--:|
| get_config | — | — | — | ✅ |
| set_config | — | — | — | ✅ |
| get_event | — | — | — | ✅ |
| send_pb | — | — | — | ✅ |
| llonebot_debug | — | — | — | ✅ |
| create_group_album | — | — | — | ✅ |
| delete_group_album | — | — | — | ✅ |
| get_group_album_list | — | — | — | ✅ |
| get_group_album_media_list | — | — | — | ✅ |
| upload_group_album | — | — | — | ✅ |
| upload_flash_file | — | — | — | ✅ |
| download_flash_file | — | — | — | ✅ |
| get_flash_file_info | — | — | — | ✅ |
| reshare_flash_file | — | — | — | ✅ |


---

## 支持的消息段

消息由一组**段（segment）**组成，每个段是 `{ "type": "xxx", "data": {...} }` 格式的对象。发送时传段数组，收到的消息 `message` 字段也是段数组。

> 不支持 CQ 码：发送时若 `message` 传字符串，会被当作**纯文本**；事件里的 `raw_message` 也是纯文本（仅文本段拼接）。未识别的段类型会原样透传，不会丢失。

| 类型 | 说明 | 常用 |
| ---- | ---- | :--: |
| `text` | 纯文本 | ✓ |
| `at` | @某人 / @全体 | ✓ |
| `face` / `sface` | QQ 表情 | ✓ |
| `image` / `flash` | 图片 / 闪照 | ✓ |
| `reply` / `quote` | 回复引用 | ✓ |
| `record` | 语音 | ✓ |
| `video` / `bubble` | 视频 / 气泡视频 | |
| `file` | 文件 | |
| `json` | JSON 卡片 | |
| `xml` | XML 卡片 | |
| `share` | 链接分享 | |
| `location` | 位置 | |
| `music` | 音乐分享（QQ音乐 / 网易云 / 自定义） | |
| `contact` | 推荐联系人 / 群 | |
| `poke` | 戳一戳 | |
| `mface` | 商城表情 | |
| `bface` | 原创表情 | |
| `rps` / `dice` | 猜拳 / 骰子（魔法表情） | |
| `markdown` | Markdown | |
| `button` | 按钮 | |
| `node` | 转发节点（合并转发用） | |
| `forward` | 合并转发引用 | |
| `long_msg` | 长消息引用 | |
| `mirai` | mirai 数据透传 | |
| `forum` | 论坛 / 帖子 | |

各段的字段说明与示例见[消息段文档](https://icqqjs.zhin.dev)。

---

## 与标准 OneBot 11 的差异

| 特性 | 标准 OneBot 11 | icqq-rust-onebot |
| ---- | ---- | ---- |
| CQ 码 | 支持 | **不支持**，仅数组消息段 |
| `message_id` | int32 整数 | base64url **字符串** |
| `message_seq` | 部分实现扩展字段 | 消息上报均携带真实协议 seq |
| `target_id` | 私聊常见扩展字段 | 私聊为接收方 QQ，群聊为群号 |
| `raw_message` | 含 CQ 码 | **纯文本**（仅文本段拼接） |

### 消息上报

- 支持 `post_type: "message"` 和 `post_type: "message_sent"`；两者共用 `message_type` 的 `private` / `group` 结构。
- 当登录号自己发出消息时（包括其他设备同步来的自发消息），上报为 `message_sent`。
- 私聊和群聊消息都会携带 `target_id` 与 `message_seq`；群聊的 `target_id` 等于 `group_id`。

## 反馈

如有问题或建议，请在本仓库 [Issues](https://github.com/icqqjs/icqq-rust-onebot-releases/issues) 中提交。
