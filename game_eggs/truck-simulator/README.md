# วิธีการตั้งค่า ETS2 Dedicated Server


พอร์ตด้านล่างเป็นพอร์ตเริ่มต้นที่เชื่อมโยงกับเซิร์ฟเวอร์เฉพาะ ETS2.

| Port     | default       |
|----------|---------------|
| Dedicated| 27015         |
| Query    | 27016         |

# การกำหนดค่า
คุณต้องสร้างไฟล์คอนฟิกเซิร์ฟเวอร์ที่จำเป็นเพื่อเรียกใช้เซิร์ฟเวอร์ในเกมบน ETS2 ในการทำเช่นนั้นคุณต้องเปิดใช้งานคอนโซล
## Enabling Console
ในการเปิดใช้งานคอนโซลของคุณ คุณต้องเปลี่ยนค่า 2 ค่าในไฟล์ config.cfg ไคลเอ็นต์ เมื่อปิดเกม ให้เปลี่ยนสิ่งต่อไปนี้:

```
g_developer "0" -----> g_developer "1"
g_console "0" -----> g_console "1"
```
# ไฟล์ที่จำเป็นเพื่อเรียกใช้เซิร์ฟเวอร์เฉพาะ

ในโฟลเดอร์โฮมของเซิร์ฟเวอร์/เกม ไฟล์ต่อไปนี้ใช้เพื่อตั้งค่าเซสชันเซิร์ฟเวอร์เฉพาะ:
```
server_packages.sii
server_packages.dat
```
server_packages.sii และ server_packages.dat ต้องสร้างด้วยตนเองผ่านการเรียกคำสั่ง `export_server_packages` ในขณะที่เกมปกติกำลังทำงานอยู่ การกำหนดค่าที่สร้างขึ้นจะสะท้อนการกำหนดค่าเกมของคุณ ไฟล์เหล่านี้จำเป็นสำหรับการเริ่มเซิร์ฟเวอร์เฉพาะ หากคุณใช้งานเซิร์ฟเวอร์โดยไม่ได้ติดตั้งเกมพื้นฐานไว้ คุณต้องคัดลอกไฟล์เหล่านี้ด้วยตนเองไปยังโฮมไดเร็กทอรีของเซิร์ฟเวอร์

ไฟล์เหล่านี้ไม่ได้เชื่อมโยงกับบัญชีของคุณแต่อย่างใด

อัพโหลดไปวางใน

( /home/container/.local/share/Euro Truck Simulator 2 )
# การเพิ่มผู้ดูแล

หากต้องการเพิ่มผู้ดูแลให้กับอินสแตนซ์เซิร์ฟเวอร์ของคุณ คุณต้องแก้ไข ให้เข้าไปที่

( /home/container/.local/share/Euro Truck Simulator 2/server_config.sii)

ตัวอย่างที่เห็นด้านล่าง:

```
 moderator_list: 2
 moderator_list[0]: 123456789
 moderator_list[1]: 234567891
 ```
^^^ สามารถพบได้โดย googling Steam ID ค้นหา

**https://help.steampowered.com/th/faqs/view/2816-BE67-5B69-0FEC**
## ตัวอย่าง
```
SiiNunit
{
server_config : _nameless.54e.4440 {
 lobby_name: "Euro Truck Simulator 2 server"            // Session name, limited to 63 characters. ชื่อห้องหรือเซิร์ฟเวอร์
 description: ""                                        // Session description, limited to 63 characters.
 welcome_message: ""                                    // Session welcome message, limited to 127 characters.
 password: ""                                           // Session password, limited to 63 characters.
 max_players: 8                                         // Maximum players in session, limit is 8 players.
 max_vehicles_total: 100
 max_ai_vehicles_player: 50
 max_ai_vehicles_player_spawn: 50
 connection_virtual_port: 100                           // Don't change here. ตรงนี้ห้ามเปลี่ยน
 query_virtual_port: 101                                // Don't change here. ตรงนี้ห้ามเปลี่ยน
 connection_dedicated_port: 27015                       // Don't change here. ตรงนี้ห้ามเปลี่ยน
 query_dedicated_port: 27016                            // Don't change here. ตรงนี้ห้ามเปลี่ยน
 server_logon_token:  ""                                // Token for game server login (persistent account).
 player_damage: true                                    // Flag if player can receive damage from other players.
 traffic: true                                          // Flag if traffic is enabled.
 hide_in_company: false                                 // Flag if remote player are hidden in company area.
 hide_colliding: true                                   // Flag to hide colliding vehicle after teleport. 
 force_speed_limiter: false                             // Flag to force speed limiter.
 mods_optioning: false                                  // Flag to enable mods marked as optional, to be really optional.
 timezones: 0                                           // Values 0 - 2.
 service_no_collision: false                            // Disable collisions on service area.
 in_menu_ghosting: false                                // Disable collisions when game paused.
 name_tags: true                                        // Show player name tags above vehicles.
 friends_only: false                                    // Not used for dedicated server.
 show_server: true                                      // Not used for dedicated server.
 moderator_list: 2                                      // Default moderators. ตัวเลขตามจำนวนผู้ดูแล
 moderator_list[0]: 123456789                           // User steam id. เปลี่ยนเป็นไอดีผู้ดูแลในเกม 1
 moderator_list[1]: 234567891                           // User steam id. เปลี่ยนเป็นไอดีผู้ดูแลในเกม 2
}

}
```
# เพลิดเพลินกับเซิร์ฟเวอร์ของคุณ
เมื่อไฟล์เหล่านั้นได้รับการอัปโหลดและกำหนดค่าแล้ว คุณสามารถเริ่มต้นเซิร์ฟเวอร์ของคุณได้อย่างอิสระ เมื่อเซิฟเวอร์เริ่มขึ้น ให้มองหาบรรทัด: Session search id: 00000000000000000/101 ตัวเลขที่อยู่หน้า / คือคำค้นหาของคุณ นี่คือหมายเลขสำหรับค้นหาในหน้าจอขบวนรถเพื่อค้นหาเซิร์ฟเวอร์ของคุณ คุณไม่สามารถค้นหาด้วยชื่อเซิร์ฟเวอร์ได้ในขณะนี้ ตัวอย่าง: ถ้าหมายเลขของคุณก่อน / คือ 987654321 คุณจะต้องค้นหา 987654321 บนหน้าจอขบวนรถในเกม

# โทเค็นเซิร์ฟเวอร์ Steam

 --**จำเป็นต้องใช้โทเค็นเซิร์ฟเวอร์ Steam**--
 
การเพิ่มโทเค็นเซิร์ฟเวอร์ที่ได้รับจากการลงทะเบียนเซิร์ฟเวอร์ของคุณที่ https://steamcommunity.com/dev/managegameservers ต้องแน่ใจว่าใช้ App ID ที่ถูกต้อง มิฉะนั้นเซิร์ฟเวอร์ของคุณจะหยุดทำงานเมื่อเริ่มต้น.

กรอกหมายเลขของยูโรทัก
```
Euro Truck Sim 2 = 227300
```

# ข้อจำกัดความรับผิดชอบ
ฉันไม่ได้อ้างว่ารู้ทุกอย่างเกี่ยวกับการตั้งค่านี้ เพราะฉันเพิ่งทำให้มันทำงานได้อย่างน่าเชื่อถือ และจะอัปเดตไข่หากมีอะไรเปลี่ยนแปลง ดังที่ได้กล่าวไปแล้ว หากคุณมีปัญหาก็เปิดประเด็นขึ้นมา และฉันจะช่วยเหลืออย่างเต็มที่หากมีเวลา

**https://discord.gg/qc57aSRqqV**
