# Вклад в Lost Paradise

Если вы рассматриваете возможность внести свой вклад в Lost Paradise, [руководство Wizard's Den по PR](https://docs.spacestation14.com/en/general-deveLPment/codebase-info/pull-request-guidelines.html) является хорошей отправной точкой для понимания качества кода и этикета отслеживания версий. Обратите внимание, что у нас нет такого разделения на ветки master/stable.

Важно: **не вносите изменения через веб-редактор**. Из текста выше:

> Не используйте веб-редактор GitHub для создания PR. PR, отправленные через веб-редактор, могут быть закрыты без рассмотрения.

"Upstream" относится к репозиторию [Simple-Station/Einstein-Engines](https://github.com/Simple-Station/Einstein-Engines), от которого был создан этот форк.

# Специфичный для LP контент

В целом, все, что вы создаете с нуля (в отличие от изменения существующего контента из upstream), должно находиться в специфичной для Lost Paradise подпапке `_LP`.

Примеры:

- `Content.Server/_LP/Shipyard/Systems/ShipyardSystem.cs`
- `Resources/Prototypes/_LP/Loadouts/role_loadouts.yml`
- `Resources/Audio/_LP/Voice/Goblin/goblin-scream-03.ogg`
- `Resources/Textures/_LP/Tips/clippy.rsi/left.png`
- `Resources/Locale/en-US/_LP/devices/pda.ftl`
- `Resources/ServerInfo/_LP/Guidebook/Medical/Doc.xml`

# Изменения в файлах upstream

Если вы вносите изменения в C# или YAML-файл из upstream, **вы обязаны добавить комментарии на измененных строках или рядом с ними**.

Комментарии должны пояснять, что именно было изменено, чтобы упростить разрешение конфликтов при изменении файла в upstream.

Если вы изменяете значения, для единообразия оставляйте комментарий в формате `LP edit OLD<NEW`.

Для YAML в частности: если вы добавляете компонент или список смежных полей, используйте блочные комментарии, но если вы вносите ограниченные изменения в поля компонента, комментируйте поля индивидуально.

Для C# файлов: если вы добавляете большой объем кода, рассмотрите возможность использования разделяемых классов (partial class), если это имеет смысл.

При заимствовании (cherry-picking) функций из upstream лучше всего комментировать номером PR, который был заимствован.

Кроме того, fluent (.ftl) файлы **не поддерживают комментарии на той же строке**, что и значение локализации - оставляйте комментарий на строке выше при изменении значений.

## Примеры комментариев в файлах upstream или портированных файлах

Однострочный комментарий к измененному полю yml:

```yml
- type: entity
  id: TorsoHarpy
  name: "harpy torso"
  parent: [PartHarpy, BaseTorso] # LP edit: add BaseTorso
```

Изменение значения (обратите внимание на формат `OLD<NEW`):

```yml
  - type: Gun
    fireRate: 4 # LP edit 3<4
    availableModes:
    - SemiAuto
```

Модуль киборга с добавленным полем moduleId (встроенный пустой комментарий), закомментированным ведром (встроенный пустой комментарий) и DroppableBorgModule, который мы добавили (начало/конец блочного комментария):

```yml
  - type: ItemBorgModule
    moduleId: Gardening # LP edit
    items:
    - HydroponicsToolMiniHoe
    - HydroponicsToolSpade
    - HydroponicsToolClippers
    # - Bucket # LP edit
  # LP edit start: droppable borg items
  - type: DroppableBorgModule
    moduleId: Gardening
    items:
    - id: Bucket
      whitelist:
        tags:
        - Bucket
  # LP edit end
```

Комментарий к новому импортированному пространству имен:

```cs
using Content.Client._NF.Emp.Overlays; // LP edit
```

Пара комментариев, заключающих блок добавленного кода:

```cs
component.Capacity = state.Capacity;

component.UIUpdateNeeded = true;

// LP edit start: ensure signature colour is consistent
if (TryComp<StampComponent>(uid, out var stamp))
{
    stamp.StampedColor = state.Color;
}
// LP edit end
```

# Картостроение

В общем:

Если вы вносите изменения в карту, свяжитесь с мейнтейнером карты (или, если его нет, с автором) и избегайте наличия нескольких открытых PR с изменениями одной и той же карты.

Конфликты с картами делают PR взаимоисключающими, поэтому либо ваша работа, либо работа мейнтейнера будет потеряна. Общайтесь, чтобы избежать этого!

# Перед отправкой

Дважды проверьте свой diff на GitHub перед отправкой: поищите непреднамеренные коммиты или изменения и удалите случайные пробелы или изменения окончания строк.

# Журналы изменений (Changelogs)

В настоящее время все журналы изменений попадают в журнал изменений LP. Префикс `ADMIN:` в данный момент ничего не делает.

# Дополнительные ресурсы

Если вы новичок в разработке в SS14 в целом, ознакомьтесь с [документацией SS14](https://docs.spacestation14.io/) или обратитесь за помощью в [Discord](https://wiki.lost-paradise.space/discord/)!

## Контент, сгенерированный ИИ

Код, спрайты и любой другой контент, сгенерированный ИИ, не разрешается отправлять в репозиторий.

Попытка отправить PR с контентом, сгенерированным ИИ, может привести к блокировке вашей возможности вносить вклад.
