# HorizonBoostDrop

HorizonBoostDrop là một plugin Minecraft mạnh mẽ được thiết kế để tăng tỷ lệ rơi vật phẩm từ MythicMobs. Nó cho phép quản trị viên máy chủ cung cấp tỷ lệ tăng cường tạm thời hoặc vĩnh viễn cho người chơi, tăng cơ hội nhận được chiến lợi phẩm có giá trị. Plugin hỗ trợ cả vật phẩm rơi ra từ vanilla và MMOItems, với danh sách đen có thể cấu hình.

## Tính năng

-   **Tăng cường rơi vật phẩm có thể cấu hình:** Cấp cho người chơi các đợt tăng cường rơi vật phẩm dựa trên phần trăm tạm thời hoặc vĩnh viễn.
-   **Tích hợp MythicMobs:** Được thiết kế đặc biệt để hoạt động với các vật phẩm rơi ra từ MythicMobs.
-   **Hỗ trợ MMOItems:** Các đợt tăng cường áp dụng cho vật phẩm rơi ra từ MMOItems, với tùy chọn đưa vào danh sách đen các vật phẩm cụ thể.
-   **Hỗ trợ vật phẩm Vanilla:** Các đợt tăng cường cũng áp dụng cho vật phẩm rơi ra từ vanilla, với tùy chọn đưa vào danh sách đen các vật phẩm cụ thể.
-   **Tăng cường dựa trên quyền hạn:** Người chơi có thể nhận được các đợt tăng cường bổ sung dựa trên quyền hạn của họ.
-   **Hệ thống lệnh linh hoạt:** Các lệnh toàn diện để quản lý các đợt tăng cường (thêm, xóa, xóa tất cả, liệt kê).
-   **Hỗ trợ PlaceholderAPI:** Hiển thị phần trăm tăng cường hiện tại của người chơi bằng cách sử dụng PlaceholderAPI.
-   **Tăng cường liên tục:** Các đợt tăng cường được lưu và tải lại sau khi khởi động lại máy chủ.
-   **Tin nhắn có thể tùy chỉnh:** Tất cả các tin nhắn của plugin có thể được cấu hình thông qua `messages.yml`.

## Cài đặt

1.  Tải xuống tệp `HorizonBoostDrop.jar`.
2.  Đặt tệp `HorizonBoostDrop.jar` vào thư mục `plugins/` của máy chủ của bạn.
3.  (Tùy chọn) Nếu bạn muốn hỗ trợ PlaceholderAPI, hãy đảm bảo PlaceholderAPI cũng được cài đặt.
4.  Khởi động hoặc khởi động lại máy chủ của bạn.
5.  Plugin sẽ tạo `config.yml` và `messages.yml` trong `plugins/HorizonBoostDrop/`.

## Lệnh

Tất cả các lệnh bắt đầu bằng `/boostdrop` hoặc bí danh của nó (nếu được cấu hình).

-   `/boostdrop help`: Hiển thị thông báo trợ giúp của plugin.
-   `/boostdrop <player> <seconds> <percent> [type] [source]`: Cấp một đợt tăng cường rơi vật phẩm tạm thời cho người chơi.
    -   `<player>`: Tên người chơi mục tiêu.
    -   `<seconds>`: Thời lượng của đợt tăng cường tính bằng giây.
    -   `<percent>`: Phần trăm tăng tỷ lệ rơi vật phẩm (ví dụ: `50` cho +50%).
    -   `[type]`: (Tùy chọn) Loại tăng cường (ví dụ: `COMMAND`, `EVENT`). Mặc định là `COMMAND`.
    -   `[source]`: (Tùy chọn) Một định danh tùy chỉnh cho đợt tăng cường (ví dụ: "Phần thưởng hàng ngày"). Mặc định là "Được boost từ <sender_name>".
-   `/boostdrop addperm <player> <percent> [type] [source]`: Cấp một đợt tăng cường rơi vật phẩm vĩnh viễn cho người chơi.
    -   `<player>`: Tên người chơi mục tiêu.
    -   `<percent>`: Phần trăm tăng tỷ lệ rơi vật phẩm.
    -   `[type]`: (Tùy chọn) Loại tăng cường. Mặc định là `COMMAND`.
    -   `[source]`: (Tùy chọn) Một định danh tùy chỉnh cho đợt tăng cường. Mặc định là "Lệnh bởi <sender_name>".
-   `/boostdrop list [player]`: Hiển thị tóm tắt các đợt tăng cường đang hoạt động cho người chơi. Nếu không có người chơi nào được chỉ định, nó sẽ hiển thị các đợt tăng cường của bạn (nếu bạn là người chơi).
-   `/boostdrop remove <player> <source>`: Xóa một đợt tăng cường cụ thể khỏi người chơi dựa trên nguồn của nó.
    -   `<player>`: Tên người chơi mục tiêu.
    -   `<source>`: Định danh của đợt tăng cường cần xóa.
-   `/boostdrop clear <player>`: Xóa tất cả các đợt tăng cường đang hoạt động khỏi người chơi.
-   `/boostdrop reload`: Tải lại các tệp cấu hình của plugin (`config.yml` và `messages.yml`) và dữ liệu tăng cường.

## Quyền hạn

-   `horizonboostdrop.admin`: Cho phép truy cập vào tất cả các lệnh quản trị (`/boostdrop addperm`, `/boostdrop remove`, `/boostdrop clear`, `/boostdrop <player> <seconds> <percent>`).
-   `horizonboostdrop.reload`: Cho phép truy cập vào lệnh `/boostdrop reload`.
-   `horizonboostdrop.boost.<percent>`: Cấp một phần trăm tăng cường tĩnh cho người chơi (ví dụ: `horizonboostdrop.boost.10` cho +10% tăng cường). Đợt tăng cường này được thêm vào bất kỳ đợt tăng cường tạm thời/vĩnh viễn nào đang hoạt động.

## Cấu hình (`config.yml`)

```yaml
# Cấu hình chính của HorizonBoostDrop

# Danh sách đen các MMOItems sẽ không được boost
# Định dạng: <MMOItemType.ID> (ví dụ: SWORD.MYTHIC_SWORD)
blacklist:
  mmoitems:
    - "SWORD.MYTHIC_SWORD"
    - "ARMOR.LEGENDARY_CHESTPLATE"
  # Danh sách đen các vật phẩm vanilla sẽ không được boost
  # Định dạng: <MATERIAL_NAME> (ví dụ: DIAMOND, STONE)
  vanilla:
    - "DIAMOND"
    - "STONE"

# Các cài đặt khác có thể được thêm vào đây trong tương lai
```

## Cấu hình (`messages.yml`)

Tệp này chứa tất cả các tin nhắn hiển thị cho người dùng, cho phép tùy chỉnh hoàn toàn.

Ví dụ:

```yaml
# Tin nhắn cấu hình cho HorizonBoostDrop

no-permission: "&cBạn không có quyền để thực hiện lệnh này."
player-not-found: "&cKhông tìm thấy người chơi %player%."
invalid-number: "&cSố không hợp lệ."
invalid-type: "&cLoại boost không hợp lệ. Các loại hợp lệ: COMMAND, EVENT, PERMISSION."
reload: "&aĐã tải lại cấu hình và dữ liệu boost thành công!"

boost-applied:
  sender: "&aĐã áp dụng boost &e+%percent% &acho &f%player% &aloại &b%type% &athời gian &e%time%."
  player: "&aBạn đã nhận được boost &e+%percent% &aloại &b%type% &athời gian &e%time%."
# ... (nhiều tin nhắn khác)
```

## Hỗ trợ PlaceholderAPI

Nếu PlaceholderAPI được cài đặt, bạn có thể sử dụng các placeholder sau:

-   `%horizonboost_total%`, `%horizonboost_percent%`, `%horizonboost_total_percent%`: Hiển thị tổng phần trăm boost hiện tại của người chơi.
-   `%horizonboost_time%`, `%horizonboost_remaining%`, `%horizonboost_time_left%`: Hiển thị thời gian boost còn lại dài nhất tính bằng giây.
-   `%horizonboost_time_formatted%`, `%horizonboost_remaining_formatted%`: Hiển thị thời gian boost còn lại dài nhất được định dạng (ví dụ: "1h 30p", "45 phút 10s").
-   `%horizonboost_list%`, `%horizonboost_summary%`: Liệt kê tóm tắt các boost đang hoạt động của người chơi.
-   `%horizonboost_count%`, `%horizonboost_amount%`: Hiển thị số lượng boost đang hoạt động.
-   `%horizonboost_status%`, `%horizonboost_has_boost%`: Trả về "yes" nếu người chơi có boost, ngược lại trả về "no".
-   `%horizonboost_percent_raw%`: Hiển thị tổng phần trăm boost dưới dạng số nguyên (không có ký hiệu %).
-   `%horizonboost_top_percent%`: Hiển thị phần trăm của boost cao nhất đang hoạt động.
-   `%horizonboost_top_type%`: Hiển thị loại của boost có phần trăm cao nhất.
