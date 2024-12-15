# Игра "Крестики-нолики" на JavaScript

Источник: видео "Уроки по Javascript. 
Делаем игру крестики-нолики на Javascript (Джаваскрипт)" 
https://vk.com/im?sel=19460369&z=video-101965347_456257149%2Fabd2a1cc8485a453d4%2Fpl_post_-11899736_41573

1. Создать нужные файлы

- создаем HTML (index.html), CSS (style.css), JS (script.js) документ в программе "WebStorm" для работы с JavaScript 
(скачать бесплатную версию https://www.jetbrains.com/webstorm/);

2. в файле index.html

- меняем название в строке title в разделе head - Крестики-нолики

    ```html
    <title>Крестики-нолики</title>
    ```

- подцепляем стиль из CSS файла в разделе head

    ```html
    <link rel="stylesheet" href="Slider_CSS.css">
    ```
  
- подцепляем скрипт из JS файла в разделе body

    ```html
    <script src="script.js"></script>
    ```
  
3. в файле script.js создаем новую переменную и новый массив равному 9 (т.к. элементов в таблице "крестики-нолики" - 9)

    ```JS
    var t = new Array(9);
    ```

4. в файле script.js пишем функцию, которая рандомно распределяет крестик или нолик.
Программа будет рандомно распределять нолик, а пользователь крестик

    ```JS
    function ai() {
    var id = Math.floor(Math.random() * 9); //floor - округляем
    t[id] ? ai[]: move(id, 'ai'); //проверка пустого места и переход на это пустое место
    }
    ```

5. в файле index.html в разделе body рисуем таблицу для игры

    ```html
    <div class="container">
    <div class="table">
        <div class="cell" id="0"></div>
        <div class="cell" id="1"></div>
        <div class="cell" id="2"></div>
        <div class="cell" id="3"></div>
        <div class="cell" id="4"></div>
        <div class="cell" id="5"></div>
        <div class="cell" id="6"></div>
        <div class="cell" id="7"></div>
        <div class="cell" id="8"></div>
    </div>
    </div>
    ```
   
6. в файле index.html в разделе body в нарисованную таблицу, чтобы мы могли делать шаг в игре

    ```html
    <div class="container">
    <div class="table">
        <div class="cell" id="0" onclick="move(0, 'player')"></div>
        <div class="cell" id="1" onclick="move(1, 'player')"></div>
        <div class="cell" id="2" onclick="move(2, 'player')"></div>
        <div class="cell" id="3" onclick="move(3, 'player')"></div>
        <div class="cell" id="4" onclick="move(4, 'player')"></div>
        <div class="cell" id="5" onclick="move(5, 'player')"></div>
        <div class="cell" id="6" onclick="move(6, 'player')"></div>
        <div class="cell" id="7" onclick="move(7, 'player')"></div>
        <div class="cell" id="8" onclick="move(8, 'player')"></div>
    </div>
    </div>
    ```
   
7. в файле script.js пишем функцию, которая будет делать шаг

    ```JS
    function move(id, role) {
    if(t[id]) return false; //если место занято, то мы не шагаем
    t[id] = role //кем занято это место
    document.getElementById(id).className = 'cell' + role;
    //в зависимости от кого был сделан шаг, вставляет соответствующую картинку
    }
    ```
   
8. в файле script.js пишем функцию, когда заканчивается игра и все поля в таблице заняты, игра перезагружается

    ```JS
    function reset() {
    alert("Игра окончена!");
    location.reload();
    }
    ```
   
9. в файле script.js пишем проверку, можем ли мы закончить игру. Проверяем все возможные комбинации игры 1-2-3 и т.д.

    ```JS
    function checkEnd() {
    if (t[0]=='ai' && t[1]=='ai' && t[2]=='ai' || t[0]=='player' && t[1]=='player' && t[2]=='player') return true;
    if (t[3]=='ai' && t[4]=='ai' && t[5]=='ai' || t[3]=='player' && t[4]=='player' && t[5]=='player') return true;
    if (t[6]=='ai' && t[7]=='ai' && t[8]=='ai' || t[6]=='player' && t[7]=='player' && t[8]=='player') return true;
    if (t[0]=='ai' && t[3]=='ai' && t[6]=='ai' || t[0]=='player' && t[3]=='player' && t[6]=='player') return true;
    if (t[1]=='ai' && t[4]=='ai' && t[7]=='ai' || t[1]=='player' && t[4]=='player' && t[7]=='player') return true;
    if (t[2]=='ai' && t[5]=='ai' && t[8]=='ai' || t[2]=='player' && t[5]=='player' && t[8]=='player') return true;
    if (t[0]=='ai' && t[4]=='ai' && t[8]=='ai' || t[0]=='player' && t[4]=='player' && t[8]=='player') return true;
    if (t[2]=='ai' && t[4]=='ai' && t[6]=='ai' || t[2]=='player' && t[4]=='player' && t[6]=='player') return true;
    if (t[0] && t[1] && t[2] && t[3] && t[4] && t[5] && t[6] && t[7] && t[8]) return true;
    //перезапуск игры последней строкой    
    }
    ```

10. Связываем 2 функции reset и move

    ```JS
    
    ```