# Домашнее задание к работе 10
## Условие задачи
Составьте программу, которая для заданной пользователем фигуры (круга, прямоугольника, равнобедренного треугольника) предлагает меню выбора одной из операций:
1) рассчитать площадь;
2) вывести определение фигуры;
3) нарисовать фигуру (вид символа пользователь задает в main);
4) вывести параметры фигуры (радиус для круга, диагональ для прямоугольника, высота для равнобедренного треугольника);
5) сравнить площади двух фигур (вывести разность между площадями).
## 1. Алгоритм 
1) Начало
2) Выбор фигуры
3) Выбор операции 
4) Выполнение функции
5) Конец
## 2. Реализация программы
```C
#define _CRT_SECURE_NO_DEPRECATE
#define P 3.14
#include <stdio.h>
#include <locale.h>
#include <math.h>

float area_round();
float area_rectangle();
float area_triangle();

void draw_round();
void draw_rectangle();
void draw_triangle();

double get_radius();
double get_diag_rectangle();
float get_h_triangle();

double compare();

void define_round();
void define_rectangle();
void define_triangle();

int main()
{
    setlocale(LC_CTYPE, "RUS");
    int type_figure, type_func;
    puts("Выберите фигуру (1 - круг, 2 - прямоугольник, 3 - равнобедренный треугольник)\n");
    scanf("%d", &type_figure);
    puts("\n");
    switch (type_figure) {
    case 1: {
        puts("Выберите операцию\n");
        puts("(1 - Вычислить площадь\n");
        puts("2 - Нарисовать\n");
        puts("3 - Вычислить радиус\n");
        puts("4 - Cравнить площади\n");
        puts("5 - Вывести определение)\n");
        scanf("%d", &type_func);
        puts("\n");
        switch (type_func) {
        case 1: printf("Площадь круга равна %.2f", area_round()); break;
        case 2: draw_round(); break;
        case 3: printf("Радиус круга равен %.2lf", get_radius()); break;
        case 4: printf("Разница между площадями равна %.2lf", compare()); break;
        case 5: define_round(); break;
        }
        break;
    }
    case 2: {
        puts("Выберите операцию\n");
        puts("(1 - Вычислить площадь\n");
        puts("2 - Нарисовать\n");
        puts("3 - Вычислить длину диагонали\n");
        puts("4 - Cравнить площади\n");
        puts("5 - Вывести определение)\n");
        scanf("%d", &type_func);
        puts("\n");
        switch (type_func) {
        case 1: printf("Площадь прямоугольника равна %.2f", area_rectangle()); break;
        case 2: draw_rectangle(); break;
        case 3: printf("Диагональ прямоугольника равна %.2lf", get_diag_rectangle()); break;
        case 4: printf("Разница между площадями равна %.2lf", compare()); break;
        case 5: define_rectangle(); break;
        }
        break;
    }

    case 3: {
        puts("Выберите операцию\n");
        puts("(1 - Вычислить площадь\n");
        puts("2 - Нарисовать\n");
        puts("3 - Вычислить высоту\n");
        puts("4 - Cравнить площади\n");
        puts("5 - Вывести определение)\n");
        scanf("%d", &type_func);
        puts("\n");
        switch (type_func) {
        case 1: printf("Площадь равнобедренного треугольника равна %.2f", area_triangle()); break;
        case 2: draw_triangle(); break;
        case 3: printf("Высота равнобедренного треугольника равна %.2f", get_h_triangle()); break;
        case 4: printf("Разница между площадями равна %.2lf", compare()); break;
        case 5: define_triangle(); break;
        }
        break;
    }
    }
    return 0;
}

float area_round()
{
    float a, s;
    puts("Введите радиус:\n");
    scanf("%f", &a);
    s = a * a * P;
    return s;
}


float area_rectangle()
{
    float a, b, s;
    puts("Введите стороны:\n");
    scanf("%f %f", &a, &b);
    s = a * b;
    return s;
}

float area_triangle()
{
    float a, b, c, s;
    puts("Введите стороны (основание, длина боковой стороны):\n");
    scanf("%f %f", &c, &a);
    b = a;
    s = (c / 4) * sqrt(4 * a * a - c * c);
    return s;
}

void draw_round()
{
    char symb;
    puts("Введите символ для рисования:\n");
    scanf(" %c", &symb);
    printf("    %c%c    \n", symb, symb);
    printf("  %c    %c  \n", symb, symb);
    printf(" %c      %c \n", symb, symb);
    printf("  %c    %c  \n", symb, symb);
    printf("    %c%c    \n", symb, symb);
}

void draw_rectangle()
{
    char symb;
    puts("Введите символ для рисования:\n");
    scanf(" %c", &symb);
    printf("%c%c%c%c%c%c%c%c\n", symb, symb, symb, symb, symb, symb, symb, symb);
    printf("%c      %c\n", symb, symb);
    printf("%c      %c\n", symb, symb);
    printf("%c      %c\n", symb, symb);
    printf("%c%c%c%c%c%c%c%c\n", symb, symb, symb, symb, symb, symb, symb, symb);
}

void draw_triangle()
{
    char symb;
    puts("Введите символ для рисования:\n");
    scanf(" %c", &symb);
    printf("     %c     \n", symb, symb);
    printf("    %c %c   \n", symb, symb);
    printf("   %c   %c  \n", symb, symb);
    printf("  %c     %c \n", symb, symb);
    printf(" %c       %c\n", symb, symb);
    printf("%c%c%c%c%c%c%c%c%c%c%c\n", symb, symb, symb, symb, symb, symb, symb, symb, symb, symb, symb);
}

double get_radius()
{
    double r, s;
    puts("Введите площадь круга:\n");
    scanf("%lf", &s);
    r = sqrt(s / P);
    return r;
}

double get_diag_rectangle()
{
    float a, b, d;
    puts("Введите стороны прямоугольника:\n");
    scanf("%f %f", &a, &b);
    d = sqrt(a * a + b * b);
    return d;
}

float get_h_triangle()
{
    float a, c, h;
    puts("Введите стороны треугольника (основание, длина боковой стороны):\n");
    scanf("%f %f", &c, &a);
    h = a * a - 0.5 * c * c;
    return h;
}

double compare()
{
    double a, b;
    puts("Введите площади фигур:\n");
    scanf("%lf %lf", &a, &b);
    return fabs(a - b);
}

void define_round()
{
    puts("Круг — часть плоскости, которая лежит внутри окружности.\n");
}

void define_rectangle()
{
    puts("Прямоугольник — это четырёхугольник, у которого все четыре угла прямые.\n");
}

void define_triangle()
{
    puts("Равнобедренный треугольник — это треугольник, у которого две стороны равны.\n");
    puts("Эти равные стороны называются боковыми, а третья сторона — основанием.\n");
}
```
## 3. Результат работы программы
### Вычисление площади круга
Выберите фигуру (1 - круг, 2 - прямоугольник, 3 - равнобедренный треугольник)  

1  


Выберите операцию  

(1 - Вычислить площадь  

2 - Нарисовать  

3 - Вычислить радиус  

4 - Cравнить площади  

5 - Вывести определение)  

1  


Введите радиус:  

2  
Площадь круга равна 12.56  
### Вычисление диагонали прямоугольника
Выберите фигуру (1 - круг, 2 - прямоугольник, 3 - равнобедренный треугольник)  

2  


Выберите операцию  

(1 - Вычислить площадь  

2 - Нарисовать  

3 - Вычислить длину диагонали  

4 - Cравнить площади  

5 - Вывести определение)  

3  


Введите стороны прямоугольника:  

3 4  
Диагональ прямоугольника равна 5.00  
### Вывод определения равнобедренного треугольника
Выберите фигуру (1 - круг, 2 - прямоугольник, 3 - равнобедренный треугольник)  

3  


Выберите операцию  

(1 - Вычислить площадь  

2 - Нарисовать  

3 - Вычислить высоту  

4 - Cравнить площади  

5 - Вывести определение)  

5  


Равнобедренный треугольник - это треугольник, у которого две стороны равны.  

Эти равные стороны называются боковыми, а третья сторона - основанием.  
## 4. Информация о разработчике 
Вильальба Агния, группа бТИИ-251


