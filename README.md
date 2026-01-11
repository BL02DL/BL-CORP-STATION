<p align="center"><img src="https://raw.githubusercontent.com/Lost-Paradise-Project/Main-Station/master/Resources/Textures/_LP/Logo/splashlogo.png" width="512px" /></p>

---

Lost Paradise — это форк [Einstein Engines](https://github.com/Simple-Station/Einstein-Engines).

Space Station 14 во многом вдохновлена Space Station 13 и работает на [Robust Toolbox](https://github.com/space-wizards/RobustToolbox) — движке собственной разработки, написанном на C#.

## Links

[Сайт](https://wiki.lost-paradise.space) | [Discord](https://wiki.lost-paradise.space/discord) | [Steam(SSMV Launcher)](https://store.steampowered.com/app/2585480/Space_Station_Multiverse/) | [Steam(WizDen Launcher)](https://store.steampowered.com/app/1255460/Space_Station_14/) | [Standalone](https://spacestationmultiverse.com/downloads/)

## Участие в разработке

Мы рады любой помощи! Если вы хотите внести свой вклад, заходите в наш Discord.
У нас есть [список задач](https://github.com/Lost-Paradise-Project/Main-Station/issues), требующих выполнения — любой желающий может взять их в работу. И не стесняйтесь просить помощи в Discord, если она вам понадобится!

В данный момент мы принимаем переводы игры в нашем основном репозитории.
Если вы хотите перевести игру на другой язык, загляните в канал #contributor-general в нашем Discord.

## Сборка

Для получения общей информации по настройке среды разработки обратитесь к [руководству Space Wizards](https://docs.spacestation14.com/en/general-development/setup/setting-up-a-development-environment.html). Однако имейте в виду, что Lost Paradise отличается от оригинала, и многие вещи могут быть неприменимы.
Для упрощения процесса мы подготовили несколько скриптов, которые приведены ниже.

### Build dependencies

> - Git
> - .NET SDK 9.0.101

### Windows

> 1. Клонируйте репо
> 2. Запустите `git submodule update --init --recursive` в консоли, чтобы обновить движок
> 3. Запустите `Scripts/bat/buildAllDebug.bat` после каждого измения в C#. Для мапперов - `Scripts/bat/buildAllTools.bat`
> 4. Запустите `Scripts/bat/runQuickAll.bat` для запуска клиента и сервера.
> 5. Подключитесь к "localhost" в клиенте.

### Linux

> 1. Клонируйте репо
> 2. Запустите `git submodule update --init --recursive` в консоли, чтобы обновить движок
> 3. Запустите `Scripts/sh/buildAllDebug.sh` после каждого изменения в C#. Для мапперов - `Scripts/sh/buildAllTools.sh`
> 4. Запустите `Scripts/sh/runQuickAll.sh` для запуска клиента и сервера.
> 5. Подключитесь к "localhost" в клиенте.

### MacOS

> Я не знаю никого, кто использовал бы macOS для тестирования этого, но, вероятно, шаги примерно те же, что и в Linux.

### Основные решения проблем

Попробуйте удалить папку bin и внутренности RobustToolBox.

## Лицензия

Пожалуйста, ознакомьтесь с файлом [LEGAL.md](./LEGAL.md), чтобы получить информацию о лицензиях кода и ресурсов в этом репозитории.

![Alt](https://repobeats.axiom.co/api/embed/fea9effb2311367773c7993d0aec4b2f866505a8.svg "Repobeats analytics image")
