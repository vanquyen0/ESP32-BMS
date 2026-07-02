1. LXT
2. 
ESP32 3V3 ──[4.7k]──┐

                    │
GPIO22 DATA ────────┴──── LXT DATA


GPIO27 ENABLE ─────────── LXT ENABLE

ESP32 GND  ────────────── B-
LXT dùng kiểu 1-wire/open-drain nên DATA nên có pull-up 4.7k lên 3.3V.
--------------------------------------------------------------------------------
2. XGT

ESP32 3V3 ──[4.7k]──┐
                    │
GPIO22 DATA ────────┴──── XGT DATA


ESP32 GND  ────────────── B-
XGT cũng nên có pull-up 4.7k lên 3.3V trên đường DATA.
---------------------------------------------------------------------------------
3. HIKOKI
GPIO27 OUT      ───────── HIKOKI OUT


GPIO22 INV OUT  ───────── HIKOKI INV OUT


ESP32 3V3 ──[10k]──┐
                   │
GPIO35 IN  ◀───────┴──── HIKOKI IN


ESP32 GND ─────────────── B-
OUT và INV OUT là ESP32 xuất tín hiệu, thường không cần pull-up.
IN là ESP32 đọc tín hiệu từ pin, nên thêm pull-up 10k lên 3.3V nếu đường pin là open collector/open drain.
GPIO35 chỉ input, dùng đúng cho chân IN.
--------------------------------------------------------------------------------------
4. Milwaukee M18
GPIO22 TX  ────────────── M18 RX / DATA IN


GPIO27 RX  ◀───────────── M18 TX / DATA OUT

ESP32 GND ─────────────── B-
M18 dạng UART TX/RX nên thường không cần pull-up. Nếu muốn bảo vệ thêm:

M18 TX ──[1k]── GPIO27 RX
GPIO22 TX ──[1k]── M18 RX
