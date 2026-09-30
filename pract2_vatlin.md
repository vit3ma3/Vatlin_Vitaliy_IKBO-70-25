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
