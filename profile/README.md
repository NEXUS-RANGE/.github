<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/NEXUS-RANGE/.github/main/profile/assets/banner-dark.svg">
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/NEXUS-RANGE/.github/main/profile/assets/banner-light.svg">
    <img alt="NEXUS // Range — отечественная платформа киберполигонов" src="https://raw.githubusercontent.com/NEXUS-RANGE/.github/main/profile/assets/banner-dark.svg" width="100%">
  </picture>
</p>

<p align="center">
  <a href="https://nexussec.ru"><img alt="Сайт" src="https://img.shields.io/badge/%D1%81%D0%B0%D0%B9%D1%82-nexussec.ru-2B2B2B?style=for-the-badge&labelColor=0A0A0A"></a>
  <a href="https://t.me/nexus_range"><img alt="Telegram" src="https://img.shields.io/badge/telegram-nexus__range-2B2B2B?style=for-the-badge&logo=telegram&logoColor=white&labelColor=0A0A0A"></a>
  <a href="https://github.com/orgs/NEXUS-RANGE/projects/1"><img alt="Доска задач" src="https://img.shields.io/badge/%D0%B4%D0%BE%D1%81%D0%BA%D0%B0-%D0%B7%D0%B0%D0%B4%D0%B0%D1%87-2B2B2B?style=for-the-badge&logo=github&logoColor=white&labelColor=0A0A0A"></a>
</p>

<br>

**NEXUS** — отечественная платформа киберполигонов. Она разворачивает изолированные учебные стенды по информационной безопасности на обычном сервере вуза или в облаке: преподаватель описывает стенд в одном файле, а студенты работают с ним прямо из браузера.

<br>

## ▍Что умеет платформа

<table>
  <tr>
    <td width="50%" valign="top">
      <b>Стенды как код</b><br>
      <sub>Сети и виртуальные машины описываются декларативным манифестом. Движок сам приводит инфраструктуру к нужному состоянию.</sub>
    </td>
    <td width="50%" valign="top">
      <b>Быстрый запуск</b><br>
      <sub>Машины создаются из эталонных образов по технологии Copy-on-Write: стенд поднимается за минуты и почти не занимает диск.</sub>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <b>Доступ из браузера</b><br>
      <sub>Консоль виртуальной машины открывается во вкладке. Студентам ничего не нужно устанавливать.</sub>
    </td>
    <td width="50%" valign="top">
      <b>Роли и аудит</b><br>
      <sub>Три роли — наблюдатель, оператор, администратор. Каждое действие записывается в журнал аудита.</sub>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <b>Видимость атак</b><br>
      <sub>Запись трафика стендов и алерты Suricata в реальном времени — преподаватель видит, что происходит в сети.</sub>
    </td>
    <td width="50%" valign="top">
      <b>Поиск уязвимостей</b><br>
      <sub>ПО внутри виртуальных машин сверяется с базой уязвимостей — для сценариев атаки и защиты.</sub>
    </td>
  </tr>
</table>

<br>

## ▍Архитектура

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/NEXUS-RANGE/.github/main/profile/assets/architecture-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/NEXUS-RANGE/.github/main/profile/assets/architecture-light.svg">
  <img alt="Архитектура NEXUS: управление, узел киберполигона, наблюдение и анализ" src="https://raw.githubusercontent.com/NEXUS-RANGE/.github/main/profile/assets/architecture-dark.svg" width="100%">
</picture>

<br>

## ▍Компоненты

| Компонент | Что делает | Стек | Статус |
|:--|:--|:--|:--|
| **nexus-web** | Веб-интерфейс платформы | TypeScript | в разработке |
| **API Gateway** | Единая точка входа: пользователи, роли, журнал аудита | Go · PostgreSQL | в разработке |
| **Node Agent** | Управляет виртуальными машинами, дисками и сетями на узле | Go · libvirt | в разработке |
| **PCAP Engine** | Перехватывает сетевой трафик с интерфейсов KVM | Go · gopacket | в разработке |
| [**suri-streamer**](https://github.com/NEXUS-RANGE/suri-streamer) | Читает алерты Suricata из `eve.json` и передаёт их в веб через SSE | Go | открытый код · MIT |
| **Master-образы** | Эталонные диски QCOW2 и скрипты зачистки | QCOW2 · Linux | в разработке |
| **CVE Analyzer** | Опрашивает ПО виртуальных машин и сверяет его с базой уязвимостей | Go · qemu-guest-agent · PostgreSQL | в разработке |

<br>

## ▍Стек

<p>
  <img alt="Go" src="https://img.shields.io/badge/Go-1F1F1F?style=flat-square&logo=go&logoColor=white">
  <img alt="TypeScript" src="https://img.shields.io/badge/TypeScript-1F1F1F?style=flat-square&logo=typescript&logoColor=white">
  <img alt="PostgreSQL" src="https://img.shields.io/badge/PostgreSQL-1F1F1F?style=flat-square&logo=postgresql&logoColor=white">
  <img alt="KVM / QEMU" src="https://img.shields.io/badge/KVM%20%2F%20QEMU-1F1F1F?style=flat-square&logo=qemu&logoColor=white">
  <img alt="libvirt" src="https://img.shields.io/badge/libvirt-1F1F1F?style=flat-square">
  <img alt="Suricata" src="https://img.shields.io/badge/Suricata-1F1F1F?style=flat-square">
  <img alt="Docker" src="https://img.shields.io/badge/Docker-1F1F1F?style=flat-square&logo=docker&logoColor=white">
  <img alt="Linux" src="https://img.shields.io/badge/Linux-1F1F1F?style=flat-square&logo=linux&logoColor=white">
</p>

<br>

## ▍Сейчас в работе · сентябрь — октябрь 2026

- **PCAP Engine** — демон перехвата трафика с интерфейсов KVM
- **Suricata Streamer** — потоковая передача алертов IDS в веб-интерфейс
- **Master-образы** — чистые диски QCOW2 (Kali, Debian, Alpine) и скрипты зачистки
- **CVE Analyzer** — анализ уязвимостей ПО виртуальных машин, архитектура и шлюз

Статус задач — на [доске проекта](https://github.com/orgs/NEXUS-RANGE/projects/1).

<br>

## ▍Как мы работаем

- Бэкенд пишем на Go, интерфейс — на TypeScript.
- Каждая задача живёт на доске проекта и в отдельной ветке.
- Изменения попадают в основную ветку только через pull request и code review.

<br>

<p align="center">
  <sub>
    <a href="https://nexussec.ru">nexussec.ru</a> ·
    <a href="https://t.me/nexus_range">Telegram</a> ·
    <a href="https://github.com/orgs/NEXUS-RANGE/projects/1">Доска задач</a>
  </sub>
  <br>
  <sub>NEXUS · Россия · 2026</sub>
</p>
