# ROG Ally Z1 Extreme — Elden Ring: FSR 4.1 Lite + Frame Generation

Готовый набор модов для **Elden Ring**, который даёт одновременно:

* **настоящий FSR 4.1 (INT8 Lite)** — апскейлинг с резкой картинкой;
* **XeSS Frame Generation (XeFG) 2X** — удвоение FPS;
* **низкую задержку** (Reflex + XeLL) и ограничитель FPS;
* **чистую картинку** — водяной знак / оверлей FSR4 выключен.

## ⚠️ Совместимость

> **Работает на ASUS ROG Ally Z1 Extreme (AMD Radeon 780M, iGPU).**
>
> На других системах работа **не проверялась** и не гарантируется.
> Настройки `Fsr4GpuSupport` / `Fsr4Model` подобраны именно под Radeon 780M.

Проверено на:

| Компонент | Значение |
|---|---|
| Устройство | ASUS ROG Ally **Z1 Extreme** |
| GPU | AMD Radeon 780M (iGPU), драйвер 32.0.32015.14001 |
| ОС | Windows 11 x64 |
| Игра | Elden Ring v1.17.2 |
| Экран | 1920×1080 borderless |

## Что внутри

* **OptiScaler 10.0.0-dev** (`dxgi.dll`) — апскейлер + мост к генерации кадров
* **ERSS-FG 4.14.1** (`ERSS-FG.dll` + `D3D12.dll` + папка `ERSS2\`) — загрузчик апскейла/генерации
* **XeFGUnlock** (`OptiScaler\plugins\XeFGUnlock.asi`) — разблокирует MFG (2X/3X)
* **EldenModLoader** (`dinput8.dll`) + пара косметических модов в `mods\`
  (убраны хроматические аберрации и виньетка)

## Рабочий конфиг (эталон)

* 1080p borderless, рендер **852×480** (коэффициент 2.25), **2X**, лок **66 FPS**
* В мире стабильно ~66 FPS, фреймтайм ровный

## Установка

1. Скачайте архив из раздела **Releases**.
2. Распакуйте **всё содержимое** в папку игры Elden Ring — туда, где лежит
   `eldenring.exe` (обычно `...\steamapps\common\ELDEN RING\Game\`).
   Файлы должны лечь рядом с `eldenring.exe`, папки `ERSS2\`, `OptiScaler\`, `mods\` — тоже туда.
3. **Если у вас уже стоят моды через `dxgi.dll` или `dinput8.dll`** — сначала сделайте
   бэкап папки `Game`, потом перезаписывайте.
4. Запустите игру. Настраивать ничего не нужно.

Сохранения игры (`%APPDATA%\EldenRing`) этот набор **не трогает**.

## Управление

В игре два оверлея:

* **HOME** — ERSS-FG (пресеты качества, лимиты);
* **INSERT** — OptiScaler (алгоритмы, Sharpness, Reflex, Frame Gen, Framerate Limit).

## Как менять под себя

**Качество апскейла** (`OptiScaler.ini` → `UpscaleRatioOverrideValue`, или INSERT → Upscale Ratio Override):

| Значение | Рендер | Итог |
|---|---|---|
| 2.25 | 852×480 | как сейчас (среднее) |
| 2.50 | 768×432 | быстрее, мягче |
| 2.00 | 960×540 | чётче, медленнее |
| 1.50 | 1280×720 | Quality — самое чёткое |

**Лимит FPS:** `OptiScaler.ini` → `[Framerate] FramerateLimit` (или INSERT → Framerate Limit).

> **Важно:** лимит базового FPS в ERSS-FG (`MaxFPS`) здесь **не работает** — его снимает
> аддон `RemoveFrameTimeConstraint`. Используйте только `FramerateLimit`.

**2X / 3X:** `OptiScaler.ini` → `[XeFG] InterpolationCount` (1 = 2X, 2 = 3X). Требует перезапуска игры.

**Другой GPU:** настройки FSR4 специфичны для Radeon 780M. Для дискретных AMD их нужно
подбирать отдельно (в наборе это **не проверялось**).

## Если что-то не так

* **Игра не запускается** — проверьте, что все файлы и папки лежат рядом с `eldenring.exe`.
* **Чёрный экран / нет картинки** — в INSERT выключите Frame Gen и проверьте апскейл.
* **Откат** — удалите добавленные файлы/папки (`dxgi.dll`, `dinput8.dll`, `ERSS-FG.dll`,
  `D3D12.dll`, `ERSS2`, `OptiScaler`, `mods`, `libxess*.dll`, `libxell.dll`, `fakenvapi.*`)
  и восстановите папку `Game` из своего бэкапа.

## Требования

* Elden Ring v1.17.2 (проверено именно на ней)
* Windows 10/11 x64, DirectX 12
* ASUS ROG Ally Z1 Extreme (или совместимый Radeon 780M)

## Отказ от ответственности

Набор собран и проверен на конкретной конфигурации (см. выше). Используйте на свой риск.
Все права на Elden Ring принадлежат FromSoftware / Bandai Namco. Сторонние компоненты
(OptiScaler, ERSS-FG и др.) принадлежат их авторам.
