# MBTI Server Extractor 

REST Сервер для определения MBTI по картинке. 
Для определения используется следующий набор признаков:
* Топ-6 основных цветов
* Colorfulness (совокупность конрастности + яркости + цветов)
* Объекты (Google ImageNet)
* Лица
* Текст
* Форма (линии)


Изображение для анализа необходимо поместить в папку  ```tmp/``` (системными средствами, в зависимости от метода, которым они приходят в саму систему).

Запуск:
```shell
python server.py
```

 Скрипт запустит локальный REST-сервер, доступный по адресу http://127.0.0.1:5000/.
 Чтобы обработать картинку, необходимо послать серверу GET запрос вида http://127.0.0.1:5000/image/imagename_with_extension
 
 Если все прошло успешно, то сервер отдаст в ответ json следующего вида:
 
```shell
{'status': 'OK', 
    'mbti': {
        'psy_type': [0.49131639680794503, 0.24257720714209274, 0.277456075040284, 0.29387620391719405]
        }
    }
```

4 числа в ответе -- вероятности каждого из 4-х MBTI классов. А именно:
* Introversion -> Extraversion (значение, меньшее 0.5 обозначает выраженность интраверсии, а больше 0.5 означает выраженность экстраверсии)
* Sensing -> Intuition 
* Thinking -> Feeling
* Judging -> Perception

При значении вероятности класса, приближенного к 0.5 можно сделать вывод, что у картинки нет яркой выраженности ни одной из двух сторон.

