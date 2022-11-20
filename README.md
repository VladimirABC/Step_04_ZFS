1. Сcылка на репозиторий GitHub.
https://github.com/VladimirABC/Step_04_ZFS

2. Vagrantfile с Bash-скриптом, который будет конфигурировать сервер
По ссылке п.1

3. Документация по каждому заданию:

1) Определить алгоритм с наилучшим сжатием

== набор команд ==
    1  zpool create otus1 mirror /dev/sdb /dev/sdc
    2  zpool create otus2 mirror /dev/sdd /dev/sde
    3  zpool create otus3 mirror /dev/sdf /dev/sdg
    4  zpool create otus4 mirror /dev/sdh /dev/sdi
    5  zpool list
    6  zpool
    7  zpool-status
    8  zpool status
    9  zfs set compression=lzjb otus1
   10  zfs set compression=lz4 otus2
   11  zfs set compression=gzip-9 otus3
   12  zfs set compression=zle otus4
   13  zfs get all 
   14  zfs get all | grep compr
   15  for i in {1..4}; do wget -P /otus$i https://gutenberg.org/cache/epub/2600/pg2600.converter.log; done
   16  yum install tree -y
   17  tree /otus*
   18  ls -al /otus*/pg*
   19  ls -al /otus*/pg
   20  ls -al /otus*/*
   21  ls -al /otus*
   22  ls -l /otus*
   23  zfs list
   24  dd if=/dev/urandom of=random bs=50M count=1
   25  for i in {1..4}; do cp ./random /otus$i; ; done
   26  for i in {1..4}; do cp ./random /otus$i; done
   27  tree /otus*
   28  zfs list
   29  zfs get all | grep compress
===

Лучшее сжатие даёт алгоритм gzip-9.

2) Определить настройки пула
Вывод всех настроек пула даёт - zpool get all otus

== набор команд ==
   48  zpool import -d zpoolexport/otus
   49  zpool status
   50  zpool get all otus
   51  zfs get available otus
   52  zfs get free otus
   53  zfs get used otus
   54  zfs get used otus1
   55  zfs get used otus*
   57  for i in {1..4}; do zfs get used otus$i; done
   58  zfs get readonly otus
   59  zfs get recordsize otus
   60  zfs get compression otus
   61  zfs get checksum otus
===

3) Работа со снапшотами

== набор команд ==
   62  wget -O otus_task2.file --no-check-certificate "https://drive.google.com/u/0/uc?id=1gH8gCL9y7Nd5Ti3IRmplZPF1XjzxeRAG&export=download"
   63  ll
   64  zfs receive otus/test@today < ./otus_task2.file
   65  lsblk
   66  zfs list
   67  zfs status
   68  zpool status
   69  find /otus/test -name "secret" 
   70  ls /otus/test
   71  ls /otus/test/task1/
   72  ls /otus/test/task1/file_mess/
   73  cat /otus/test/task1/file_mess/secret_message 
== результат ==
[root@server ~]# cat /otus/test/task1/file_mess/secret_message 
https://github.com/sindresorhus/awesome
==

