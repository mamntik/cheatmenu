# CheatMenu Mod — Fabric 1.21.4

GUI чит-меню, открывается по клавише **Right Shift** в игре.

## Что умеет

| Категория     | Кнопки                                                  |
|---------------|---------------------------------------------------------|
| Время         | День / Ночь                                             |
| Погода        | Дождь / Ясно                                            |
| Эффекты       | Скорость, Сила, Прыжок, Ночное зрение, Устойчивость, Снять всё |
| ХП / Голод    | Полное HP / Насытить                                    |
| Режим игры    | Выживание / Творчество / Наблюдатель / Приключение      |
| Опыт          | +100 уровней / +1000 уровней                            |
| Телепорт      | На 0 64 0 / На Spawn                                    |
| Предметы      | Алмазы x64 / Незерит x64                               |

> ⚠️ Команды требуют прав оператора (singleplayer — по умолчанию есть, на сервере нужен OP).

---

## Сборка

### Требования
- Java 21+
- Git (опционально)

### Шаги

1. Скачай [Fabric Loom template](https://github.com/FabricMC/fabric-example-mod) или используй этот проект как есть
2. Убедись что структура папок такая:
   ```
   cheatmenu/
   ├── build.gradle
   ├── gradle.properties
   ├── settings.gradle
   └── src/main/java/com/cheatmenu/
       ├── CheatMenuMod.java
       └── client/gui/
           └── CheatMenuScreen.java
   └── src/main/resources/
       └── fabric.mod.json
   ```

3. Открой терминал в папке `cheatmenu/` и выполни:
   ```bash
   # Windows
   gradlew.bat build

   # Linux / Mac
   ./gradlew build
   ```
   
   > Если нет файла `gradlew`, скачай его с любого fabric-проекта или установи Gradle вручную.

4. После сборки `.jar` файл будет в:
   ```
   build/libs/cheatmenu-1.0.0.jar
   ```

5. Скопируй `.jar` в папку `.minecraft/mods/`

6. Запусти игру с Fabric Loader 0.16+ и Fabric API

---

## Горячие клавиши

| Клавиша       | Действие          |
|---------------|-------------------|
| Right Shift   | Открыть чит-меню  |
| Escape        | Закрыть меню      |

---

## Добавить свои кнопки

В `CheatMenuScreen.java` найди блок `// ── Items ──` и добавь по аналогии:

```java
this.addDrawableChild(ButtonWidget.builder(Text.literal("🎁 Моя кнопка"), btn ->
        sendCommand("give @s minecraft:ITEM_ID 64"))
        .dimensions(col1, startY + rowH * 11, BTN_WIDTH, BTN_HEIGHT).build());
```
