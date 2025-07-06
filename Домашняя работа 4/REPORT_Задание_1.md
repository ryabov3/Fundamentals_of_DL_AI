# Задание 1: Сравнение CNN и полносвязных сетей
## 1.1. Сравнение MNIST

#### 1. Создал 2 модели. Модель CNN с Residual Block была взята из репозитория с домашней работа 4.
#### 2. Каждую модель обучил с одинаковыми гиперпараметрами на ГПУ и сравнил точность и потери на train и val множествах. Визуализация кривых обучения для каждой модели:

- Кривые обучения для FCN модели:

![Image alt](https://github.com/ryabov3/Fundamentals_of_DL_AI/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D1%8F%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%204/plots/FCN_curves_task_1.jpg)

Примерно после 7 эпохи начинается процесс переобучения, так как train loss продолжает падать, а val loss начинает расти.

- Кривые обучения для SimpleCNN:

![Image alt](https://github.com/ryabov3/Fundamentals_of_DL_AI/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D1%8F%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%204/plots/SimpleCNN_curves_task_1.jpg)

После 4 эпохи начинается процесс переобучения, так как train loss продолжает падать, а val loss начинает расти.

- Кривые обучения для CNN с Residual Block:

![Image alt](https://github.com/ryabov3/Fundamentals_of_DL_AI/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D1%8F%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%204/plots/CNNWithResidual_curves_task_1.jpg)

После 12 эпохи начался процесс переобучения, так как train loss продолжает падать, а val loss начинает расти.

#### 3. Посмотрим на графики ниже для оценки количества параметров моделей, общего времени обучения, инференса и точности:

![Image alt](https://github.com/ryabov3/Fundamentals_of_DL_AI/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D1%8F%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%204/plots/comparation_model_parameters_task_1_1.jpg)

- Количество параметров: Здесь первенство держит модель FCN (что не удивительно). Меньше всех параметров у CNNWithResidual.
- Время обучения: Здесь же ситуация противоположная. На первом месте по общему времени обучения модель CNNWithResidual, быстрее же всех обучилась FCN.
- Количество времени на батч: Быстрее всех обрабатывает один батч модель CNNWithResidual, медленее всех SimpleCNN.
- Точность: По метрики accuracy все модели имеют почти одинаковую точность. Различия не значительные. Но по точности лучше всех является модель CNNWithResidual, на последнем месте FCN.

#### 4. Стабильнее всех обучалась модель CNNWithResidual. О чём говорят значения функции потерь на тренировке и валидации. У данной модели значения потерь на валидации уменьшались стабильнее (не считая начала обучения), в отличие от других моделей.

## 1.2. Сравнение на CIFAR-10

#### 1. Взяз модели (Полносвязную и CNN с Residual) из репозитория с домашней работой. Немного изменил CNNWithResidual, чтобы можно было по желанию использовать/не использовать регуляризацию.
#### 2. Обучил модель с одинаковыми гиперпараметрами на ГПУ.
#### 3. Сравнил точность и время обучения каждой модели.

- График кривых для CIFARCNN:

![Image alt](https://github.com/ryabov3/Fundamentals_of_DL_AI/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D1%8F%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%204/plots/CIFARCNN_curves_task_1_2.jpg)

По данному графику можно сделать вывод, что точность CIFARCNN росла до ~9 эпохи, но потом начала стагнировать.

- График кривых для CNN с ResidualBlock без регуляризации:

![Image alt](https://github.com/ryabov3/Fundamentals_of_DL_AI/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D1%8F%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%204/plots/CNN_curves_task_1_2.jpg)

По данному графику можно сделать вывод, что точность модели росла (со скачками) до ~11 эпохи, а позже начала стагнировать.

- График кривых для CNN с ResidualBlock с регуляризацией:

![Image alt](https://github.com/ryabov3/Fundamentals_of_DL_AI/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D1%8F%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%204/plots/CNN-Regularized_curves_task_1_2.jpg)

По данному графику можно сделать вывод, что точность модели росла до ~5 эпохи, а потом с различными скачками начала стагнировать.

- Время обучения каждой модели:

![Image alt](https://github.com/ryabov3/Fundamentals_of_DL_AI/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D1%8F%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%204/plots/task_1_2_train_time.jpg)

На данном скриншоте видно, что быстрее всех обучилась модель CIFARCNN, а медленее всех CNNWithResidual с регуляризацией.

#### 3. Анализ переобучения

- Графики функции потерь и точности CIFARCNN:

![Image alt](https://github.com/ryabov3/Fundamentals_of_DL_AI/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D1%8F%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%204/plots/CIFARCNN_curves_task_1_2.jpg)

Переобучение CIFARCNN началось примерно после 9 эпохи. Именно после этой эпохи val_loss начало стагнировать или расти, что является признаком переобучения.

- Графики функции потерь и точности для CNNWithResidual без регуляризации:

![Image alt](https://github.com/ryabov3/Fundamentals_of_DL_AI/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D1%8F%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%204/plots/CNN_curves_task_1_2.jpg)

Переобучение CNNWithResidual без регуляризации началось примерно после 4 эпохи. Именно после этой эпохи val_loss начало стагнировать или расти, что является признаком переобучения.

- Графики функции потерь и точности для CNNWithResidual с регуляризацией:

![Image alt](https://github.com/ryabov3/Fundamentals_of_DL_AI/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D1%8F%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%204/plots/CNN-Regularized_curves_task_1_2.jpg)

Несмотря на скачки, данная модель не подверглась переобучению. Val_loss стабильно уменьшается вместе с train loss.

#### 4. Визуализация confustion matrix.

- CM для CIFARCNN:

 ![Image alt](https://github.com/ryabov3/Fundamentals_of_DL_AI/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D1%8F%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%204/plots/CIFARCNN_confusion_matrix_task_1_2.jpg)

 Данная CM показывает высокую точность модели CIFARCNN, невзирая на то, что некоторые классы могут путаться (н, класс 5 и класс 3).

 - CM для CNNWithResidual без регуляризации.

![Image alt](https://github.com/ryabov3/Fundamentals_of_DL_AI/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D1%8F%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%204/plots/CNN_confusion_matrix_task_1_2.jpg)

Для данной CM для модели CNNWithResidual без рег. ситуацию лучше, чем у CIFARCNN. Некоторые классы также продолжают путаться, но уже меньше (н, с классами 5 и 3 ситуацию улучшилась).

- CM для CNNWithResidual с регуляризации.

![Image alt](https://github.com/ryabov3/Fundamentals_of_DL_AI/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D1%8F%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%204/plots/CNN-Regularized_confusion_matrix_task_1_2.jpg)

Для данной CM для модели CNN с рег. ситуация хуже, чем у модели без рег. Класс 3 путается с классом 6 (176) и с классом 5 (164). Но она всё ещё демонстрирует хорошую точность.

#### 5. Границы gradient flow.

- Градиенты CIFARCNN:

  ![Image alt](https://github.com/ryabov3/Fundamentals_of_DL_AI/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D1%8F%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%204/plots/CIFARCNN_gradient_flow_task_1_2.jpg)

Выводы по графику:
* На графике можно увидеть стабильное уменьшение градиентов: Градиенты для всех слоев (conv1.weight, conv2.weight, conv3.weight, fc1.weight, fc2.weight) стабильно уменьшаются с увеличением числа итераций, что видно по убыванию значений на логарифмической шкале.
* Можно увидеть потенциальная проблему исчезающих градиентов: К 6000 итерациям все градиенты достигают очень низких значений (~ 10^(-4)), что может указывать на проблему исчезающих градиентов, особенно для слоев fc1.weight и fc2.weight, где значения становятся наименьшими.


