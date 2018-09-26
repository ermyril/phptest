## Тестовые задания для PHP Backend разработчика

Приветствуем тебя, %username%, ищущий работу!

Что с этим всем делать?
Результат каждого задания - код, который нужно отправить нам, скинув ссылку на repo/gist на Github


### Задача. Like a fizz buzz

Реализовать функцию checkBraces($str), проверяющую на синтаксическую верность последовательность скобок

- Необходимо учитывать вложенность
- Обратите внимание на производительность вашего решения
- В случае ошибки возвращаем 1, в противном случае 0

Минимальный набор тестов:

```
checkBraces("---(++++)----") == 0
checkBraces("") -> 0
checkBraces("before ( middle []) after ") == 0
checkBraces(") (") == 1
checkBraces("} {") == 1
checkBraces("<(   >)") == 1
checkBraces("(  [  <>  ()  ]  <>  )") == 0
checkBraces("   (      [)") == 1
```


### Рефакторинг. A piece of legacy

Используйте файл [aws_upload.php](aws_upload.php)

1. Декомпозируйте функцию 
2. Какие еще улучшения можно внести, что изменить? 
Вы вольны улучшать код на свое усмотрение: ООП? Пожалуйста!


### Практическая задача. DB dump obfuscator

В основе лежит реальная задача, возникающая в процессе развертывания окружений — взять дамп боевой базы и очистить/обфусцировать приватные данные в нем.
 
Есть SQL dump некоторой базы данных [example.dump.sql](example.dump.sql)

Необходимо написать консольную утилиту, которая принимает параметры:
- путь к исходному файлу с дампом
- путь к выходному файлу дампа
- путь к файлу с конфигурацией, описывающему трансформацию данных

Файл конфигурации вида
```
obfuscator.config.php
// имя таблицы => список полей, данные которых мы очищаем
[
   'user' => ['email', 'name', 'surname'],
   'tablename' => ['column_name'],
]
```
(можно использовать и php конфигурацию, и json, и yml - на ваш вкус)

- Простой вариант - заменять данные данные на пустые строки

- При желании сделайте более продвинутый вариант — возможность указывать в конфигурации типы полей: email, string, integer, phone, чтобы эти данные генерировались типично для них: например, test@test.ru для эл. почты и +79053334455 для телефона. А опционально — возможность указать готовые значения этих полей, если мы хотим их явно задать

- Напишите тесты тесты, проверяющие реализованную функциональность (юнит/интеграционные/прочие - на ваше усмотрение)

