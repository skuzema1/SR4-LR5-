`Дисциплина: Методы и технологии машинного обучения`   
`Уровень подготовки: бакалавриат`   
`Направление подготовки: 01.03.02 Прикладная математика и информатика`   
`Семестр: осень 2022/2023`   
`Кузема София Евгеньевна`
# Лабораторная работа №5: Методы, основанные на деревьях решений. Регрессионные деревья. Деревья классификации. Бустинг.  

В практических примерах ниже показано:   

* как делать перекодировку признаков в номинальной и порядковой шкалах
* как вырастить дерево и сделать обрезку его ветвей   
* как настроить модель бустинга на деревьях решений  
* как подбирать настроечные параметры моделей методом сеточного поиска  

Точность всех моделей оценивается методом перекрёстной проверки по 5 блокам.  

*Модели*: дерево классификации, бэггинг, бустинг, дерево регрессии  
*Данные*: `default_of_credit_card_clients.csv`. Источник: [сайт Калифорнийского университета в Ирвине](https://archive.ics.uci.edu/ml/datasets/in-vehicle+coupon+recommendation)
## 1. Данные разделила на  выборку для построения моделей (85%) и отложенные наблюдения (15%).

![image](https://user-images.githubusercontent.com/93768556/202890573-f91d0e25-804d-4c2d-a798-6a1674f7dc11.png)

## 2. Построение модели дерева с обрезкой ветвей
Всего значений alpha: 1657

Энтропия листьев для первых 5 значений alpha: [0.00128451 0.00136294 0.00139254 0.00142214 0.00145175]

![image](https://user-images.githubusercontent.com/93768556/202890795-cf5169b4-c941-48d7-b875-507010af5dda.png)

![image](https://user-images.githubusercontent.com/93768556/202890822-2e2da91c-ab15-4be9-affb-c64713b1a4e3.png)

Оптимальное количество узлов: 33 

соответствующая Acc на тестовой: 0.822 

Acc с перекрёстной проверкой для модели pruned_tree : 0.737

Количество листьев (количество узлов): 2249

Глубина дерева: количество узлов от корня до листа в самой длинной ветви: 39

Очевидно, дерево получилось слишком большое для отображения в графическом формате.
### 3. Построение модели дерева методом бустинга

Подберём сеточным поиском настроечные параметры модели:  
* $B$ число деревьев, 
* $\lambda$ – скорость обучения,
* $d$ – глубина взаимодействия предикторов.

![image](https://user-images.githubusercontent.com/93768556/202891491-64754150-ac07-4fce-8cc8-bad6191ea135.png)

Сеточный поиск c использованием 5 различных значений занял 916.55 секунд

Сеточный поиск c использованием 5 различных значений занял 1676.04 секунд

точность лучшей модели: 0.821

параметры лучшей модели:
  n_estimators: 50 
  learning_rate: 0.11285714285714286 
  max_depth: 2
  
  ### 4. Выбрала самую точную модель:
  
  ![image](https://user-images.githubusercontent.com/93768556/202907756-ea3673cd-3381-4b7c-9298-acd480a8725b.png)
  
  Ей оказалась модель бустинга.
  
  ### 5. Сделать по ней прогноз на отложенные наблюдения, оценить точность этого прогноза.
  
  ![image](https://user-images.githubusercontent.com/93768556/202907846-2e154602-53ed-4d70-97c1-912900ec12b9.png)
  
  ### 6. Точность: 0,83, что выше точности построенных моделей.


  
  
