

## Отчет по лабораторной работе № 1

#### № группы: `ПМ-2402`

#### Выполнил: `Грашин Илья Романович`

#### Вариант: `7`

### Cодержание:

- [Постановка задачи](#1-постановка-задачи)
- [Входные данные](#2-входные-данные)
- [Данные на выход](#3-данные-на-выход)
- [Выбор структуры данных](#4-выбор-структуры-данных)
- [Алгоритм](#5-алгоритм)
- [Программа](#6-программа)
- [Анализ правильности решения](#7-анализ-правильности-решения)

### 1. Постановка задачи

- Условия задачи

> Три покупателя стоят в очереди за бананами. Они планируют купить A, B,
C килограмм бананов соответственно порядку в очереди. Если к моменту,
когда приходит его очередь, в магазине не остаётся нужного покупателю
количества бананов, покупатель уходит, ничего не купив. Изначально в магазине имеется X кг бананов. Сколько покупателей смогут купить бананы,
которые они планируют? На вход программы подаются натуральные числа
X, A, B, C.

- Для решения задачи нам необходима последовательная проверка с помощью модуля if достаточности килограмм бананов для каждого покупателя по очереди.

### 2. Входные данные

На вход подаются натуральные числа, значит используем тип данных int - целые.
Последовательно переменнымм присваиваются значения, с которыми мы далее будем взаимодействовать.
Ограничений нет, диапазона значений тоже

### 3. Данные на выход
На выходе получаем фразу, которая меняется в зависимости от полученного итога в неравенствах на каждом этапе.
Например: "1-ый покупатель А смог купить нужное количество бананов"


### 4. Выбор структуры данных
Так как в условии задачи сказано, что используются натуральные значения, то будем использовать int для всех переменных

|                                                | название переменной | Тип (в Java) | 
|------------------------------------------------|---------------------|--------------|
| X (Количество киллограм бананов)               | `X`                 | `int`        |
| A (Требуемое кол-во бананов для покупателя А)  | `A`                 | `int`        |
| B (Требуемое кол-во бананов для покупателя B)  | `B`                 | `int`        |
| C (Требуемеое кол-во бананов для покупателя C) | `C`                 | `int`        |
### 5. Алгоритм
#### Алгоритм выполнения программы:

1. **Ввод данных:**
   Программы считывает 4 целых числа(по условии задачи еще и натуральных), обозначенные как `X`, `A`, `B` и `C`.
2. **Расчет разности и сравнение ее с нулем с выводом нужного ответа**
   Программа выполняет вычитание требуемего кол-ва бананов каждого покупатея из `X` киллограм.
    - Если `X-A` меньше нуля, то программа выводит, что бананов недостаточно даже для одного
    - Если `X-A` больше нуля, то далее выполняется сравнение `X-A-B` с нулем, если же оно меньше нуля, то программа выводит, что бананов достаточно только для покупателя А.
    - Если `X-A-B` больше нуля, то дальше выполняется сравнение `X-A-B-C` с нулем, если оно меньше нуля, то программа выводит, что бананов хватает для A и B покупателей.
    - Если `X-A-B-C` больше нуля, то программа выводит, что бананов хватает на всех
3. **Вывод результата**
   на экран выводится определенное предложения, исходя из условия.

   #### Блок-схема
```mermaid
   graph TD
        A([Начало]) --> B[/Ввести: X, A, B, C/]
        B --> C{X-A<0}
        C -- Да --> D[/Вывод: ни один покупатель не смог купить нужное количество бананов/]
        C -- Нет --> E{X-A-B<0}
        E -- Да --> F[/Вывод:1-ый покупатель А смог купить нужное количество бананов/]
        E -- Нет --> G{X-A-B-C<0}
        G -- Да --> H[/Вывод:2 покупателя А и В смогли купить нужное количество бананов/]
        G --> Нет --> I[/Вывод:все 3 покупателя А, В, С смогли купить нужное количество бананов/]
        D --> Z
        F --> Z
        H --> Z
        I --> Z([Конец])
```


### 6. Программа


```java

import java.io.PrintStream;

import java.util.Scanner;
        public class Main {

        // Объявляем объект класса Scanner для ввода данных

        public static Scanner in = new Scanner(System.in);

        // Объявляем объект класса PrintStream для вывода данных

        public static PrintStream out = System.out;
        
            public static void main(String[] args) {

                // Считывание четырех целых чисел X, A, B, C из консоли, являющемися: Х - киллограмы бананов в магазине;
                // A, B, C - требуемое кол-во бананов для каждого покупателя соотвественно

                int X = in.nextInt();
                int A = in.nextInt();
                int B = in.nextInt();
                int C = in.nextInt();

                // проверям хватает ли бананов для покупателя А

                if(X-A<0){
                    System.out.println("ни один покупатель не смог купить нужное количество бананов"); // вывод ответа при недостаточности бананов для А
                }

                else{
                    // проверка количества оставшегося кол-ва бананов для В

                    if(X-A-B<0){
                        System.out.println("1-ый покупатель А смог купить нужное количество бананов"); // вывод ответа при недостаточности бананов для В
                    }

                    else{
                        // проверка количества оставшегося кол-ва бананов для С
                        if(X-A-B-C<0){
                            System.out.println("2 покупателя А и В смогли купить нужное количество бананов"); // вывод ответа при недостаточности бананов для С
                        }
                        else{
                            System.out.println("все 3 покупателя А, В, С смогли купить нужное количество бананов"); // вывод ответа при достаточном количестве бананов
                        }

                    }
                }
            }
        }
```


### 7. Анализ правильности решения

Привести тесты и анализ работы программы для этих тестов.
Очень неплохо было бы обосновать выбор тестов.

1. Тест на X<A
- Input:
    ```
    15
    20
    ```

- Output:
    ```
    ни один покупатель не смог купить нужное количество бананов
    ```

2. Тест на A<=X<B+A

- Input:
    ```
    25
    15
    20
    ```

- Output:
    ```
   1-ый покупатель А смог купить нужное количество бананов
    ```
 3. Тест на A+B<=X<C+A+B

- Input:
    ```
    35
    15
    10
    20
    ```

- Output:
    ```
   2 покупателя А и В смогли купить нужное количество бананов
    ```
 4. Тест на A+B+С<=X

- Input:
    ```
    35
    15
    10
    5
    ```

- Output:
    ```
  все 3 покупателя А, В, С смогли купить нужное количество бананов
    ```

