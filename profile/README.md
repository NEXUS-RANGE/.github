<img alt="NEXUS // Range — оркестрация изолированных киберполигонов на базе KVM" src="https://raw.githubusercontent.com/NEXUS-RANGE/.github/main/profile/assets/banner.svg" width="100%">

<p align="center">
  <a href="https://nexussec.ru"><img alt="Сайт" src="https://img.shields.io/badge/%D1%81%D0%B0%D0%B9%D1%82-nexussec.ru-2B2B2B?style=for-the-badge&labelColor=0A0A0A"></a>
  <a href="https://t.me/nexus_range"><img alt="Telegram" src="https://img.shields.io/badge/telegram-nexus__range-2B2B2B?style=for-the-badge&logo=telegram&logoColor=white&labelColor=0A0A0A"></a>
  <a href="https://github.com/orgs/NEXUS-RANGE/projects/1"><img alt="Доска задач" src="https://img.shields.io/badge/%D0%B4%D0%BE%D1%81%D0%BA%D0%B0-%D0%B7%D0%B0%D0%B4%D0%B0%D1%87-2B2B2B?style=for-the-badge&logo=github&logoColor=white&labelColor=0A0A0A"></a>
</p>

<p align="center">
  <img alt="Go 1.22" src="https://img.shields.io/badge/Go-1.22-30363d?style=flat-square&logo=go&logoColor=white&labelColor=0d1117">
  <img alt="KVM / libvirt" src="https://img.shields.io/badge/KVM-libvirt-30363d?style=flat-square&logo=qemu&logoColor=white&labelColor=0d1117">
  <img alt="PostgreSQL" src="https://img.shields.io/badge/PostgreSQL-14%2B-30363d?style=flat-square&logo=postgresql&logoColor=white&labelColor=0d1117">
  <img alt="Linux" src="https://img.shields.io/badge/Linux-host-30363d?style=flat-square&logo=linux&logoColor=white&labelColor=0d1117">
  <img alt="MITRE ATT&CK" src="https://img.shields.io/badge/MITRE%20ATT%26CK-%D1%80%D0%B0%D0%B7%D0%BC%D0%B5%D1%82%D0%BA%D0%B0-30363d?style=flat-square&labelColor=0d1117">
  <img alt="Suricata — в разработке" src="https://img.shields.io/badge/Suricata-%D0%B2%20%D1%80%D0%B0%D0%B7%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%BA%D0%B5-30363d?style=flat-square&labelColor=0d1117">
</p>

<p align="center"><b>Настоящие виртуальные машины, изолированная сеть и стенд на всю группу.<br>Из браузера, одним кликом.</b></p>

<br>

<img alt="Конструктор стенда: машины из образов сервера, связи, консоль студента и принятый флаг" src="https://raw.githubusercontent.com/NEXUS-RANGE/.github/main/profile/assets/hero.png" width="100%">

## Зачем

Контейнер делит ядро с хостом, и уязвимость ядра выводит из него прямо на сервер. Windows в нём не запустить. Классическая ВМ честная, но стенд на группу означает часы установки или тридцать полных копий образа на диске.

NEXUS берёт лучшее от обоих: у каждой машины своё ядро на KVM, а клон создаётся мгновенно и почти не занимает места.

|                   | Контейнеры                 | Классические ВМ                 | NEXUS                              |
| ----------------- | -------------------------- | ------------------------------- | ---------------------------------- |
| Ядро              | общее с хостом             | своё                            | своё, KVM                          |
| Гостевые ОС       | только Linux-процессы      | любые                           | любые, из образов вашего сервера   |
| Стенд на 30 человек | быстро, но это не машины | часы или 30 полных копий        | 30 тонких клонов одного образа     |
| Сеть              | общий мост Docker          | настраивается руками            | своя сеть у каждого стенда, без маршрута наружу |

## Что внутри

<table>
<tr>
<td width="50%" valign="top">

<img src="https://raw.githubusercontent.com/NEXUS-RANGE/.github/main/profile/assets/icons/layers.svg" width="22" alt=""><br>
**Copy-on-write в два уровня**

- Образ сервера → шаблон лабы → клон студента. Каждый уровень — тонкая дельта qcow2.
- Тридцать машин из одного образа — тридцать почти пустых файлов.
- Шаблон, на котором стоят клоны, удалить нельзя: система не даст сломать диски студентов.

</td>
<td width="50%" valign="top">

<img src="https://raw.githubusercontent.com/NEXUS-RANGE/.github/main/profile/assets/icons/terminal.svg" width="22" alt=""><br>
**Консоль без клиента**

- noVNC в браузере по WebSocket. Ни VNC-клиента, ни VPN.
- Одноразовые тикеты на подключение. Порты VNC наружу не открываются.
- Студент видит только свои машины. Чужая — 404.

</td>
</tr>
<tr>
<td width="50%" valign="top">

<img src="https://raw.githubusercontent.com/NEXUS-RANGE/.github/main/profile/assets/icons/shield.svg" width="22" alt=""><br>
**Изоляция стенда**

- У сети стенда нет маршрута наружу. nwfilter отрезает гостю все адреса хоста.
- ARP-спуфинг и подмена адресов внутри стенда разрешены: это часть упражнения.
- Квоты на машины, vCPU и память у каждой группы.

</td>
<td width="50%" valign="top">

<img src="https://raw.githubusercontent.com/NEXUS-RANGE/.github/main/profile/assets/icons/package.svg" width="22" alt=""><br>
**Свой образ за минуты**

- Преподаватель включает машину и настраивает её руками в консоли.
- Одна кнопка — очистка virt-sysprep и новый шаблон лабы.
- Сессия настройки живёт 2 часа в отдельной сети с защитой от подмены MAC.

</td>
</tr>
</table>

Сценарии размечены по тактикам и техникам MITRE ATT&CK. Флаги проверяются автоматически, баллы и ведомость группы обновляются сами.

**В разработке.** Захват трафика стенда прямо в браузере с разбором протоколов, включая Modbus/TCP: API и интерфейс готовы, сервер захвата — следующий. Алерты Suricata в интерфейсе в реальном времени: стример [suri-streamer](https://github.com/NEXUS-RANGE/suri-streamer) уже открыт под MIT. Привязка к ATT&CK — за ним.

---

<p align="center">
  <sub>
    <a href="https://nexussec.ru">nexussec.ru</a> ·
    <a href="https://t.me/nexus_range">Telegram</a> ·
    <a href="https://github.com/orgs/NEXUS-RANGE/projects/1">Доска задач</a>
  </sub>
  <br>
  <sub><b>Made in Dagestan</b></sub>
  <br>
  <sub>NEXUS // Range — для обучения и отработки защиты. Атаки выполняются только внутри изолированного стенда.</sub>
</p>
