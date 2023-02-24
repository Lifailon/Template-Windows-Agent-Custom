# Windows-Agent-Custom
Русифицированная версия стандартного шаблона Zabbix (от 14.08.2022).

## Нагрузочное тестирование дискового массива с целью выявление критических показателей для создания актуальных тригеров:

### Показатели и графики на дисковом массиве при нагрузке **[CrystalDiskMark](https://crystalmark.info/en/software/crystaldiskmark):**

![Image alt](https://github.com/Lifailon/Template-Windows-Agent-Custom/blob/rsa/IOps/IOPS.jpg)

![Image alt](https://github.com/Lifailon/Template-Windows-Agent-Custom/blob/rsa/IOps/IOPS-graf.jpg)

### Тестирование с помощью **[DiskSpd](https://github.com/microsoft/diskspd):**

`diskspd.exe –c8G -d300 -r -w40 -t8 -o32 -b64K -Sh -L testfile1.dat > DiskSpeedResults.txt`

![Image alt](https://github.com/Lifailon/Template-Windows-Agent-Custom/blob/rsa/IOps/IOps-DiskSpd.jpg)

### Тест на локальном диске SSD:

![Image alt](https://github.com/Lifailon/Template-Windows-Agent-Custom/blob/rsa/IOps/IOPS-local-ssd.jpg)

### Сравнение производительности:

![Image alt](https://github.com/Lifailon/Template-Windows-Agent-Custom/blob/rsa/IOps/CrystalDiskMark-Comparison.jpg)

![Image alt](https://github.com/Lifailon/Template-Windows-Agent-Custom/blob/rsa/IOps/MSI-M390.jpg)
