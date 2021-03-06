boardtt
=======
https://github.com/translate-board-game/boardtt


Description
-----------

*Board Games Translator Toolbox*

Инструмент для локализации карт (перевода на русский, например).

**Обратите внимание, что этот код - проверка идеи.**



Концепция
---------

* используя инструментарий boardtt, описываем типы карт и области имеющиеся в них;
* делаем сканы карт (карты выкладываем друг к другу на сканер);
* запускаем скрипт из boardtt, натравливаем на сканы;
* скрипт проходит по скану, режет его на отдельные карты;
* на карте скрипт определяет регионы с текстом, которые будем локализовывать;
* текст в регионах разбирается при помощи OCR (сейчас Tesseract);
* в директории с именем файла скана для каждой карты создаётся json с данными карты и текстами для перевода, и оригинальное изображение карты;
* осуществляем перевод путём изменения строк в полученных json;
* запускаем тот же скрипт из boardtt с теми же параметрами;
* теперь скрипт создаёт ещё два изображения:

  1. оригинал карты с локализованным текстом поверх нужных регионов (цвет подложки текста скрипт пробует вычислить из цвета подложки оригинала);
  2. оверлей, где только регионы с локализацией.

После этого оверлей можно отпечатать на плёнке, которую либо наклеить либо наложить на карту, определив последнюю в прозрачный кармашек.

Результат работы скрипта может выглядеть так: https://yadi.sk/i/RgDeu6LpbiEuR



Пример конфигурирования boardtt
-------------------------------

В директории `examples` лежит `star_wars.py`, в нём описаны типы карт, используемые
в колоде дополнения **Lure of The Dark Side**.

Там же можно посмотреть, как **boardtt** запускается на данный момент.



Требования
----------

* Ubuntu Linux
* Python 2.7
* Pillow
* Tesseract OCR (libtesseract.so)
