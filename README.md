# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #1 выполнил:
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
познакомиться с программными средствами для создания системы машинного обучения и ее интеграции в Unity.

## Задание 1. Написать программы Hello World на Python и Unity.
#### -Реализовать систему машинного обучения в связке Python - Google-Sheets – Unity. При выполнении задания можно использовать видео-материалы и исходные данные, предоставленные преподавателями курса.

##Ход работы:

*Установка необходимых пакетов.
![image](https://user-images.githubusercontent.com/104727697/198155577-be21425d-c124-46d7-ae7d-87c0dcae629c.png)

*Создание 3 объектов, присвоение им материала, добавление rigidbody и скрипта к шару.
![Lab3 1 2](https://user-images.githubusercontent.com/104727697/198154792-13fd3f0f-7655-4269-8009-9c65e85a7d97.png)
![image](https://user-images.githubusercontent.com/104727697/198155651-cf9bb20b-e3a1-4c7a-8a21-15f0739e703c.png)

*Запустк обучения MLAgent в конфигурации rollerball_config.yaml на 3,9,27 копиях ранее созданного Prefab.
mlagents-learn rollerball_config.yaml --run-id=RollerBall --force
![Lab3 1 3](https://user-images.githubusercontent.com/104727697/198154798-267a36d0-762a-421d-9048-cba17325b5fa.png)
![Lab3 1 4](https://user-images.githubusercontent.com/104727697/198154800-0ca20604-1ecf-4ee1-a285-d3ccbe349dd3.png)
![Lab3 1 5](https://user-images.githubusercontent.com/104727697/198154804-dc19e373-f17b-4f71-85ed-ce4f2c2f28b5.png)

![Train1](https://user-images.githubusercontent.com/104727697/198154795-0f1910d9-7a92-4196-8cce-c697b049646e.png)

## Задание 2
###Подробно опишите каждую строку файла конфигурации нейронной сети, доступного в папке с файлами проекта по ссылке. Самостоятельно найдите информацию о компонентах Decision Requester, Behavior Parameters, добавленных на сфере.
behaviors:
RollerBall: # id
trainer_type: ppo # Proximal Policy Optimization, режим обучения
hyperparameters:
batch_size: 10 # кол-во опытов на каждой итерации
buffer_size: 100 # кол-во опыта, которое нужно набрать перед обновлением модели
learning_rate: 3.0e-4 # начальная скорость обучения
beta: 5.0e-4 # увеличение случайности действий
epsilon: 0.2 # насколько быстро политика может развиваться во время обучения
lambd: 0.99 #  насколько агент полагается на свою текущую оценку стоимости при расчете обновленной оценки стоимости
num_epoch: 3 # количество проходов через буфер опыта, при выполнении оптимизации
learning_rate_schedule: linear # определяет как скорость обучения изменяется с течением времени, linear линейно уменьшает скорость
network_settings:
normalize: false # нормализация к входным данным векторного наблюдения
hidden_units: 128 # количество нейронов в скрытых слоях сети
num_layers: 2 # количество скрытых слоёв в нейронной сети
reward_signals:
extrinsic:
gamma: 0.99 # коэффициент дисконтирования для будущих вознаграждений
strength: 1.0 # коэффициент на который умножается вознаграждение
max_steps: 500000 # максимальное количество проходов
time_horizon: 64 # временные рамки
summary_freq: 10000 # количество опыта, который необходимо собрать перед созданием и отображением статистики

## Задание 3
### Доработайте сцену и обучите ML-Agent таким образом, чтобы шар перемещался между двумя кубами разного цвета. Кубы должны, как и в первом задании, случайно изменять координаты на плоскости.

using UnityEngine;
using Unity.MLAgents;
using Unity.MLAgents.Sensors;
using Unity.MLAgents.Actuators;

public class RollerAgent : Agent
{
    Rigidbody rBody;
    void Start()
    {
        rBody = GetComponent<Rigidbody>();
    }

    public GameObject Target1;
    public GameObject Target2;
    private bool target1Collected;
    private bool target2Collected;

    public override void OnEpisodeBegin()
    {
        if (this.transform.localPosition.y < 0)
        {
            this.rBody.angularVelocity = Vector3.zero;
            this.rBody.velocity = Vector3.zero;
            this.transform.localPosition = new Vector3(0, 0.5f, 0);
        }
        Target1.transform.localPosition = new Vector3(Random.value * 8 - 4, 0.5f, Random.value * 8 - 4);
        Target2.transform.localPosition = new Vector3(Random.value * 8 - 4, 0.5f, Random.value * 8 - 4);
        Target1.SetActive(true);
        Target2.SetActive(true);
        target1Collected = false;
        target2Collected = false;
    }

    public override void CollectObservations(VectorSensor sensor)
    {
        sensor.AddObservation(Target1.transform.localPosition);
        sensor.AddObservation(Target2.transform.localPosition);
        sensor.AddObservation(this.transform.localPosition);
        sensor.AddObservation(target1Collected);
        sensor.AddObservation(target2Collected);
        sensor.AddObservation(rBody.velocity.x);
        sensor.AddObservation(rBody.velocity.z);
    }

    public float forceMultiplier = 10;
    public override void OnActionReceived(ActionBuffers actionBuffers)
    {
        Vector3 controlSignal = Vector3.zero;
        controlSignal.x = actionBuffers.ContinuousActions[0];
        controlSignal.z = actionBuffers.ContinuousActions[1];
        rBody.AddForce(controlSignal * forceMultiplier);
        float distanceToTarget1 = Vector3.Distance(this.transform.localPosition, Target1.transform.localPosition);
        float distanceToTarget2 = Vector3.Distance(this.transform.localPosition, Target2.transform.localPosition);
        if (!target1Collected & distanceToTarget1 < 1.42f)
        {
            target1Collected = true;
            Target1.SetActive(false);
        }
        if (!target2Collected & distanceToTarget2 < 1.42f)
        {
            target2Collected = true;
            Target2.SetActive(false);
        }
        if (target1Collected & target2Collected)
        {
            SetReward(1.0f);
            EndEpisode();
        }
        else if (this.transform.localPosition.y < 0)
        {
            EndEpisode();
        }
    }
}

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
