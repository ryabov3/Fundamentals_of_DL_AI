# Задание 1: Сравнение CNN и полносвязных сетей
## 1.1. Сравнение MNIST

1. Создал 2 модели. Модель CNN с Residual Block была взята из репозитория с домашней работа 4.
2. Каждую модель обучил с одинаковыми гиперпараметрами и сравнил точность и потери на train и val множествах. Визуализация кривых обучения для каждой модели:

- Кривые обучения для FCN модели:

![Image alt](https://github.com/ryabov3/Fundamentals_of_DL_AI/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D1%8F%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%204/plots/FCN_curves_task_1.jpg)

Примерно после 7 эпохи начинается процесс переобучения, так как train loss продолжает падать, а val loss начинает расти.

- Кривые обучения для SimpleCNN:

![Image alt](https://github.com/ryabov3/Fundamentals_of_DL_AI/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D1%8F%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%204/plots/SimpleCNN_curves_task_1.jpg)

После 4 эпохи начинается процесс переобучения, так как train loss продолжает падать, а val loss начинает расти.

- Кривые обучения для CNN с Residual Block:

![Image alt](https://github.com/ryabov3/Fundamentals_of_DL_AI/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D1%8F%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%204/plots/CNNWithResidual_curves_task_1.jpg)

После 12 эпохи начался процесс переобучения, так как train loss продолжает падать, а val loss начинает расти.

3. Посмотрим на графики ниже для оценки количества параметров моделей, общего времени обучения, инференса и точности:

![Image alt](https://github.com/ryabov3/Fundamentals_of_DL_AI/blob/main/%D0%94%D0%BE%D0%BC%D0%B0%D1%88%D0%BD%D1%8F%D1%8F%20%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0%204/plots/comparation_model_parameters_task_1_1.jpg)

- Количество параметров: Здесь первенство держит модель FCN (что не удивительно). Меньше всех параметров у CNNWithResidual.
- Время обучения: Здесь же ситуация противоположная. На первом месте по общему времени обучения модель CNNWithResidual, быстрее же всех обучилась FCN.
- Количество времени на батч: Быстрее всех обрабатывает один батч модель CNNWithResidual, медленее всех SimpleCNN.
- Точность: По метрики accuracy все модели имеют почти одинаковую точность. Различия не значительные. Но по точности лучше всех является модель CNNWithResidual, на последнем месте FCN.
