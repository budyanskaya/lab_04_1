# Лабораторная работа 4.1 Чтение данных из файла и их обработка. Запись результатов обработки в файл
## Цель работы
Научиться работать с файлами, выполнять их чтение, запись и манипуляцию, а также освоить методы сериализации и десериализации данных с использованием популярных форматов хранения, таких как CSV и JSON.
## Вариант 3
№ 4.1.3 Измените задачу № 4.1.2 так, чтобы вне зависимости от ошибок чтения файла, программа выполняла подсчет суммы и максимума.
```
def load_data(filename):
    """Загрузить список вещественных чисел из файла 'filename'.

    Функция не обрабатывает исключения."""
    with open(filename, 'r') as f:
        lines = f.readlines()
    return [float(line.strip()) for line in lines]


def append_to_file(values, filename):
    """Дописать данные в файл.

    Параметры:
        - values (list of float): список вещественных чисел;
        - filename (str): имя файла.
    """
    with open(filename, 'a') as f:
        for value in values:
            f.write(str(value) + '\n')


try:
    filename = input()  # Ввести имя файла с клавиатуры
    values = load_data(filename)

    # Вычисляем сумму и максимум
    total_sum = sum(values)
    max_value = max(values)

    # Дописываем сумму и максимум в файл
    append_to_file([total_sum, max_value], filename)

except FileNotFoundError as err:
    print("Указанный файл не существует.")
    # Подсчет выполняется даже при ошибке чтения файла
    values = []
    total_sum = 0
    max_value = float('-inf')
    print(f"Сумма: {total_sum}, Максимум: {max_value}")

except IOError as err:
    print("Ошибка при чтении/сохранении файла с данными:", err)
    # Подсчет выполняется даже при ошибке ввода-вывода
    values = []
    total_sum = 0
    max_value = float('-inf')
    print(f"Сумма: {total_sum}, Максимум: {max_value}")

except Exception as err:
    print("Произошла ошибка!")
    print("Тип:", type(err))
    print("Описание:", err)
    # Подсчет выполняется даже при других ошибках
    values = []
    total_sum = 0
    max_value = float('-inf')
    print(f"Сумма: {total_sum}, Максимум: {max_value}")
```
<img width="531" height="108" alt="image" src="https://github.com/user-attachments/assets/ffa8b6e6-274b-4df3-b61e-29c8b97a2fa2" />

## Вывод
В ходе данной лабораторной работы мы смогли научиться работать с файлами, выполнять их чтение, запись и манипуляцию, а также освоить методы сериализации и десериализации данных с использованием популярных форматов хранения, таких как CSV и JSON.

