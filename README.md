# Git-How-To 
___
## 1. Фінальні приготування

### 1. Встановлюємо ім'я та адресу електронної пошти
- git config --global user.name "Your Name"
- git config --global user.email "your_email@whatever.com"

### 2. Назва гілки за замовчуванням
- git config --global init.defaultBranch main

### 3. Коректна обробка закінчень рядків
- git config --global core.autocrlf input
- git config --global core.safecrlf warn

## Результат:
![lesson_1.1](GHT/2.png)

## 2. Створення проєкту

### 1. Створіть сторінку «Hello, World»
- mkdir work
- cd work
- touch hello.html

### 2. Створіть репозиторій
- git init

### 3. Додайте сторінку у репозиторій
- git add hello.html
- git commit -m "Initial Commit"

## Результат:
![lesson_1.2](GHT/3.png)

## 3. Перевірка стану

### 1. Перевірте стан репозиторія
- git status

## Результат:
![lesson_1.3](GHT/4.png)

## 4. Внесення змін

### 1. Змініть сторінку «Hello, World»
- <h1>Hello, World!</h1>

### 2. Перевірте стан
- git status

## Результат:
![lesson_1.4](GHT/5.png)

## 5. Індексація змін

### 1. Додайте зміни
- git add hello.html
- git status

## Результат:
![lesson_1.5](GHT/6.png)

## 7. Коміт змін

### 1. Закомітьте зміни
- git commit

![lesson_1.7.1](GHT/8.png)

### 2. Перевірте стан
- git status

![lesson_1.7.2](GHT/9.png)

## 8. Зміни, а не файли

### 1. Перша зміна: Додайте стандартні теги сторінок
 html
<html>
  <body>
    <h1>Hello, World!</h1>``````
  </body>
</html>

### 2. Додайте ці зміни
- git add hello.html

![lesson_8.1-2](GHT/1.png)

### 3. Друга зміна: Додайте заголовок HTML
<html>
  <head>
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>

### 5. Коміт
- git commit -m "Added standard HTML page tags"
- git status

![lesson_8.5](GHT/10.png)

### 6. Додайте другу зміну
- git add .
- git status

### 7. Зробіть коміт другої зміни
- git commit -m "Added HTML header"

![lesson_8.6-7](GHT/11.png)

## 9. Історія проєкту

### 1. Отримання списку зроблених змін
- git log

![lesson_9.1](GHT/12.png)

### 2. Однорядкова історія
- git log --pretty=oneline

![lesson_9.2](GHT/13.png)

### 5. Кінцевий формат історії
- git log --pretty=format:"%h %ad | %s%d [%an]" --date=short
- git config --global format.pretty '%h %ad | %s%d [%an]'
- git config --global log.date short

![lesson_9.5](GHT/14.png)

## 10. Отримання старих версій

### 1. Отримайте хеші попередніх комітів
- git log
- git checkout <hash>
- cat hello.html

![lesson_10.1](GHT/15.png)
![lesson_10.1.2](GHT/16.png)
### 2. Поверніться до останньої версії в гілці main
- git switch main
- cat hello.html

![lesson_10.2](GHT/17.png)

## 11. Створення тегів версій

### 1. Створіть тег першої версії
- git tag v1
- git log

![lesson_11.1](GHT/18.png)

### 2. Теги для попередніх версій
- git checkout v1^
- cat hello.html
- git tag v1-beta
- git log

![lesson_11.2](GHT/19.png)
![lesson_11.2.2](GHT/20.png)

### 3. Перемикання за ім'ям тегу
- git checkout v1
- git checkout v1-beta

![lesson_11.3](GHT/21.png)

### 4. Перегляд тегів за допомогою команди tag
- git tag

![lesson_11.4](GHT/22.png)

### 5. Перегляд тегів у логах
- git log main --all

![lesson_11.5](GHT/23.png)
## 12.Скасування локальних змін (до індексації)

### 1. Перейдіть на гілку main
- git switch main

### 2. Змініть hello.html
<html>
  <head>
  </head>
  <body>
    <h1>Hello, World!</h1>
    <!-- This is a bad comment. We want to revert it. -->
  </body>
</html>
### 3. Перевірте стан
- git status

## 4. Скасування змін в робочій директорії
- git restore hello.html
- git status
- cat hello.html

## Результат:
![lesson_12.1-4](GHT/24.png)
![lesson_12.1-4.2](GHT/25.png)

## 13. Скасування проіндексованих змін (перед комітом)

### 1. Внесіть зміни у файл і проіндексуйте їх
<html>
<head>
    <!-- This is an unwanted but staged comment -->
</head>
<body>
<h1>Hello, World!</h1>
</body>
</html> 

- git add hello.html

### 2. Перевірте стан
- git status

![lesson_13.1-2](GHT/26.png)

### 3. Відновлення індексу
- git restore --staged hello.html
`
## 4. Відновлення файлу
- git restore hello.html
- git status

![lesson_13.3-4](GHT/27.png)

## 14. Скасування комітів
### 1. Змініть файл і зробіть коміт
<html>
  <head>
  </head>
  <body>
    <h1>Hello, World!</h1>
    <!-- This is an unwanted but committed change -->
  </body>
</html>
- git add hello.html
- `git commit -m "Oops, we didn't want this commit"

### 2. Зробіть коміт з новими змінами, що скасовують попередні
- `git revert HEAD`

### 3. Перевірте лог
- git log

![lesson_14.1-3](GHT/28.png)

## 15. Видалення комітів з гілки (revert)

### 1. Перевірте нашу історію
- git log

### 2. Для початку позначте цю гілку
- git tag oops

### 3. Відкіт до коміту, що передує до oops
- git reset --hard oops^
- git log

## 4. Нічого ніколи не губиться
- git log --all

![lesson_15.1-4](GHT/29.png)
![lesson_15.1-4.2](GHT/30.png)

## 16. Видалення тегу oops
- git tag -d oops
- git log --all

## 17. Внесення змін до комітів

### 1. Змініть сторінку, а потім зробіть коміт
<!-- Author: Alexander Shvets -->
<html>
  <head>
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>

- git add hello.html
- git commit -m "Added copyright statement"
- git log

### 2. Ой... необхідний email
<!-- Author: Alexander Shvets (alex@githowto.com) -->
<html>
  <head>
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>

### 3. Змініть попередній коміт
- git add hello.html
- git commit --amend -m "Added copyright statement with email"

## 4. Перегляд історії
- git log

![lesson_17.1-4](GHT/33.png)
![lesson_17.1-4.2](GHT/35.png)
![lesson_17.1-4.3](GHT/36.png)

## 18. Створення гілки

### 1. Створіть гілку
- git switch -c style
- git status

### 2. Додайте файл стилів style.css
- touch style.css
h1 {
  color: red;
}
- git add style.css
- git commit -m "Added css stylesheet"

![lesson_18.1-2](GHT/37.png)
![lesson_18.1-2.2](GHT/38.png)

### 3. Змініть hello.html для того, щоб використовувати style.css
<!-- Author: Alexander Shvets (alex@githowto.com) -->
<html>
  <head>
    <link type="text/css" rel="stylesheet" media="all" href="style.css" />
  </head>
  <body>
    <h1>Hello, World!</h1>
  </body>
</html>
- git add hello.html
- git commit -m "Included stylesheet into hello.html"

![lesson_18.3](GHT/39.png)

## 19. Перемикання гілок
- git log --all

## 1. Перемкніться на гілку main
- git switch main
- cat hello.html

## 2. Повернемося до гілки style
- git switch style
- cat hello.html

![lesson_19.1-2](GHT/40.png)
![lesson_19.1-2.2](GHT/41.png)
![lesson_19.1-2.3](GHT/42.png)

## 20. Переміщення файлів

### 1. Перегляд історії змін конкретного файлу
- git log -- hello.html
- git log -- style.css

### 2. Перегляд різниці між версіями певного файлу
- git show v1

![lesson_20.1-2](GHT/43.png)
![lesson_20.1-2.2](GHT/44.png)

### 3. Перейменуйте hello.html.
- git mv hello.html index.html
- git status
- git add .
- git status

![lesson_20.3](GHT/45.png)
![lesson_20.3.2](GHT/46.png)

## 4. Безпечне переміщення файлу style.css\- `mkdir css
- mkdir css
- git mv style.css css/style.css
- git status
- git commit -m "Renamed hello.html; moved style.css"
- git log css/style.css
- git log --follow css/style.css

![lesson_20.4](GHT/47.png)
![lesson_20.4.2](GHT/48.png)

## 21. Зміни в гілці main

### 1. Створіть файл README
This is the Hello World example from the GitHowTo tutorial.
### 2. Закомітьте файл README у гілку main
- git switch main
- git add README.md
- git commit -m "Added README"

![lesson_21.1-2](GHT/49.png)'

## 22. Перегляд розбіжних гілок

### Перегляньте поточні гілки
git log --all --graph

![lesson_22](GHT/50.png)

## 23. Злиття

### Злиття гілок
- git switch style
- git merge main
- git log --all --graph

![lesson_23](GHT/51.png)

## 24. Створення конфлікту

### 1. Поверніться у main і створіть конфлікт
- git switch main
<!-- Author: Alexander Shvets (alex@githowto.com) -->
<html>
  <head>
    <title>Hello World Page</title>
  </head>
  <body>
    <h1>Hello, World!</h1>
    <p>Let's learn Git together.</p>
  </body>
</html>
- git add hello.html
- git commit -m "Added meta title"

### 2. Перегляд гілок
- git log --all --graph

![lesson_24.1-2](GHT/52.png)

## 25. Вирішення конфліктів
### 1. Злиття main до гілки style
- git switch style
- git merge main
- git status

## 2. Скасування злиття
- git merge --abort
- git status

### 3. Рішення конфлікту
- git merge main
- відредагувати файл до стану, що нас влаштовує
### 4. Зробіть коміт з розв'язаним конфліктом
- git add index.html
- git commit -m "Resolved merge conflict"
- git status
- git log --all --graph

## 26. rebase проти merge

## 27. Відкочування гілки style

### 1.  Відкотіть гілку style
- git switch style
- git log --graph
- git reset --hard HEAD~2


### 2. Перевірте гілку
- git log --graph

![lesson_27.1-2](GHT/54.png)
![lesson_27.1-2.2](GHT/55.png)

## 28. Перебазування

### 1. Перебазуйте гілку style на main.
- git switch style
- git rebase main
- git status

### 2 . Розв'яжіть конфлікт
- git add .
- git rebase --continue
- git status
- git log --all --graph

## 29. Злиття в гілку main

### 1. Злиття style в main
- git switch main
- git merge style

![lesson_28.1](GHT/56.png)

### 2. Перегляньте логи
- git log --all --graph

![lesson_29.1-2](GHT/57.png)
