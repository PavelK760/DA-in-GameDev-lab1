# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #2 выполнил:
- Карабанов Павел Александрович
- РИ210942
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:


[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.
- ✨Magic ✨

## Цель работы
познакомиться с программными средствами для организции передачи данных между инструментами google, Python и Unity

## Задание 1. . Реализовать совместную работу и передачу данных в связке Python - Google-Sheets – Unity.
### Пошагово выполнить каждый пункт раздела "ход работы" с описанием и примерами реализации задач
#### -Для Python в отчете привести скриншоты с демонстрацией сохранения документа google.colab на свой диск с запуском программы, выводящей сообщение Hello World.
![Снимок](https://user-images.githubusercontent.com/104727697/192782964-dbeff17e-dc74-4abd-b44c-c520d8e3009b.PNG) 
![Снимок01](https://user-images.githubusercontent.com/104727697/192792145-9825f2bf-5780-43ee-8c36-b2c1b15dee88.PNG)


#### - Для Unity  в отчете привести скришноты вывода сообщения Hello World в консоль. 
![Снимок04](https://user-images.githubusercontent.com/104727697/192791649-6f509bf4-cc79-4e93-afec-3e96f53b376f.png)
![Снимок05](https://user-images.githubusercontent.com/104727697/192793653-59b5f73a-61b6-499b-8e73-03b5b4ceafef.png)


## Задание 2
### В разделе «ход работы» пошагово выполнить каждый пункт с описанием и примером реализации задачи по теме лабораторной работы.
1.	Произвести подготовку данных для работы с алгоритмом линейной регрессии. 10 видов данных были установлены случайным образом, и данные находились в линейной зависимости. Данные преобразуются в формат массива, чтобы их можно было вычислить напрямую при использовании умножения и сложения.
![Снимок02](https://user-images.githubusercontent.com/104727697/192792300-9072f864-a1f0-4d05-89ce-b4e2ce0e58fb.PNG)


2.	Определите связанные функции. Функция модели: определяет модель линейной регрессии wx+b. Функция потерь: функция потерь среднеквадратичной ошибки. Функция оптимизации: метод градиентного спуска для нахождения частных производных w и b.
![Снимок03](https://user-images.githubusercontent.com/104727697/192792351-f56ac797-559f-4571-8b9b-49981d565d1d.PNG)

3.	Начать итерацию
- Шаг 1 Инициализация и модель итеративной оптимизации
![Снимок1](https://user-images.githubusercontent.com/104727697/192783023-be78f754-a8a6-4989-9063-9e9478ad3742.PNG)

- Шаг 2 На второй итерации отображаются значения параметров, значения потерь и эффекты визуализации после итерации
![Снимок2](https://user-images.githubusercontent.com/104727697/192792861-a81f9872-f6f9-4deb-8603-8c1a929e2fbf.PNG)

- Шаг 3 Третья итерация показывает значения параметров, значения потерь и визуализацию после итерации
![Снимок3](https://user-images.githubusercontent.com/104727697/192792917-e7e4aa8b-3530-4fdf-8a4e-cb7363118820.PNG)

- Шаг 4 На четвертой итерации отображаются значения параметров, значения потерь и эффекты визуализации
![Снимок4](https://user-images.githubusercontent.com/104727697/192792957-4bd47588-addf-4b35-844b-a7ab1c98989b.PNG)

- Шаг 5 Пятая итерация показывает значение параметра, значение потерь и эффект визуализации после итерации
![Снимок5](https://user-images.githubusercontent.com/104727697/192793040-69aba424-762f-4045-acd2-84d0ed639b29.PNG)

- Шаг 6 10000-я итерация, показывающая значения параметров, потери и визуализацию после итерации
![Снимок6](https://user-images.githubusercontent.com/104727697/192793087-7656071b-4389-4cbb-a882-3bf8f953f205.PNG)


## Задание 3
### Должна ли величина loss стремиться к нулю при изменении исходных данных? Ответьте на вопрос, приведите пример выполнения кода, который подтверждает ваш ответ.

Величина loss - это коэффициент среднеквадратичной ошибки, с каждой итерацией он стремится к нулю, так как модель постепенно "обучается". Наглядный пример — это разница в значении loss на первой и на 10000-ой итерации.

1-ая итерация
![Доки3 01](https://user-images.githubusercontent.com/104727697/192794814-d3044580-02a8-4c02-88f2-01ec0f2674b9.PNG)

100000-ая итерация
![Доки3 1](https://user-images.githubusercontent.com/104727697/192794833-88e0ba4d-2b23-4001-9c45-bbfda9ac39e9.PNG)

### Какова роль параметра Lr? Ответьте на вопрос, приведите пример выполнения кода, который подтверждает ваш ответ. В качестве эксперимента можете изменить значение параметра

Lr – коэффициент, необходимый, чтобы уменьшить производные функции в различных точках a и b, это необходимо для оптимизации данных к наименьшей погрешности. При изменении переменной можно заметить, как при увеличении данные больше расходятся, а при уменьшении - сходятся

![Доки3 02](https://user-images.githubusercontent.com/104727697/192796293-ce22856b-d244-440a-a4ca-8fa6cc24511b.PNG)


![Доки3 2](https://user-images.githubusercontent.com/104727697/192796335-9fc4628a-2b8d-45bd-8160-80470360a9c0.PNG)

## Выводы

Я ознакомился с основными операторами зыка Python на примере реализации линейной регрессии, а так же установил на свой компьютер необходимые для дальнейшего обучения ресурсы и получил базовые навыки в обращении с ними

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
