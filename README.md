1. LXT
<img width="1184" height="2560" alt="z7999221381471_e064897ebd431bfeeb2e29967d90fa25" src="https://github.com/user-attachments/assets/ad94aa60-9ea2-482a-b576-f56cc0657cd8" />

   
ESP32 3V3 ──[4.7k]──┐

                    
GPIO22 DATA ────────┴──── LXT DATA (2)


GPIO27 ENABLE ─────────── LXT ENABLE (6)

ESP32 GND  ────────────── B-

LXT dùng kiểu 1-wire/open-drain nên DATA nên có pull-up 4.7k lên 3.3V.
--------------------------------------------------------------------------------
2. XGT
   <img width="920" height="690" alt="PIN CONNECT" src="https://github.com/user-attachments/assets/4b13107f-20ca-4a09-81f3-db7d5fd372a5" />


ESP32 3V3 ──[4.7k]──┐

                    
GPIO22 DATA ────────┴──── XGT DATA


ESP32 GND  ────────────── B-

XGT cũng nên có pull-up 4.7k lên 3.3V trên đường DATA.
---------------------------------------------------------------------------------
3. HIKOKI
   <img width="1994" height="1600" alt="wiring" src="https://github.com/user-attachments/assets/23d57b28-bddb-46dd-9d8b-489c94d0ef6e" />


GPIO27 OUT      ───────── HIKOKI OUT


GPIO22 INV OUT  ───────── HIKOKI INV OUT


ESP32 3V3 ──[10k]──┐

                   
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
