# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #3 выполнил:
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
Познакомиться с основными принципами работы перцептрона, научиться применять их

## Задание 1. В данной лабораторной работе мы в проекте Unity рализуем перцептрон, который умеет производить вычисления:

```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

[System.Serializable]
public class TrainingSet
{
	public double[] input;
	public double output;
}

public class Perceptron : MonoBehaviour {

	public TrainingSet[] ts;
	double[] weights = {0,0};
	double bias = 0;
	double totalError = 0;

	double DotProductBias(double[] v1, double[] v2) 
	{
		if (v1 == null || v2 == null)
			return -1;
	 
		if (v1.Length != v2.Length)
			return -1;
	 
		double d = 0;
		for (int x = 0; x < v1.Length; x++)
		{
			d += v1[x] * v2[x];
		}

		d += bias;
	 
		return d;
	}

	double CalcOutput(int i)
	{
		double dp = DotProductBias(weights,ts[i].input);
		if(dp > 0) return(1);
		return (0);
	}

	void InitialiseWeights()
	{
		for(int i = 0; i < weights.Length; i++)
		{
			weights[i] = Random.Range(-1.0f,1.0f);
		}
		bias = Random.Range(-1.0f,1.0f);
	}

	void UpdateWeights(int j)
	{
		double error = ts[j].output - CalcOutput(j);
		totalError += Mathf.Abs((float)error);
		for(int i = 0; i < weights.Length; i++)
		{			
			weights[i] = weights[i] + error*ts[j].input[i]; 
		}
		bias += error;
	}

	double CalcOutput(double i1, double i2)
	{
		double[] inp = new double[] {i1, i2};
		double dp = DotProductBias(weights,inp);
		if(dp > 0) return(1);
		return (0);
	}

	void Train(int epochs)
	{
		InitialiseWeights();
		
		for(int e = 0; e < epochs; e++)
		{
			totalError = 0;
			for(int t = 0; t < ts.Length; t++)
			{
				UpdateWeights(t);
				Debug.Log("W1: " + (weights[0]) + " W2: " + (weights[1]) + " B: " + bias);
			}
			Debug.Log("TOTAL ERROR: " + totalError);
            Debug.Log("TOTAL Generation: " + e);
		}
	}

	void Start () {
		Train(100);
		Debug.Log("Test 0 0: " + CalcOutput(0,0));
		Debug.Log("Test 0 1: " + CalcOutput(0,1));
		Debug.Log("Test 1 0: " + CalcOutput(1,0));
		Debug.Log("Test 1 1: " + CalcOutput(1,1));		
	}
	
	void Update () {
		
	}
}
```
###  * OR Перцептрон успешно обучился уже на 4 поколении
![Снимок1](https://user-images.githubusercontent.com/104727697/204275058-03a9811b-a864-496d-aa50-cb39da50d8f4.PNG)

###  * AND Перцептрон успешно обучился уже на 5 поколении
![Снимок2](https://user-images.githubusercontent.com/104727697/204275652-df30305c-3657-4dc3-b20c-71b446bcfb5b.PNG)

###  * NAND Перцептрон успешно обучился уже на 6 поколении
![Снимок3](https://user-images.githubusercontent.com/104727697/204276147-8dc7b080-36c0-4f27-9a92-984533ceb9a8.PNG)

###  * XOR Перцептрон не способен обучиться этому коду даже при 100 поколениях
![Снимок4](https://user-images.githubusercontent.com/104727697/204271407-f2316556-c76f-465c-abb6-13044c83ab87.PNG)

## Задание 2. Построить графики зависимости количества эпох от ошибки обучения. Чем больше количество эпох обучения тем меньше вероятность ошибки.Так как увеличивается количество попыток на обучение. 

График зависимости количества эпох от ошибки обучения для OR:
![Снимок5](https://user-images.githubusercontent.com/104727697/204275730-c6126a8b-e87c-4d88-bfb4-081501866dc2.PNG)

График зависимости количества эпох от ошибки обучения для AND:
![Снимок6](https://user-images.githubusercontent.com/104727697/204275972-2cab5313-77da-479f-a64b-8bf72d53d12f.PNG)

График зависимости количества эпох от ошибки обучения для NAND:
![Снимок7](https://user-images.githubusercontent.com/104727697/204276564-28c20fa6-826f-41b4-9f99-5a10d24de6c9.PNG)

График зависимости количества эпох от ошибки обучения для XOR:
![Снимок8](https://user-images.githubusercontent.com/104727697/204277243-c8b06735-5120-4e3d-b683-8c3f37f8159c.PNG)



3.	Начать итерацию

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
