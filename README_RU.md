# gowebly – CLI-инструмент нового поколения для создания потрясающих веб-приложений на языке Go с использованием htmx и hyperscript

[![Go version][go_version_img]][go_dev_url]
[![Go report][go_report_img]][go_report_url]
[![Code coverage][go_code_coverage_img]][repo_url]
[![License][repo_license_img]][repo_license_url]

[English][repo_url] | **Русский** | [中文][repo_readme_cn_url] | 
[Español][repo_readme_es_url]

С помощью этого CLI-инструмента можно легко создавать потрясающие 
веб-приложения на **Go** в качестве бэкенда с использованием 
[**htmx**][htmx_url] и [**hyperscript**][hyperscript_url], а также, с наиболее 
популярными atomic/utility-first **CSS-фреймворками** на фронтенде.

Особенности:

- 100% **свободный** и с **открытым исходным кодом** под лицензией
  [Apache 2.0][repo_license_url].
- Для **любого** уровня знаний и технической экспертизы разработчика.
- Помогает быстрее начать использовать стек технологий **Go** + **htmx** + 
  **hyperscript**.
- Умный CLI, который делает **бóльшую часть** рутинной настройки и 
  подготовки для продакшена.
- Возможность простого добавления в проект atomic/utility-first 
  **CSS-фреймворка**;
- Содержит исчерпывающий **пример** использования из коробки.
- **Хорошо документирован**, с большим количеством советов и подсказок от 
  авторов.

## ⚡️ Быстрый старт

Сначала [скачайте][go_download_url] и установите **Go**. Требуется версия 
`1.21` (или выше).

Теперь вы можете использовать `gowebly` без установки. Просто запустите команду 
[`go run`][go_run_url], чтобы создать новый проект с файлом 
[конфигурации][repo_default_config] по умолчанию:

```console
go run github.com/gowebly/gowebly@latest create
```

Вот и все! 🔥 Замечательное веб-приложение, использующее встроенный пакет 
**net/http** (в качестве Go-бэкенда), **htmx**, **hyperscript** и **UnoCSS** 
(в качестве CSS-фреймворка), доступно в ваших HTML-шаблонах Go.

### 🔹 Быстрый старт с помощью полной Go установки

Если вы, всё же, хотите установить `gowebly` CLI в свою систему средствами 
Golang, воспользуйтесь командой [`go install`][go_install_url]:

```console
go install github.com/gowebly/gowebly@latest
```

### 🍺 Быстрый старт с помощью Homebrew

Пользователи GNU/Linux и Apple macOS могут установить `gowebly` CLI с 
помощью [Homebrew][brew_url].

Добавьте новую формулу:

```console
brew tap gowebly/tap
```

Установите `gowebly`:

```console
brew install gowebly/tap/gowebly
```

### 🐳 Быстрый старт с помощью Docker

Не стесняйтесь использовать `gowebly` CLI с помощью нашего 
[официального Docker-образа][docker_image_url], чтобы запускать его в 
изолированном контейнере:

```console
docker run --rm -it -v ${PWD}:${PWD} -w ${PWD} gowebly/gowebly:latest create
```

### 📦 Другой способ быстрого старта

На странице [Releases][repo_releases_url] вы можете скачать готовые файлы 
`exe` для Windows, `deb`, `rpm`, `apk` или Arch Linux пакеты.

## 📖 Полное руководство пользователя

Чтобы получить полное руководство по использованию и понять основные 
принципы работы с `gowebly` CLI, мы подготовили исчерпывающее объяснение 
каждой команды сразу в этом файле README.

> ⚡️ От авторов: Мы всегда ценим ваше время и хотим, чтобы вы как можно 
> скорее начали создавать действительно замечательные веб-продукты на этом 
> потрясающем технологическом стеке!

Мы надеемся, что вы найдете ответы на все свои вопросы! 👌 Но, если вы не нашли 
нужной информации, не стесняйтесь создать [issue][repo_issues_url] или 
отправить [PR][repo_pull_request_url] в этот репозиторий.

### `init`

Команда для создания файла конфигурации **по умолчанию** 
([`.gowebly.yml`][repo_default_config]) в текущей папке.

```console
gowebly init
```

> 💡 Примечание: Конечно, вы можете пропустить этот шаг, если вас устраивает 
> следующая конфигурация по умолчанию для вашего нового проекта:
>
> - Go-бэкенд с пакетом **net/http**;
> - Последние версии **htmx** и **hyperscript**;
> - Последняя версия **UnoCSS** (в качестве CSS-фреймворка).

Как правило, созданный конфигурационный файл содержит следующие параметры:

```yaml
backend:
  name: default
  port: 5000
  timeout:
    read: 5
    write: 10
  
frontend:
  htmx: latest
  hyperscript: latest
  css:
    framework: unocss
    version: latest
```

Но вы можете выбрать любой **Go-бэкенд** с параметрами сервера для вашего 
проекта (_это обязательно_):

| Имя Go-бэкенда | Описание                                                                |
|----------------|-------------------------------------------------------------------------|
| `default`      | Использование Go-бэкенда со встроенным пакетом [net/http][net_http_url] |
| `fiber`        | Использование Go-бэкенда с веб-фреймворком [Fiber][fiber_url]           |
| `echo`         | Использование Go-бэкенда с веб-фреймворком [Echo][echo_url]             |
| `chi`          | Использование Go-бэкенда с композитным маршрутизатором [chi][chi_url]   |

Кроме того, вы можете выбрать для своего проекта версии **htmx**, 
**hyperscript** и один из самых популярных atomic/utility-first 
**CSS-фреймворков** (_это опционально, не обязательно_):

| Имя CSS-фреймворка | Описание                                                                |
|--------------------|-------------------------------------------------------------------------|
| `tailwindcss`      | Использование [Tailwind CSS][tailwindcss_url] в качестве CSS-фреймворка |
| `unocss`           | Использование [UnoCSS][unocss_url] в качестве CSS-фреймворка            |

### `create`

Команда для создания нового проекта с **Go-бэкендом**, **htmx**, 
**hyperscript**, и (_опционально_) atomic/utility-first **CSS-фреймворком**.

```console
gowebly create
```

> 💡 Примечание: Если не выполнить команду `init` для создания 
> конфигурационного файла (`.gowebly.yml`), то по умолчанию `gowebly` CLI 
> создает новый проект с конфигурацией [по умолчанию][repo_default_config].

### `run`

Команда для запуска проекта в режиме **разработки** (не продакшен).

```console
gowebly run
```

> 💡 Примечание: Если не выполнить команду `init` для создания
> конфигурационного файла (`.gowebly.yml`), то по умолчанию `gowebly` CLI
> запускает ваш проект с конфигурацией [по умолчанию][repo_default_config].

В HTML-шаблонах Go будут использованы следующие версии библиотек:

- **htmx**: последняя не продакшен версия с CDN;
- **hyperscript**: последняя не продакшен версия с CDN;
- (_опционально_) **CSS-фреймворк**: последняя не продакшен версия с CDN;

В режиме разработки будут использованы только официальные CDN, которые
поддерживаются самими разработчиками:

- [unpkg.com][unpkg_url] для **htmx** и **hyperscript**;
- [tailwindcss.com][tailwindcss_cdn_url] для **Tailwind CSS**;
- [jsDelivr][jsdelivr_url] для **UnoCSS**.

Каждый раз, когда вы выполняете команду `run` для своего проекта:

1. CLI проверяет конфигурацию и применяет все настройки к текущему проекту;
2. CLI внедряет CDN-версии **htmx** и **hyperscript** в ваши Go HTML-шаблоны 
   в обычном теге `<script>` в блок `gowebly-body-scripts` (обычно он 
   размещается в самом низу тега `<body>`);
3. (_опционально_) CLI встраивает CDN-версию выбранного **CSS-фреймворка** в 
   ваши Go HTML-шаблоны в обычном теге `<link>` в блок `gowebly-head-styles` 
   (обычно он размещается в самом низу тега `<head>`);
4. CLI запускает бэкенд проекта (порт `5000`) с помощью простой команды 
   `go run`.

### `build`

Команда для сборки проекта для **продакшена** и подготовки контейнеров к 
развертыванию.

```console
gowebly build
```

> 💡 Примечание: Если не выполнить команду `init` для создания
> конфигурационного файла (`.gowebly.yml`), то по умолчанию `gowebly` CLI
> подготавливает ваш проект с конфигурацией [по умолчанию][repo_default_config].

В HTML-шаблонах Go будут использованы следующие версии библиотек:

- **htmx**: минифицированная продакшен версия, которую вы указали в 
  конфигурационном файле;
- **hyperscript**: минифицированная продакшен версия, которую вы указали в
  конфигурационном файле;
- (_опционально_) **CSS-фреймворк**: последняя минифицированная продакшен 
  версия после tree-shaking;

Каждый раз, когда вы выполняете команду `build` для своего проекта:

1. CLI проверяет конфигурацию и применяет все настройки к текущему проекту;
2. CLI загружает минимизированные версии **htmx** и **hyperscript** с 
   официальных (и доверенных) ресурсов;
   - Происходит их встройка в HTML-шаблоны Go (в стиле inline) в блок под 
     названием `gowebly-body-scripts` (обычно он размещается в самом низу тега 
     `<body>`);
3. (_опционально_) CLI подготавливает минифицированную (и tree-shaking) версию 
   выбранного **CSS-фреймворка** с помощью инструмента [Vite][vite_url];
   - Происходит его встройка в HTML-шаблоны Go (в стиле inline) в блок под 
     названием `gowebly-head-styles` (обычно он размещается в самом низу тега 
     `<head>`);
4. CLI генерирует понятный и хорошо документированный файл
   `docker-compose.yml` в корневой папке проекта для последующего его 
   разворачивания в изолированных Docker-контейнерах через
   [Portainer][portainer_url] (_рекомендуется_), или в ручном режиме, на 
   удаленном сервере.

## 🎯 Мотивация к созданию

Скажите, как часто вам приходилось начинать новый проект с нуля и делать 
мучительные ручные настройки? 🤔 Особенно, когда вы только начинаете знакомиться 
с новой технологией или стеком, где все для вас в новинку.

Для многих разработчиков, _в том числе и для нас_, этот процесс является 
максимально утомительным и даже унылым, не несущим никакой полезной нагрузки.
Это **очень** неприятный процесс, который может сильно оттолкнуть любого 
разработчика от технологии.

Так почему бы не отдать всю эту ужасную ручную работу машинам? Пусть они 
сделают всю тяжелую работу за нас, а мы будем просто создавать потрясающие 
веб-продукты и не думать о сборке и развертывании.

Именно поэтому мы и создали `gowebly` CLI, который помогает вам начинать 
потрясающие веб-приложения на языке **Go** с использованием **htmx**, 
**hyperscript** и популярных atomic/utility-first **CSS-фреймворков**.

Мы здесь для того, чтобы избавить вас (_и себя_) от этой рутинной боли! ✨

## 🏆 Взаимовыгодное сотрудничество

А теперь, я приглашаю вас принять участие в этом проекте! Давайте работать 
**вместе**, чтобы создать **самый полезный** инструмент для разработчиков в 
Интернете на сегодняшний день.

- [Issues][repo_issues_url]: задавайте вопросы и предлагайте свои улучшения.
- [Pull requests][repo_pull_request_url]: присылайте свои улучшения.

Ваши PR и вопросы приветствуются! Спасибо 😘

## ⚠️ Лицензия

[`gowebly`][repo_url] — это свободное программное обеспечение с открытым 
исходным кодом, лицензируемое по лицензии [Apache 2.0][repo_license_url], 
созданное и поддерживаемое [Vic Shóstak][author_url] с 🩵 к людям и роботам.

<!-- Go links -->

[go_download_url]: https://golang.org/dl/
[go_run_url]: https://pkg.go.dev/cmd/go#hdr-Compile_and_run_Go_program
[go_install_url]: https://golang.org/cmd/go/#hdr-Compile_and_install_packages_and_dependencies
[go_report_url]: https://goreportcard.com/report/github.com/gowebly/gowebly
[go_dev_url]: https://pkg.go.dev/github.com/gowebly/gowebly
[go_version_img]: https://img.shields.io/badge/Go-1.21+-00ADD8?style=for-the-badge&logo=go
[go_code_coverage_img]: https://img.shields.io/badge/code_coverage-0%25-success?style=for-the-badge&logo=none
[go_report_img]: https://img.shields.io/badge/Go_report-A+-success?style=for-the-badge&logo=none

<!-- Repository links -->

[repo_url]: https://github.com/gowebly/gowebly
[repo_issues_url]: https://github.com/gowebly/gowebly/issues
[repo_pull_request_url]: https://github.com/gowebly/gowebly/pulls
[repo_releases_url]: https://github.com/gowebly/gowebly/releases
[repo_license_url]: https://github.com/gowebly/gowebly/blob/main/LICENSE
[repo_license_img]: https://img.shields.io/badge/license-Apache_2.0-red?style=for-the-badge&logo=none
[repo_readme_ru_url]: https://github.com/gowebly/gowebly/blob/main/README_RU.md
[repo_readme_cn_url]: https://github.com/gowebly/gowebly/blob/main/README_CN.md
[repo_readme_es_url]: https://github.com/gowebly/gowebly/blob/main/README_ES.md
[repo_default_config]: https://github.com/gowebly/gowebly/blob/main/internal/attachments/configs/default.yml

<!-- Author links -->

[author_url]: https://github.com/koddr

<!-- Readme links -->

[docker_image_url]: https://hub.docker.com/repository/docker/gowebly/gowebly
[portainer_url]: https://docs.portainer.io
[brew_url]: https://brew.sh
[vite_url]: https://vitejs.dev
[htmx_url]: https://htmx.org
[hyperscript_url]: https://hyperscript.org
[tailwindcss_url]: https://tailwindcss.com
[tailwindcss_cdn_url]: https://tailwindcss.com/docs/installation/play-cdn
[unocss_url]: https://unocss.dev
[unpkg_url]: https://unpkg.com
[jsdelivr_url]: https://www.jsdelivr.com
[net_http_url]: https://pkg.go.dev/net/http
[fiber_url]: https://github.com/gofiber/fiber
[echo_url]: https://github.com/labstack/echo
[chi_url]: https://github.com/go-chi/chi
