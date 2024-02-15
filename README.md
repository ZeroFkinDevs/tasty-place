# Proj Nackskott
(наверное надо переназвать)

top-down survival хоррор в запущенном болезненном городе после инцидента с биологическим оружием.

## Как клонировать
```
git clone --recurse-submodules https://github.com/ZeroFkinDevs/proj-nackskott.git
```
`--recurse-submodules` чтобы отдельный репозиторий с ресурсами `/resources/` клонировался


# Софт
- [Godot](https://godotengine.org/) - `v4.2.1.stable.mono.official [b09f793f5]`
- [Visual Studio Code](https://code.visualstudio.com/) - with `ms-dotnettools.csharp`, `ms-dotnettools.csdevkit`
- [Blender](https://www.blender.org/) - `v3.1.2`
- [Adobe Photoshop](https://www.adobe.com/ru/products/photoshop.html) - `CC 2014`
- [Obsidian](https://obsidian.md/)
- [game-resources-exporter](https://github.com/AshenHermit/game-resources-exporter)

# Экосистема

### Obsidian
Это внешняя *SSD* для мозга.  
В [Obsidian](https://obsidian.md/) ведем записи, идеи, дев-лог, все что связано с идеями.
- Это очень **упростит наращивание новых идей**, понимание того что делаем,  
потому что все записи, идеи и история буквально перед глазами.
- **Упростит переосмысление/изменение** чего-то уже накопленного,  
то есть проще работать над существующими идеями и не дает запутаться у себя в голове.  

Главное вести записи и размышлять в кайф.

### `/resources/` - Тут Живут Ресурсы
Это отдельный репозиторй, чтобы там контент хранить.  
Используем [game-resources-exporter](https://github.com/AshenHermit/game-resources-exporter)  
Все что находится в этой папке должно читаться экспортером и экспортироваться в проект, в `/project/resources`.
То есть:
- Проекты редакторов: `psd`, `blend`, `fla`, `flp` ... другие ... 
- Уже готовые экспортированные файлы: `png`, `mp3`, `wav` ... 
    только в том случае если нет необходимости иметь файл проекта.  
- Экспорты `flp` проектов FL studio, для них пока что экспорт не автоматизирован, поэтому `mp3`/`wav` обязательно сюда же.

### Файловая Система
- Имена **папок** в стиле `snake_case` *(пример)*
- Имена **скриптов** в стиле `PascalCase.cs` *(пример)*
- Имена всех остальных файлов - файлов **ресурсов**, **сцен** ... в стиле `snake_case.tscn` *(пример)*

### Файлы Одного Объекта
К файлам объекта относятся:
- **модель** (`.blend`, в ней же физическая, визуальная, еще кака-то), 
- **текстура** (`.psd`, разные `.psd` для разных текстур, (там типо текстуры для color, emission, normal))

Где хранить:
- Если объект постоянен на протяжении игры (Игрок например) или просто им пользуются на протяжении всей игры или в разных ее частях,  
то в папке `resources/objects/persistent/<object_name>`
- Если нет, то есть относиться к какой-то локации и используется там,  
то в папке `resources/objects/<location_name>/<object_name>`

## Поверсируем
По системе semantic versioning: [Semantic Versioning 2.0.0](https://semver.org/) |  [Семантическое Версионирование 2.0.0](https://semver.org/lang/ru/)  
Это правда больше относится к разработке API, программ-редакторов...  
Но можно интерпретировать эту логику для игры: вот так например: Semantic versioning для игр: [Best practices for labeling game versions?](https://gamedev.stackexchange.com/questions/48325/best-practices-for-labeling-game-versions)
Существует 4 уровня изменений, которые указываются в версии отдельными числами через точку: `MAJOR.MINOR.REVISION.PACKAGE`. их следует увеличивать:
- `MAJOR` - "Это указывает на важную веху *(milestone)* в игре, увеличивайте ее при переходе от бета-версии к выпуску, от выпуска к основным обновлениям."
- `MINOR` - "Используется для обновлений функций, исправлений крупных ошибок и т.д."
- `REVISION` или `PATCH` - "Незначительные изменения существующих функций, небольшие исправления ошибок и т.д."
- `PACKAGE` - "Ваш код остается прежним, изменяются внешние библиотеки или обновляются файлы ресурсов."

## Покоммитим
Коммиты можно на `русском` писать, если удобнее.  
Делать коммитов сколько угодно, сколько потребуется, это считай просто `ctrl` + `s` нажимаешь.  
Коммитить лучше тогда, когда сделал что-то, из-за чего логично было бы повысить один из уровней версии.

Небольшое правило для написания понятных коммитов: 
- [Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/)
- [Соглашение о коммитах 1.0.0](https://www.conventionalcommits.org/ru/v1.0.0/) 
### Кратко:
```
<type>(<optional scope>): <subject>     <---- Заголовок коммита

[optional body]                         <---- Тело коммита

[optional footer(s)]                    <---- Футер коммита
```
**Заголовок коммита**: 
- Заголовок коммита должен быть кратким и информативным. Что изменилось/добавилось
- Он начинается с типа коммита,
Возможные типы коммитов:
    - `feat`: Добавление новой функциональности, (или ресурсов)
    - `fix`: Исправление ошибок
    - `chore`: Различные задачи и обслуживание, (незначительные изменения которые не связаны с кодом или с добавлением чего-то нового)(правки в моделях, текстурах, ресурсах короче)
    - `refactor`: Рефакторинг кода (без добавления новой функциональности и исправления ошибок)
    - `docs`: Обновление документации
    - `style`: Изменения форматирования кода (без изменения функциональности)
    - `test`: Добавление или исправление тестов
- за ним следует двоеточие и пробел, а затем краткое описание изменения.

**Тело коммита (необязательно)**: 
- После заголовка коммита можно добавить более подробное описание изменения, может отдельные мысли, проблемы которые возникли, это не страшно, а очень важно записывать.
- Это поле должно быть отделено от заголовка пустой строкой и начинаться с новой строки.

**Футер коммита (необязательно)**: 
- Футер коммита может содержать ссылки на задачи, связанные с этим изменением, или другую дополнительную информацию.

Примеры
```
fix: prevent racing of requests

Introduce a request id and a reference to latest request. Dismiss
incoming responses other than from latest request.

Remove timeouts which were used to mitigate the racing issue but are
obsolete now.

Reviewed-by: Z
Refs: #123
```
```
feat(README): add a section explaining the problems encountered
```
! - BREAKING CHANGE
```
feat(api)!: send an email to the customer when a product is shipped
```
