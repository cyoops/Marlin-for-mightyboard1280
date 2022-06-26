# Marlin-for-mightyboard1280
2.0.9.3 for mightyboard 1280 (FlashForge Creator 1 Single Extruder)

---

默认配置编译不适用于 1280，会超出 flash 范围。

不再使用 x3g，正式告别GPX，适用 replicator 相关 clone，因 flash 限制，只支持单头（手上正好是单头机器），支持 PLA 吹料风扇

刷机依然需要上传固件时按下 reset 按钮，但比 sailfish 升级还是方便多了。

---

Cura 设置：

X：227

Y：148

Z：150

Rectangular
不要选择置中
选择加热床

G-code: Marlin

---

;START G-CODE;

M104 T0 S{material_print_temperature}

M140 S{material_bed_temperature}

G28

T0

G1 X150 Y-70 Z30 F4800 ; move to wait position left hand side of the table

M190 S{material_bed_temperature}

M109 T0 S{material_print_temperature}

G92 E0

G1 Z0.4 F1800

G1 X110 Y-70 E20 F300 ; purge nozzle

G1 X120 Y-70 Z0.15 F1200 ; slow wipe

G1 X110 Y-70 Z0.5 F1200 ; lift

G92 E0

;START G-CODE;

---

;END G-CODE;

G1 X150 Y75 Z150 F1000 ; send Z axis to bottom of machine

M140 S0; cool down HBP

M104 T0 S0 ; cool down right extruder

M104 T1 S0 ; cool down left extruder

M127 ; stop blower fan

M18 ; disable stepper

;END G-CODE;

---
