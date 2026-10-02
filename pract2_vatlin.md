# Task 1

### Служебная информация о matplotlib:
```
python3 -m pip show matplotlib
```
### Основные элементы полученной информации:

- Name — название пакета;
- Version — версия;
- Summary — краткое описание;
- License — лицензия;
- Location — расположение установленного пакета;
- Requires — зависимости пакета;
- Required-by — пакеты, использующие matplotlib.

### Получение пакета непосредственно из репозитория:
```
git clone <адрес репозитория>
```
Это получает исходный код пакета напрямую из его репозитория без использования pip.

# Task 2

### Служебная информация о express:
```
npm info express
```
### Основные элементы полученной информации:
- name — название пакета;
- description — описание пакета;
- version — версия;
- author — автор;
- contributors — участники разработки;
- license — лицензия;
- repository — репозиторий;
- homepage — домашняя страница;
- keywords — ключевые слова;
- dependencies — зависимости, необходимые для работы express;
- devDependencies — зависимости, используемые при разработке и тестировании;
- engines — требуемая версия Node.js;
- files — файлы и каталоги, включаемые в пакет;
- scripts — команды для разработки, проверки и тестирования.

### Файл со служебной информацией пакета:
```
cat node_modules/express/package.json
```
Файл package.json содержит основную информацию о пакете, его версии, лицензии, репозитории, зависимостях, требованиях к Node.js и командах для разработки и тестирования.

### Получение пакета непосредственно из репозитория:
```
git clone https://github.com/expressjs/express.git
```
Это получает исходный код express напрямую из его репозитория без использования npm.

# Task 3

### Graphviz-код для зависимостей matplotlib:

Файл `matplotlib.dot`:

```
digraph matplotlib {
    rankdir=LR;

    matplotlib -> contourpy;
    matplotlib -> cycler;
    matplotlib -> fonttools;
    matplotlib -> kiwisolver;
    matplotlib -> numpy;
    matplotlib -> packaging;
    matplotlib -> pillow;
    matplotlib -> pyparsing;
    matplotlib -> "python-dateutil";
}
```
### Получение изображения:
```
dot -Tpng matplotlib.dot -o matplotlib.png
```
В результате создаётся изображение matplotlib.png с графом зависимостей matplotlib.

### Graphviz-код для зависимостей express:

Файл express.dot:
```
digraph express {
    rankdir=LR;

    express -> accepts;
    express -> body_parser;
    express -> content_disposition;
    express -> content_type;
    express -> cookie;
    express -> cookie_signature;
    express -> debug;
    express -> depd;
    express -> encodeurl;
    express -> escape_html;
    express -> etag;
    express -> finalhandler;
    express -> fresh;
    express -> http_errors;
    express -> merge_descriptors;
    express -> mime_types;
    express -> on_finished;
    express -> once;
    express -> parseurl;
    express -> proxy_addr;
    express -> qs;
    express -> range_parser;
    express -> router;
    express -> send;
    express -> serve_static;
    express -> statuses;
    express -> type_is;
    express -> vary;
}
```
### Получение изображения:
```
dot -Tpng express.dot -o express.png
```
В результате создаётся изображение express.png с графом зависимостей express.

### Для проверки созданных файлов:
```
ls -l matplotlib.png express.png
```

# Task 4

### Модель задачи о счастливых билетах:

Файл `happy_ticket.mzn`:

```
include "globals.mzn";

array[1..6] of var 0..9: x;

constraint x[1] + x[2] + x[3] = x[4] + x[5] + x[6];

constraint all_different(x);

solve minimize x[1] + x[2] + x[3];

output [
    "ticket = ", show(x),
    "\nsum = ", show(x[1] + x[2] + x[3])
];
```
### Запуск программы:
```
minizinc happy_ticket.mzn
```
### Полученный результат:
```
ticket = [6, 2, 0, 4, 3, 1]

sum = 8
```
### Основные элементы модели:
- array[1..6] of var 0..9: x — шесть цифр билета, каждая от 0 до 9;
- x[1] + x[2] + x[3] = x[4] + x[5] + x[6] — сумма первых трёх цифр равна сумме последних трёх;
- all_different(x) — все цифры билета должны быть различными;
- solve minimize — поиск решения с минимальной суммой первых трёх цифр;
- output — вывод найденного билета и его суммы.

### Для найденного решения:
```
6 + 2 + 0 = 8
4 + 3 + 1 = 8
```
Все шесть цифр различны, а минимальная сумма трёх цифр равна 8.

# Task 5

### Модель задачи о зависимостях пакетов:

Файл `task5.mzn`:

```
enum MENU = {
    menu_1_0_0,
    menu_1_1_0,
    menu_1_2_0,
    menu_1_3_0,
    menu_1_4_0,
    menu_1_5_0
};

enum DROPDOWN = {
    dropdown_1_8_0,
    dropdown_2_0_0,
    dropdown_2_1_0,
    dropdown_2_2_0,
    dropdown_2_3_0
};

enum ICONS = {
    icons_1_0_0,
    icons_2_0_0
};

var MENU: menu;
var DROPDOWN: dropdown;
var ICONS: icons;

constraint icons = icons_1_0_0;

constraint
    (menu = menu_1_0_0) ->
    (dropdown = dropdown_1_8_0);

constraint
    (menu in {
        menu_1_1_0,
        menu_1_2_0,
        menu_1_3_0,
        menu_1_4_0,
        menu_1_5_0
    }) ->
    (dropdown in {
        dropdown_2_0_0,
        dropdown_2_1_0,
        dropdown_2_2_0,
        dropdown_2_3_0
    });

constraint
    (dropdown = dropdown_1_8_0) ->
    (icons = icons_1_0_0);

constraint
    (dropdown in {
        dropdown_2_0_0,
        dropdown_2_1_0,
        dropdown_2_2_0,
        dropdown_2_3_0
    }) ->
    (icons = icons_2_0_0);

solve satisfy;

output [
    "menu = ", show(menu),
    "\ndropdown = ", show(dropdown),
    "\nicons = ", show(icons)
];
```
### Запуск программы:
```
minizinc task5.mzn
```
### Полученный результат:
```
menu = menu_1_0_0
dropdown = dropdown_1_8_0
icons = icons_1_0_0
```
### Основные элементы модели:
- MENU — возможные версии пакета menu;
- DROPDOWN — возможные версии пакета dropdown;
- ICONS — возможные версии пакета icons;
- var — переменные, которым MiniZinc подбирает версии пакетов;
- constraint — ограничения на совместимость версий;
- -> — условие зависимости: если выбрана определённая версия, должна быть выбрана соответствующая зависимость;
- solve satisfy — поиск любой комбинации версий, удовлетворяющей всем ограничениям.

### Полученная совместимая комбинация:
```
menu 1.0.0
dropdown 1.8.0
icons 1.0.0
```

