# Discord coverage

Baseline live pass: Discord Stable build 621195, BetterDiscord, macOS, 2026-09-26. The targeted Windows recheck below does not replace this full matrix.

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

## Targeted recheck - 2026-10-08

Discord Stable build 637730 (59c3d22), BetterDiscord 1.14.1, Windows, theme 2.3.0. The installed CSS matched the repository copy after live reload.

- Offline members: verified readable names at rest, with subdued avatars and distinct online/offline groups. Removed the native row opacity of 0.3; user role colors are not forcibly overridden.
- Emoji search: verified a red focus border and a neutral border after losing focus, without selecting or sending an emoji. The native input uses `--input-border-active` and `data-focus-within`.
- Discord switches: verified existing ON and OFF controls on the Developer page show red and grey respectively without changing their values. The native `input[role="switch"]` is inside the same label as its visual indicator; selectors now use `:checked` instead of an exact inline RGBA value.
- Account controls: verified the lower-left row remains neutral and its controls remain visible. The decorative `fitInAccount_` container has `aria-hidden="true"`; the selector no longer includes a generated hash and remains scoped to the account panel.
- Tooltip selectors: removed the exact hash in favor of the tooltip class prefix, retaining the semantic `role="tooltip"` selector. A full tooltip pass remains outstanding.

The extended pass below covers these additional surfaces. The baseline table above remains a historical record, not a blanket validation of the current Windows build.

## Extended Windows pass - 2026-10-08

Same client/build as the targeted recheck. Live checks used a **1098 × 1105 px** window, compared with the initial **1948 × 1105 px** window. This is a desktop narrow-window check, not mobile or minimum-height coverage. The channel sidebar was approximately 375 px wide. No messages, invitations or posts were sent; no files were uploaded; no camera or stream was started.

**Verified** means the listed states were visually checked; **partial** means some variants remain untested; **needs follow-up** means a visible issue remains. Grouped surfaces are split here so a successful read-only check does not imply that uploads, video or form submission work.

| Surface / state | Result | Evidence and remaining scope |
| --- | --- | --- |
| Narrow text chat | Verified | Messages, replies, reactions, members and composer remain reachable; long channel/composer labels truncate within their available width. |
| Settings navigation and profile privacy radios | Verified | Main category and multiline subsection labels checked at both widths. Separate track marker no longer overlaps letters; selected radio circle is unobstructed. No setting values changed. |
| Search suggestions, results and empty state | Verified | Filter suggestions, populated results with highlighted matches, pagination and a no-result query checked at narrow width. Detailed filter dialog remains untested. |
| Existing thread | Partial | Opened the side pane, read long messages and replies, jumped to latest messages and checked the composer. The old-message jump button label is clipped at narrow width; thread creation/archive states remain untested. |
| Forum list and existing post | Needs follow-up | List card, tags/filter controls, post pane, replies and image grid checked. Canvas now uses the light palette. Card/search strip and thread header still inherit lavender surfaces from the native custom client theme; creation, tag selection and alternate grid layout remain untested. |
| Existing image attachments and viewer | Verified | Two-image grid in a forum post and full image viewer inspected at narrow width; close/navigation controls remain visible. Download/upload and video/audio/file attachment variants remain untested. |
| Voice connection and call stage | Partial | Joined an empty voice room with microphone muted and camera off, checked own participant tile and controls, then disconnected and restored the microphone state. Fixed the white patch behind the call title. Remote participants, camera video and active streams remain untested. |
| Screen-share source dialog | Verified | Opened the application-source picker at narrow width; source thumbnails, tabs and quality controls fit. Closed without choosing or broadcasting a source. |
| Invite dialog | Verified | Friend list, search field, footer and link/copy button fit at narrow width. Closed without sending an invitation. |
| Create channel dialog | Verified | Type choices, selected radio, name field, private-channel switch and disabled submit state fit. Native Mana text input now has one red focus ring. No channel created; errors/submission remain untested. |
| Add/create server entry dialog | Verified | Template choices, scrolling body and join-server footer fit at narrow width. Subsequent wizard steps and submission remain untested. |
| Quick switcher | Needs follow-up | Input, selected result and scrollable results fit; the pro-tip footer text is vertically clipped. Keyboard selection was not used to open a result. |
| Tooltips | Partial | Server-name, create-channel and voice-disconnect tooltips observed with readable light surfaces and red edge. Remaining toolbar variants are untested. |

### Release follow-up

- Resolve the residual native custom-theme surfaces on forum cards/search and thread headers.
- Inspect and correct the quick-switcher footer clipping and narrow thread jump-button label.
- Complete minimum-height/minimum-width checks, pinned messages, detailed search filters, upload preview/error states, non-image attachments, server/channel settings and dialog variants.
- Validate remote call participants, camera video and active streaming in a dedicated test session; a muted empty-room check cannot validate those states.
- Other historical pending rows (soundboard, inbox, notifications, Nitro/Shop and BetterDiscord settings) remain outstanding.

The theme is **not yet fully release-validated**. The installed CSS was refreshed after the fixes; source/installed hash equality and `git diff --check` are the final local checks for this pass.
