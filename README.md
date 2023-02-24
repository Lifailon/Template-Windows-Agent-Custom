# Windows-Agent-Custom
Русифицированная версия стандартного шаблона Zabbix (от 14.08.2022).

## Нагрузочное тестирование дискового массива с целью анализа критических показателей для создания актуальных тригеров.

### Показатели и графики на дисковом массиве при нагрузке **[CrystalDiskMark](https://crystalmark.info/en/software/crystaldiskmark):**

`SEQ1M` запись контрольного файла будет производиться последовательно (Sequential), как и его чтение, с размером блока 1МБайт. Именно результат теста Seq Q32T1 стоит сравнивать со скоростью носителя, указанной производителем. \
`RND4K (Random 4KiB) Q32T1` лучше использовать для тестирования раздела диска с операционной системой, т.к. ОС в основном работает с небольшими блоками данных, а тестирование будет производиться блоками размером 4 КБ при единственном потоке с глубиной очереди 32. \
`Потоки (Threads)` количество одновременно выполняемых операций чтения/записи, увеличение этого параметра приводит к повышению нагрузки на носитель. \
`Глубина очереди` число запросов, обрабатываемых тестируемым накопителем. Чем больше глубина, тем больший объём информации будет обработан диском. \
Если кэш диска 4-8 Gb, то нужен файл размером больше кэша.

![Image alt](https://github.com/Lifailon/Template-Windows-Agent-Custom/blob/rsa/IOps/IOPS.jpg)

![Image alt](https://github.com/Lifailon/Template-Windows-Agent-Custom/blob/rsa/IOps/IOPS-graf.jpg)

### Тестирование с помощью **[DiskSpd](https://github.com/microsoft/diskspd):**

`diskspd.exe –c8G -d300 -r -w40 -t8 -o32 -b64K -Sh -L testfile1.dat > DiskSpeedResults.txt` \
`-c8G` размер файла 8 Гб (лучше использовать большой размер файла, чтобы он не поместился в кэш контроллера СХД) \
`-d300` продолжительность тестирования в секундах (5 минут) \
`-r` произвольное чтение/запись (если нужно тестировать последовательный доступ, используется –s) \
`-t8` количество потоков \
`-w40` соотношение операций записи к операциям чтения 40% / 60% \
`-o32` длина очереди \
`-b64K` размер блока \
`-Sh` не использовать кэширование \
`-L` измерять задержки (Latency)

![Image alt](https://github.com/Lifailon/Template-Windows-Agent-Custom/blob/rsa/IOps/IOps-DiskSpd.jpg)

### Тест на локальном диске SSD:

![Image alt](https://github.com/Lifailon/Template-Windows-Agent-Custom/blob/rsa/IOps/IOPS-local-ssd.jpg)

### Сравнение производительности:

![Image alt](https://github.com/Lifailon/Template-Windows-Agent-Custom/blob/rsa/IOps/CrystalDiskMark-Comparison.jpg)

![Image alt](https://github.com/Lifailon/Template-Windows-Agent-Custom/blob/rsa/IOps/MSI-M390.jpg)
