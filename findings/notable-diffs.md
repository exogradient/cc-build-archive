# Notable diffs

_Auto-maintained by `scripts/update-findings.py`. Do not edit by hand._

Flagged notable if `prompt_delta_chars` ≥ 300, a request-config lever moved (model / effort / context-management / thinking / max-tokens / betas / cache breakpoints), or any wire tool, static-binary tool, embedded/wire system-reminder, or binary surface (env var / feature flag / telemetry event / model id / beta token / endpoint / settings key) was added/removed/changed. Most recent first.

**Diff dirs exist iff the transition is notable.** A diff dir under `findings/diffs/<from>__to__<to>/` is materialized exactly when this list includes the transition — both are governed by the same predicate (`auto-diff.is_notable_summary`). Non-notable transitions write nothing; the build still appears in `version-history.md` (it existed; its surface was identical to its predecessor's).

## `2.1.177.e2d` → `2.1.178.575`

- **Prompt delta**: +0 chars (instructions block)
- **Tools with changed definition**: `Agent` (description, input_schema), `Skill` (description), `Workflow` (description)
- **Binary tools removed**: `TeamCreate`, `TeamDelete`
- **System reminders (binary)**: 1 modified (see `system-reminders.matrix`)
- **Env vars**: added `CLAUDE_CODE_COORDINATOR_EXTRA_TOOLS`, `CLAUDE_CODE_DESIGN_OAUTH_CLIENT_ID`, `CLAUDE_CODE_DISABLE_MEMORY_PERIODIC_RESYNC`, `CLAUDE_CODE_FABLE_BRIDGE_DIALOG_TIMEOUT_MS`, `CLAUDE_CODE_TODO_REMINDER_MODE`; removed `CLAUDE_CODE_AGENT_LIST_IN_MESSAGES`
- **Telemetry events**: added `tengu_agent_tool_remote_launched`, `tengu_async_agent_stranded_tools_cleared`, `tengu_cedar_sundial`, `tengu_chrome_bridge_account_mismatch`, `tengu_config_fallback_write`, `tengu_convolute_arcades_tools`, `tengu_daemon_exit`, `tengu_design_oauth_login_error`, `tengu_design_oauth_login_success`, `tengu_design_oauth_manual_entry`, `tengu_edit_tool_stale_read`, `tengu_fallback_sweep_tools`, `tengu_juniper_shoal_shown`, `tengu_memory_store_resync_interval_minutes`, `tengu_neapolitan`, `tengu_precomputed_compact_arm_gated`, `tengu_repl_bridge_dialog_kinds_declared`, `tengu_soft_slate_nudge`, `tengu_wif_user_oauth_refresh_race_resolved`; removed `tengu_agent_list_attach`, `tengu_auto_background_agents`, `tengu_compass_dial`, `tengu_oauth_gateway_forced`, `tengu_oauth_gateway_selected`, `tengu_team_created`, `tengu_team_deleted`
- [Tool definition diffs](diffs/2.1.177.e2d__to__2.1.178.575/tools.diff) · [all artifacts](diffs/2.1.177.e2d__to__2.1.178.575/)

## `2.1.175.ea6` → `2.1.176.5ab`

- **Prompt delta**: +0 chars (instructions block)
- **Tools with changed definition**: `Agent` (input_schema)
- **Env vars**: added `CLAUDE_CODE_TOTAL_TOKENS_REMINDER`, `CLAUDE_IN_CHROME_DOMAIN_RULE_TOOL`, `CLAUDE_IN_CHROME_MCP_SERVER_NAME`
- **Telemetry events**: added `tengu_bg_exec_no_lastline`, `tengu_chrome_auto_enable_prompt_shown`, `tengu_fabricated_turn_candidate`, `tengu_lantern_spool`, `tengu_lapis_anchor`, `tengu_mcp_first_party_auto_auth`, `tengu_non_deferrable_builtins`, `tengu_silent_harbor`
- **Model ids**: added `claude-in-teams`
- **Endpoints**: added `https://claude.ai/code/artifact/`, `https://claude.ai/code/artifact/$`
- [Tool definition diffs](diffs/2.1.175.ea6__to__2.1.176.5ab/tools.diff) · [all artifacts](diffs/2.1.175.ea6__to__2.1.176.5ab/)

## `2.1.173.53a` → `2.1.174.d48`

- **Prompt delta**: +0 chars (instructions block)
- **Binary tools added**: `Projects`
- **Env vars**: added `CLAUDE_CODE_ENABLE_REMOTE_RECAP`, `CLAUDE_CODE_HIDE_SETTINGS_HINT`, `CLAUDE_OPUS_4_8`, `CLAUDE_PROJECT_TOOL`, `CLAUDE_PROJECT_UUID`, `CLAUDE_STAGE_FILE_ROOT`; removed `CLAUDE_CODE_ARTIFACT_MCP`, `CLAUDE_CODE_VELVET_FALCON`, `CLAUDE_OPUS_4_6`
- **Telemetry events**: added `tengu_cobalt_plinth_fern`, `tengu_harbor_moth`, `tengu_malformed_tool_use_clean_retry`, `tengu_malformed_tool_use_retry_outcome`, `tengu_plugin_autoupdate_allow_credential_helper`, `tengu_plugin_refresh_on_miss`, `tengu_sunset_penguin_opus46`; removed `tengu_velvet_falcon_model`
- **Model ids**: removed `claude-code-settings`
- [Diff artifacts](diffs/2.1.173.53a__to__2.1.174.d48/)

## `2.1.170.6bc` → `2.1.172.326`

- **Prompt delta**: +0 chars (instructions block)
- **Binary tools added**: `Artifact`, `ShowOnboardingRolePicker`
- **Env vars**: added `CLAUDE_CODE_ARTIFACT_AUTO_OPEN`, `CLAUDE_CODE_ARTIFACT_DIRECT_UPLOAD`, `CLAUDE_CODE_ARTIFACT_MCP`, `CLAUDE_CODE_AUTO_MODE_SIBLING_CONTEXT`, `CLAUDE_CODE_AUTO_MODE_TEMPERATURE`, `CLAUDE_CODE_CHILD_SESSION`, `CLAUDE_CODE_DISABLE_ARTIFACT`, `CLAUDE_CODE_FORCE_SESSION_PERSISTENCE`, `CLAUDE_CODE_SKIP_PLUGIN_MCP_SERVERS`, `CLAUDE_RUNNER_FETCH_DEPTH`; removed `CLAUDE_CODE_FRAME`, `CLAUDE_CODE_FRAME_AUTO_OPEN`, `CLAUDE_CODE_FRAME_MCP`
- **Telemetry events**: added `tengu_1m_credits_clamp_activated`, `tengu_auto_mode_sibling_context_error`, `tengu_ccr_preserved_event_ids_clamped`, `tengu_cobalt_plinth`, `tengu_cobalt_plinth_direct`, `tengu_compact_credits_clamp_rescue`, `tengu_fallback_credit_skipped`, `tengu_policy_limits_cache_write_failed`, `tengu_reactive_compact_remote`, `tengu_rotunda_pennant_sync_dropped`, `tengu_slate_fern`, `tengu_structured_output_late_retraction_drop`, `tengu_structured_output_retracted`, `tengu_structured_output_retraction_exhausted`, `tengu_web_fetch_provenance_prompt`
- **Model ids**: added `claude-fable-5-mythos-5`, `claude-in-slack`
- **API beta tokens (binary)**: added `server-side-fallback-2026-06-09`
- **Endpoints**: added `https://api.anthropic.com/v1/deployments`, `https://platform.claude.com/docs/en/about-claude/models/introducing-claude-fable-5.md`, `https://www.anthropic.com/news/claude-fable-5-mythos-5`
- **Settings keys**: removed `shouldBlock`, `thinking`
- [Diff artifacts](diffs/2.1.170.6bc__to__2.1.172.326/)

## `2.1.169.ab7` → `2.1.170.6bc`

- **Prompt delta**: +45 chars (instructions block)
- **Tools with changed definition**: `Agent` (input_schema)
- **Env vars**: added `ANTHROPIC_DEFAULT_FABLE_MODEL`, `ANTHROPIC_DEFAULT_FABLE_MODEL_DESCRIPTION`, `ANTHROPIC_DEFAULT_FABLE_MODEL_NAME`, `ANTHROPIC_DEFAULT_FABLE_MODEL_SUPPORTED_CAPABILITIES`; removed `CLAUDE_CODE_FORCE_SESSION_PERSISTENCE`
- **Feature flags**: added `DISABLE_PROMPT_CACHING_FABLE`, `DISABLE_PROMPT_CACHING_MYTHOS`
- **Telemetry events**: added `tengu_fable5_launch_shown`, `tengu_fallback_credit_forfeited`, `tengu_fallback_credit_minted`, `tengu_fallback_credit_outcome`, `tengu_loggia_carousel_config`, `tengu_saffron_lattice`; removed `tengu_opus48_launch_shown`
- **Model ids**: added `claude-fable-5`, `claude-mythos-5`
- **API beta tokens (binary)**: added `fallback-credit-2026-06-01`; removed `fallback-credit-2026-06-09`
- **Endpoints**: removed `https://code.claude.com/docs/en/overviewI&`
- [Tool definition diffs](diffs/2.1.169.ab7__to__2.1.170.6bc/tools.diff) · [all artifacts](diffs/2.1.169.ab7__to__2.1.170.6bc/)

## `2.1.168.91f` → `2.1.169.ab7`

- **Prompt delta**: +279 chars (instructions block)
- **Binary tools with changed definition**: `RemoteTrigger` (see `tools-from-binary.matrix`)
- **Env vars**: added `CLAUDE_BG_CLAIM_AUTH`, `CLAUDE_BG_PTY_AUTH`, `CLAUDE_BG_RV_AUTH`, `CLAUDE_BG_SOCKET_TOKENS_PATH`, `CLAUDE_CODE_DISABLE_BUNDLED_SKILLS`, `CLAUDE_CODE_FORCE_SESSION_PERSISTENCE`, `CLAUDE_CODE_FRAME_MCP`, `CLAUDE_CODE_PEWTER_OWL_TOOL`, `CLAUDE_CODE_SAFE_MODE`, `CLAUDE_CODE_USER_DIALOG_TIMEOUT_MS`, `CLAUDE_CODE_WEBFETCH_USE_CCR_PROXY`; removed `CLAUDE_CODE_WEBFETCH_PROXY_PATH`
- **Telemetry events**: added `tengu_amber_sextant`, `tengu_ant_yolo_equiv_strip_config`, `tengu_bg_rv_reply_rejected`, `tengu_cd_command`, `tengu_cedar_plume`, `tengu_dialog_waiting_in_transcript`, `tengu_event_watchdog_default_on`, `tengu_fallback_credit_strip_as_mint_model`, `tengu_inject_control_response_unknown_id`, `tengu_lsp_diagnostics_disabled`, `tengu_mcp_stateless_skip_init`, `tengu_partial_stream_retraction_closed`, `tengu_partial_stream_retraction_display_only`, `tengu_pending_action_republished`, `tengu_plugin_autoupdate_pass`, `tengu_plugin_delisted_enforcement`, `tengu_print_model_override_adopted`, `tengu_refusal_fallback_dialog_suppressed`, `tengu_refusal_fallback_latch_reset`, `tengu_refusal_fallback_resume_latch`, `tengu_refusal_fallback_rewind_unwind`, `tengu_refusal_fallback_supersedes`, `tengu_refusal_retraction_evicted`, `tengu_refusal_retraction_history_dropped`, `tengu_refusal_retraction_late_drop`, `tengu_refusal_retraction_orphan_tool_result`, `tengu_refusal_retraction_truncation_harvest`, `tengu_refusal_retraction_unauthenticated_signal`, `tengu_refusal_turn_classified_complete`, `tengu_reinit_pending_redelivery`, `tengu_request_user_dialog_late_answer`, `tengu_request_user_dialog_requires_action`, `tengu_request_user_dialog_response_ignored`, `tengu_request_user_dialog_timeout`, `tengu_resume_model_restore`, `tengu_resume_retracted_dropped`, `tengu_resume_stale_prompt_cancel`, `tengu_rotunda_pennant_applied`, `tengu_rotunda_pennant_credit_echoed`, `tengu_rotunda_pennant_esc`, `tengu_rotunda_pennant_malformed`, `tengu_rotunda_pennant_materialized`, `tengu_rotunda_pennant_replay`, `tengu_rotunda_pennant_strip`, `tengu_rotunda_pennant_tools`, `tengu_supported_dialog_kinds_restored`, `tengu_tombstone_persisted_removal`, `tengu_tool_input_coerced`
- **Model ids**: added `claude-code-runtime`, `claude-design-contextual`, `claude-plugins-community`
- **API beta tokens (binary)**: added `fallback-credit-2026-06-09`, `server-side-fallback-2026-06-01`
- **Endpoints**: added `https://claude.ai/design?utm_source=claude_code&utm_medium=tip&utm_campaign=tengu_cedar_plume`, `https://code.claude.com/docs/en/overviewI&`, `https://platform.claude.com/docs/en/manage-claude/authentication.md`, `https://platform.claude.com/docs/en/manage-claude/wif-reference.md`
- [Diff artifacts](diffs/2.1.168.91f__to__2.1.169.ab7/)

## `2.1.166.4b6` → `2.1.168.91f`

- **Prompt delta**: +0 chars (instructions block)
- **Model ids**: removed `claude-empty-s`
- [Diff artifacts](diffs/2.1.166.4b6__to__2.1.168.91f/)

## `2.1.165.ecd` → `2.1.166.4b6`

- **Prompt delta**: +0 chars (instructions block)
- **Tools with changed definition**: `Workflow` (description)
- **Env vars**: added `CLAUDE_CODE_ARTIFACT`, `CLAUDE_CODE_ENABLE_DESIGN_SYNC`, `CLAUDE_CODE_FRAME_AUTO_OPEN`, `CLAUDE_CODE_WEBFETCH_PROXY_PATH`, `CLAUDE_PTY_HEARTBEAT_MS`
- **Telemetry events**: added `tengu_api_fallback_last_resort`, `tengu_fullscreen_upsell_dialog_accepted`, `tengu_fullscreen_upsell_dialog_dismissed`, `tengu_fullscreen_upsell_dialog_shown`, `tengu_managed_settings_validation_errors`, `tengu_mcp_command_inline`, `tengu_refusal_fallback_suppressed`, `tengu_request_user_dialog_implicit_cancel`, `tengu_resume_worktree_fallback`, `tengu_shell_allow_rule_added`, `tengu_shell_allow_rules_at_init`, `tengu_velvet_hammer`, `tengu_velvet_mallet`, `tengu_voice_init_gate`, `tengu_write_tool_not_read_hypothetical`; removed `tengu_cedar_hollow_7m`, `tengu_fullscreen_upsell_shown`, `tengu_ws_transport_closed`, `tengu_ws_transport_reconnected`, `tengu_ws_transport_reconnecting`
- **Model ids**: added `claude-empty-s`
- **Endpoints**: added `https://support.claude.com/en/articles/15363606`
- [Tool definition diffs](diffs/2.1.165.ecd__to__2.1.166.4b6/tools.diff) · [all artifacts](diffs/2.1.165.ecd__to__2.1.166.4b6/)

## `2.1.163.7c7` → `2.1.165.ecd`

- **Prompt delta**: +0 chars (instructions block)
- **Model ids**: removed `claude-empty-r`
- [Diff artifacts](diffs/2.1.163.7c7__to__2.1.165.ecd/)

## `2.1.161.b76` → `2.1.163.7c7`

- **Prompt delta**: +0 chars (instructions block)
- **Tools removed**: `Glob`, `Grep`
- **Tools with changed definition**: `Bash` (description), `EnterPlanMode` (description), `NotebookEdit` (description), `Workflow` (description)
- **Env vars**: added `CLAUDE_CODE_ACT_DONT_REDERIVE`, `CLAUDE_CODE_AUTH_FAIL_EXIT_MS`, `CLAUDE_CODE_ENABLE_MENU_KIND_LANES`, `CLAUDE_CODE_INVOKED_SKILLS`, `CLAUDE_CODE_KB_COHESION_FIXES`, `CLAUDE_CODE_OAUTH_401_WAIT_MS`, `CLAUDE_CODE_REMOTE_HERMETIC_MODE`, `CLAUDE_CODE_SYNC_SKILLS_INSTALL_TIMEOUT_MS`, `CLAUDE_CODE_VELVET_FALCON`, `CLAUDE_GATEWAY_LOG_LEVEL`; removed `CLAUDE_CODE_FORCE_MEMORY_WRITE_SURVEY`, `CLAUDE_CODE_FORK_SUBAGENT_DEFAULT_ON`, `CLAUDE_CODE_FRAME_MODE`, `CLAUDE_CODE_MEMORY_WRITE_SURVEY_TIMEOUT_MS`
- **Telemetry events**: added `tengu_auto_compact_prefix_overflow`, `tengu_bg_attach_upgrade`, `tengu_bg_prewarm_per_sweep`, `tengu_cedar_lantern`, `tengu_convolute_arcades_retry`, `tengu_convolute_arcades_retry_outcome`, `tengu_edit_tool_not_read_hypothetical`, `tengu_lone_surrogate_sanitized`, `tengu_maple_sundial`, `tengu_mcp_local_oauth_blocked_hosts`, `tengu_mint_lanes`, `tengu_native_cursor`, `tengu_oauth_401_recovered_from_rotation`, `tengu_oauth_401_zombie_exit`, `tengu_oauth_gateway_forced`, `tengu_oauth_refresh_token_cleared_on_disk`, `tengu_personal_mem_sync_started`, `tengu_precomputed_compact_rearm_capped`, `tengu_refusal_fallback_entry_recorded`, `tengu_reload_plugins_cache_impact`, `tengu_sdk_hook_callback_timeout`, `tengu_session_start`, `tengu_shutdown_signal`, `tengu_velvet_falcon_model`, `tengu_vscode_feedback_survey`; removed `tengu_memory_write_survey_event`, `tengu_slate_siskin`
- **Model ids**: added `claude-empty-r`; removed `claude-in-chrome-default-enabled`
- **Endpoints**: added `https://slack.mcp.claude.com/mcp`; removed `https://docs.anthropic.com/en/docs/claude-code/getting-started`
- [Tool definition diffs](diffs/2.1.161.b76__to__2.1.163.7c7/tools.diff) · [all artifacts](diffs/2.1.161.b76__to__2.1.163.7c7/)

## `2.1.160.bca` → `2.1.161.b76`

- **Prompt delta**: +0 chars (instructions block)
- **Tools with changed definition**: `TaskOutput` (description)
- **Binary tools with changed definition**: `SendMessage`, `TeamCreate`, `TeamDelete` (see `tools-from-binary.matrix`)
- **Env vars**: added `CLAUDE_CODE_DISABLE_MEMORY_BULK_INFLATE`, `CLAUDE_CODE_DISABLE_REFUSAL_FALLBACK`, `CLAUDE_CODE_OWNERSHIP_FRAME`, `CLAUDE_CODE_SUPPRESS_SESSION_ATTRIBUTION`
- **Telemetry events**: added `tengu_copper_thistle`, `tengu_mcp_skills`, `tengu_memory_bulk_inflate`, `tengu_plugin_state_file_error`, `tengu_walnut_prism`
- [Tool definition diffs](diffs/2.1.160.bca__to__2.1.161.b76/tools.diff) · [all artifacts](diffs/2.1.160.bca__to__2.1.161.b76/)

## `2.1.159.28e` → `2.1.160.bca`

- **Prompt delta**: +0 chars (instructions block)
- **Tools with changed definition**: `WebSearch` (description), `Workflow` (description)
- **Binary tools added**: `DesignSync`
- **Env vars**: added `CLAUDE_BRIDGE_BASE_URL`, `CLAUDE_BRIDGE_OAUTH_TOKEN`, `CLAUDE_BRIDGE_SESSION_INGRESS_URL`, `CLAUDE_CODE_AUTO_MODE_EXTERNAL_PERMISSIONS`, `CLAUDE_CODE_AUTO_MODE_MODEL`, `CLAUDE_CODE_BG_CLASSIFIER_MODEL`, `CLAUDE_CODE_DD_ERROR_TRACKING_FLUSH_INTERVAL_MS`, `CLAUDE_CODE_DEV_RAW_CHANGELOG_URL`, `CLAUDE_CODE_ENABLE_OPUS_4_7_FAST_MODE`, `CLAUDE_CODE_FORCE_BRIDGE`, `CLAUDE_CODE_FORCE_EVALUATE_MEMORY`, `CLAUDE_CODE_FORCE_MEMORY_SURVEY`, `CLAUDE_CODE_FORCE_MEMORY_WRITE_SURVEY`, `CLAUDE_CODE_FORCE_TIP_ID`, `CLAUDE_CODE_FORK_SUBAGENT_DEFAULT_ON`, `CLAUDE_CODE_FRAME`, `CLAUDE_CODE_FRAME_MODE`, `CLAUDE_CODE_GB_BASE_URL`, `CLAUDE_CODE_GB_REFRESH_INTERVAL_MS`, `CLAUDE_CODE_HFI_BEARER_TOKEN`, `CLAUDE_CODE_JSONL_TRANSCRIPT`, `CLAUDE_CODE_MANAGED_SETTINGS_PATH`, `CLAUDE_CODE_MEMORY_WRITE_SURVEY_TIMEOUT_MS`, `CLAUDE_CODE_MID_CONVERSATION_SYSTEM`, `CLAUDE_CODE_MOCK_REMOTE_SETTINGS`, `CLAUDE_CODE_MOCK_TRIAL`, `CLAUDE_CODE_OVERRIDE_DATE`, `CLAUDE_CODE_PERFETTO_WRITE_INTERVAL_S`, `CLAUDE_CODE_PLAN_MODE_INTERVIEW_PHASE`, `CLAUDE_CODE_REMOTE_RAW_EVENTS_FILE`, `CLAUDE_CODE_REMOTE_SETTINGS_POLL_MS`, `CLAUDE_CODE_SKIP_HFI_VERSION_CHECK`, `CLAUDE_CODE_SKIP_PROJECT_BACKFILL`, `CLAUDE_CODE_SKIP_REPO_UPLOAD`, `CLAUDE_CODE_TAG_ISMETA_MESSAGES`, `CLAUDE_CODE_TERMINAL_RECORDING`, `CLAUDE_CODE_TEST_FORCE_DENY`, `CLAUDE_CODE_TEST_NO_GIT_BASH`, `CLAUDE_CODE_TEST_NO_PWSH`, `CLAUDE_CODE_TWO_STAGE_CLASSIFIER`, `CLAUDE_CODE_USE_NATIVE_FILE_SEARCH`, `CLAUDE_CONTEXT_COLLAPSE`, `CLAUDE_CONTEXT_COLLAPSE_MODEL`, `CLAUDE_GATEWAY_ALLOW_LOOPBACK`, `CLAUDE_INTERNAL_WARM_RESUME_QA`, `CLAUDE_MOCK_HEADERLESS_429`, `CLAUDE_SERVE_DRAIN_TIMEOUT_MS`, `CLAUDE_SNIP`, `CLAUDE_SSH_LOCAL_BINARY`, `CLAUDE_SSH_VERSION`
- **Feature flags**: added `ENABLE_LOCKLESS_UPDATES`, `ENABLE_LSP_TOOL`, `ENABLE_PID_BASED_VERSION_LOCKING`, `ENABLE_SESSION_BACKGROUNDING`, `ENABLE_SESSION_PERSISTENCE`, `USE_API_CLEAR_TOOL_RESULTS`, `USE_API_CLEAR_TOOL_USES`
- **Telemetry events**: added `tengu_auto_mode_entry_warning_shown`, `tengu_bg_respawn`, `tengu_bg_respawn_no_transcript`, `tengu_bg_state_read_transient`, `tengu_c4e_slash_upsell`, `tengu_c4e_slash_upsell_shown`, `tengu_refusal_fallback_prompt_choice`, `tengu_refusal_fallback_prompt_shown`, `tengu_refusal_fallback_setting_changed`, `tengu_review_workflow_routing`, `tengu_slate_quill`, `tengu_stage_file_completed`
- **Model ids**: added `claude-cli-design-sync`
- **Endpoints**: added `https://clau.de/enterprise`, `https://claude.ai/design/p/`
- [Tool definition diffs](diffs/2.1.159.28e__to__2.1.160.bca/tools.diff) · [all artifacts](diffs/2.1.159.28e__to__2.1.160.bca/)

## `2.1.158.5e6` → `2.1.159.28e`

- **Prompt delta**: +0 chars (instructions block)
- **Env vars**: added `CLAUDE_CODE_PEWTER_OWL`
- **Telemetry events**: added `tengu_pewter_owl_model`
- **API beta tokens (binary)**: added `summarize-connector-text-2026-03-13`
- [Diff artifacts](diffs/2.1.158.5e6__to__2.1.159.28e/)

## `2.1.157.152` → `2.1.158.5e6`

- **Prompt delta**: +0 chars (instructions block)
- **Env vars**: added `CLAUDE_CODE_ENABLE_AUTO_MODE`
- [Diff artifacts](diffs/2.1.157.152__to__2.1.158.5e6/)

## `2.1.156.588` → `2.1.157.152`

- **Prompt delta**: +0 chars (instructions block)
- **Tools with changed definition**: `EnterWorktree` (description)
- **Env vars**: added `CLAUDE_BYTE_STREAM_IDLE_TIMEOUT_MS`, `CLAUDE_CODE_LOOP_KEEPALIVE`, `CLAUDE_CODE_SYNC_PLUGINS`, `CLAUDE_CODE_SYNC_PLUGINS_INSTALL_TIMEOUT_MS`, `CLAUDE_CODE_SYNC_PLUGINS_MCP_TIMEOUT_MS`
- **Telemetry events**: added `attributionAgentHash`, `attributionMcpServerHash`, `attributionMcpToolHash`, `attributionPluginHash`, `attributionSkillHash`, `tengu_byte_stream_idle_timeout_ms`, `tengu_cedar_marsh`, `tengu_compass_dial`, `tengu_coordinator_panel`, `tengu_fotw_nudge_shown`, `tengu_kairos_loop_keepalive`, `tengu_loop_ended`, `tengu_loop_keepalive_fired`, `tengu_plugin_install_failed`, `tengu_plugins_sync_error`, `tengu_plugins_sync_list_failed`, `tengu_plugins_sync_mcp_skipped`, `tengu_plugins_sync_mcp_timeout`, `tengu_plugins_sync_success`, `tengu_plugins_sync_wait_timeout`; removed `tengu_anchor_tide`
- **Endpoints**: added `https://www.anthropic.com/legal/promotion-terms`
- [Tool definition diffs](diffs/2.1.156.588__to__2.1.157.152/tools.diff) · [all artifacts](diffs/2.1.156.588__to__2.1.157.152/)

## `2.1.154.608` → `2.1.156.588`

- **Prompt delta**: +0 chars (instructions block)
- **Telemetry events**: added `tengu_reorder_tool_uses_skipped_for_thinking`
- [Diff artifacts](diffs/2.1.154.608__to__2.1.156.588/)

## `2.1.153.9bb` → `2.1.154.608`

- **Default model**: `claude-opus-4-7` → `claude-opus-4-8`
- **Prompt delta**: -20746 chars (instructions block)
- **Output config (effort)**: `{'effort': 'xhigh'}` → `{'effort': 'high'}`
- **Cache breakpoints**: `['system[1]', 'system[2]', 'messages[0][2]']` → `['system[1]', 'system[2]', 'messages[0][1]']`
- **API betas**: added `mid-conversation-system-2026-04-07`
- **Tools added**: `Workflow`
- **Tools with changed definition**: `Agent` (description), `AskUserQuestion` (description), `Bash` (description), `Edit` (description), `Glob` (description), `Grep` (description), `Read` (description), `WebFetch` (description), `WebSearch` (description), `Write` (description)
- **Wire reminders (skills/context)**: 1 removed (see `wire-reminders.matrix`)
- **Env vars**: added `CLAUDE_CODE_DISABLE_CLAUDE_CODE_SKILL`, `CLAUDE_CODE_FORCE_MID_CONVERSATION_SYSTEM`, `CLAUDE_CODE_SKILL_DESCRIPTION`, `CLAUDE_CODE_SKILL_NAME`, `CLAUDE_PTY_ORPHAN_CHECK_MS`; removed `CLAUDE_CODE_MID_CONVERSATION_SYSTEM`
- **Telemetry events**: added `tengu_amber_redwood3`, `tengu_basalt_meadow`, `tengu_bg_daemon_spawn_versions_fallback`, `tengu_birch_kettle`, `tengu_cedar_hollow_7m`, `tengu_claude_code_skill_loaded`, `tengu_cobalt_thicket`, `tengu_hook_prompt_too_long_retry`, `tengu_opus48_launch_shown`, `tengu_render_glyph_cardinality`, `tengu_ultra_effort`, `tengu_wif_implicit_profile_skipped_stored_login`, `tengu_xterm_atlas_reset`; removed `tengu_fennel_kite_model`, `tengu_fg_left_arrow_agents`, `tengu_mcp_retry_on_tools_list_error`, `tengu_opus47_launch_shown`, `tengu_streaming_tool_execution2`, `tengu_streaming_tool_execution_not_used`, `tengu_streaming_tool_execution_used`, `tengu_vellum_lantern`
- **Model ids**: added `claude-code-docs`, `claude-opus-4-8`
- **Endpoints**: added `https://api.anthropic.com/v1/models/claude-opus-4-8`, `https://code.claude.com/docs`, `https://code.claude.com/docs/en/amazon-bedrock.md`, `https://code.claude.com/docs/en/changelog.md`, `https://code.claude.com/docs/en/claude-code-on-the-web.md`, `https://code.claude.com/docs/en/claude-directory.md`, `https://code.claude.com/docs/en/cli-reference.md`, `https://code.claude.com/docs/en/commands.md`, `https://code.claude.com/docs/en/common-workflows.md`, `https://code.claude.com/docs/en/costs.md`, `https://code.claude.com/docs/en/env-vars.md`, `https://code.claude.com/docs/en/github-actions.md`, `https://code.claude.com/docs/en/google-vertex-ai.md`, `https://code.claude.com/docs/en/hooks.md`, `https://code.claude.com/docs/en/interactive-mode.md`, `https://code.claude.com/docs/en/jetbrains.md`, `https://code.claude.com/docs/en/mcp.md`, `https://code.claude.com/docs/en/memory.md`, `https://code.claude.com/docs/en/microsoft-foundry.md`, `https://code.claude.com/docs/en/network-config.md`, `https://code.claude.com/docs/en/output-styles.md`, `https://code.claude.com/docs/en/permission-modes`, `https://code.claude.com/docs/en/permissions.md`, `https://code.claude.com/docs/en/plugins.md`, `https://code.claude.com/docs/en/sandboxing.md`, `https://code.claude.com/docs/en/security.md`, `https://code.claude.com/docs/en/settings.md`, `https://code.claude.com/docs/en/skills.md`, `https://code.claude.com/docs/en/sub-agents.md`, `https://code.claude.com/docs/en/vs-code.md`; removed `https://api.anthropic.com/v1/models/claude-opus-4-7`
- [Tool definition diffs](diffs/2.1.153.9bb__to__2.1.154.608/tools.diff) · [all artifacts](diffs/2.1.153.9bb__to__2.1.154.608/)

## `2.1.141.e27` → `2.1.142.1aa`

- **Prompt delta**: +1 chars (instructions block)
- **Tools added**: `TaskCreate`, `TaskGet`, `TaskList`, `TaskUpdate`
- **Tools removed**: `TodoWrite`
- **Tools with changed definition**: `Bash` (description)
- **Binary tools added**: `SendUserFile`
- [Tool definition diffs](diffs/2.1.141.e27__to__2.1.142.1aa/tools.diff) · [all artifacts](diffs/2.1.141.e27__to__2.1.142.1aa/)

## `2.1.139.b1c` → `2.1.141.e27`

- **Prompt delta**: +4 chars (instructions block)
- **Tools with changed definition**: `Grep` (input_schema), `ScheduleWakeup` (description)
- [Tool definition diffs](diffs/2.1.139.b1c__to__2.1.141.e27/tools.diff) · [all artifacts](diffs/2.1.139.b1c__to__2.1.141.e27/)

## `2.1.138.1a3` → `2.1.139.b1c`

- **Prompt delta**: +404 chars (instructions block)
- **Tools with changed definition**: `Agent` (description)
- [Tool definition diffs](diffs/2.1.138.1a3__to__2.1.139.b1c/tools.diff) · [all artifacts](diffs/2.1.138.1a3__to__2.1.139.b1c/)

## `2.1.129.49a` → `2.1.138.1a3`

- **Prompt delta**: +0 chars (instructions block)
- **Tools with changed definition**: `Bash` (input_schema), `EnterWorktree` (description)
- **System reminders (binary)**: 1 removed, 1 modified (see `system-reminders.matrix`)
- [Tool definition diffs](diffs/2.1.129.49a__to__2.1.138.1a3/tools.diff) · [all artifacts](diffs/2.1.129.49a__to__2.1.138.1a3/)

## `2.1.128.9fd` → `2.1.129.49a`

- **Default model**: `claude-sonnet-4-6` → `claude-opus-4-7`
- **Prompt delta**: +14 chars (instructions block)
- **Output config (effort)**: `{'effort': 'high'}` → `{'effort': 'xhigh'}`
- **Max tokens**: `32000` → `64000`
- **API betas**: added `context-1m-2025-08-07`
- **Tools with changed definition**: `Bash` (description), `EnterPlanMode` (description)
- [Tool definition diffs](diffs/2.1.128.9fd__to__2.1.129.49a/tools.diff) · [all artifacts](diffs/2.1.128.9fd__to__2.1.129.49a/)

## `2.1.116.f49` → `2.1.128.9fd`

- **Prompt delta**: +20 chars (instructions block)
- **Tools with changed definition**: `Agent` (description), `Read` (description)
- **Binary tools added**: `ShareOnboardingGuide`
- **Binary tools removed**: `Config`
- **Binary tools with changed definition**: `RemoteTrigger` (see `tools-from-binary.matrix`)
- **System reminders (binary)**: 1 removed, 1 modified (see `system-reminders.matrix`)
- **Wire reminders (skills/context)**: 1 modified (see `wire-reminders.matrix`)
- [Tool definition diffs](diffs/2.1.116.f49__to__2.1.128.9fd/tools.diff) · [all artifacts](diffs/2.1.116.f49__to__2.1.128.9fd/)

## `2.1.111.b2b` → `2.1.116.f49`

- **Prompt delta**: -132 chars (instructions block)
- **Tools with changed definition**: `Bash` (description)
- **System reminders (binary)**: 2 added (see `system-reminders.matrix`)
- **Wire reminders (skills/context)**: 1 modified (see `wire-reminders.matrix`)
- [Tool definition diffs](diffs/2.1.111.b2b__to__2.1.116.f49/tools.diff) · [all artifacts](diffs/2.1.111.b2b__to__2.1.116.f49/)

## `2.1.110.610` → `2.1.111.b2b`

- **Prompt delta**: -449 chars (instructions block)
- **Output config (effort)**: `absent` → `{'effort': 'high'}`
- **Tools with changed definition**: `Agent` (description), `Skill` (description, input_schema)
- **Wire reminders (skills/context)**: 1 modified (see `wire-reminders.matrix`)
- [Tool definition diffs](diffs/2.1.110.610__to__2.1.111.b2b/tools.diff) · [all artifacts](diffs/2.1.110.610__to__2.1.111.b2b/)

## `2.1.152.8a5` → `2.1.153.9bb`

- **Prompt delta**: -146 chars (instructions block)
- **Tools with changed definition**: `AskUserQuestion` (description)
- [Tool definition diffs](diffs/2.1.152.8a5__to__2.1.153.9bb/tools.diff) · [all artifacts](diffs/2.1.152.8a5__to__2.1.153.9bb/)

## `2.1.150.474` → `2.1.152.8a5`

- **Prompt delta**: +0 chars (instructions block)
- **Tools with changed definition**: `AskUserQuestion` (description)
- **Wire reminders (skills/context)**: 1 modified (see `wire-reminders.matrix`)
- [Tool definition diffs](diffs/2.1.150.474__to__2.1.152.8a5/tools.diff) · [all artifacts](diffs/2.1.150.474__to__2.1.152.8a5/)

## `2.1.142.1aa` → `2.1.150.474`

- **Prompt delta**: +0 chars (instructions block)
- **Binary tools added**: `Workflow`
- **Binary tools with changed definition**: `Monitor` (see `tools-from-binary.matrix`)
- **System reminders (binary)**: 1 modified (see `system-reminders.matrix`)
- **Wire reminders (skills/context)**: 1 modified (see `wire-reminders.matrix`)
- [Diff artifacts](diffs/2.1.142.1aa__to__2.1.150.474/)

