# Discord coverage

Live pass: Discord Stable build 621195, BetterDiscord, macOS, 2026-09-26.

Status means **verified** (checked in the live client during this pass), **styled** (CSS exists but the full view was not checked), or **pending** (requires a live check). It is not a claim of support for every Discord build.

| Surface | Status | CSS anchor / next check |
| --- | --- | --- |
| Server rail | Verified | Light stone rail and red Home mark checked live; Home navigation tested |
| Server channel list | Verified | Sidebar containing `[class*="containerDefault_"]`; check unread and muted channels |
| DM and Home navigation | Verified | Sidebar containing `[class*="privateChannels_"]`; check active item and search |
| Chat messages and reactions | Verified | `[class*="message_"]`, `[class*="reaction_"]`; check long messages and mentions |
| Composer and attachments | Styled | `[class*="channelTextArea_"]`; test upload and reply states |
| Member list | Verified | `[class*="membersWrap_"]`; test role colors and hover |
| Account controls | Verified | `[class*="panels_"]`; check custom profile video does not cover controls |
| Friends and activity | Verified | `[class*="peopleColumn_"]`, `[class*="nowPlayingColumn_"]`; inspect action buttons |
| User settings | Verified | Account and Voice & Video modal checked; inspect remaining pages |
| Server and channel settings | Styled | Same settings shell; inspect permissions and destructive controls |
| Profile popouts and modals | Styled | `.user-profile-popout`, `.user-profile-modal`; preserve custom themes |
| Context menus | Verified | Friend actions menu checked; inspect server and message variants |
| Dropdowns and tooltips | Styled | Light `[role="tooltip"]` rules added; verify server and toolbar hover states in a live client |
| Search and pinned messages | Styled | `[class*="searchResultsWrap_"]`; inspect result filters and empty state |
| Quick switcher | Verified | `[class*="quickswitcher_"]`; selected result contrast checked |
| Autocomplete | Styled | `[class*="autocomplete_"]`; test mentions and commands |
| Threads and forums | Pending | Test list, post, thread pane and composer |
| Calls, video and streaming | Pending | Test voice controls, participants and settings |
| Emoji, GIF and sticker pickers | Verified | Grid, search fields, tabs and selection checked in the live client |
| Soundboard | Pending | Test picker, search and selected states |
| Invite, upload and create server dialogs | Pending | Inspect each modal and error state |
| Inbox, notifications, Nitro and Shop | Pending | Inspect distinct page and popout surfaces |
| BetterDiscord settings | Pending | Check plugin and theme settings in the current client |

When updating a row, note the Discord build and a short description of any regression. Keep screenshots local unless identifying details have been removed.
