#Комп’ютерний практикум № 7

#РЯДКИ

*Мета роботи* — ознайомитися з особливостями реалізації текстових рядків, опанувати технологію їх використання, навчитися розробляти алгоритми та програми із застосуванням рядків.

##Теоретичні відомості

*Рядок* — це сукупність символів, яка сприймається і обробляється як єдине ціле. Кожен рядок характеризується загальною довжиною, яка визначається при оголошенні, і поточною довжиною - кількістю символів у конкретний момент виконання програми.

Поточна довжина рядка може змінюватися в процесі роботи програми, але не може перевищувати загальної довжини, зазначеної при оголошенні типу.

На відміну від Pascal, в С/С++ немає стандартного рядкового типу даних, але поняття “рядка”, як єдиної лінгвістичної конструкції, існує. Рядком в С/С++ вважається символьний масив, який завершується `“\0”` (нуль-символом). Як і у випадку масиву, ім’я рядка є покажчиком на рядок (на його перший символ).

Рядок в С/С++ може як оголошуватися, так і визначатися. Наприклад:

```cpp
char str[26];
char *st;
char str[]="рядок";
#define str "Приклад рядка"
```

Для введення-виведення рядків у мовах програмування, зазвичай, вико-ристовуються стандартні засоби. При введенні рядка з клавіатури фактична його вимірність визначається автоматично при натисканні Enter. 

У С/С++ для введення-виведення рядків можуть використовуватися декілька альтернативних засобів:

-	форматовані (printf);
-	потокові (cin, cout); 
-	спеціальні (gets, puts).

Наприклад:

```cpp
char s[14], st[19], str[16]; 
cin>>s; cout<<s;
printf("рядок - %s",st);
gets_s(str); puts(str);
```

Слід зазначити, що `“\0”` при введенні рядків заноситься автоматично при натисненні клавіші Enter.

Оскільки у С/С++ ім’я рядка є покажчиком на його перший елемент, то забороненою є операція явного присвоювання рядка рядковій змінній.

Тобто, якщо мають місце оголошення:

```cpp
char str[26];			// змінна-рядок
char *st;			// покажчик на тип char
```

то оператор присвоєння виду 

```cpp
st = "адреса"
```

є допустимим, а оператор 

```cpp
str = "помилка"
```

викличе повідомлення про помилку.

Рядки можуть оброблятися як цілісний об’єкт, так і посимвольно. При посимвольній обробці доступ до конкретного символу рядка, як і до елементів масиву символів, здійснюється за індексом або за покажчиком (у С++). У цьому випадку до окремого символа рядка можна застосовувати ті ж операції, що і до змінної символьного типу.

Рядки, як цілісні об’єкти, можна присвоювати, порівнювати і обробляти різноманітним чином, застосовуючи стандартні функції обробки рядків.

Усі стандартні функції С/С++, що служать для обробки рядків, почина-ються з префікса `str` і описані у заголовному файлі `string.h`. Перелік деяких із них представлений у таблиці 1.

Таблиця 1. Стандартні засоби обробки рядків у С++

| Функція   |      Опис      |
|----------|:-------------:|
|Визначення довжини рядка|
| size_t strlen(char *str); |  Визначення довжини рядка |
|Копіювання рядка  |
| `errno_t strcpy_s(char * strDestination, size_t numberOfElements, const char *strSource);` | Копіювання рядка strSource у рядок strDestination,  розміром numberOfElements |
| `errno_t strncpy_s(char *strDest, size_t numberOfElements, const char *strSource, size_t count);` | Копіювання count перших символів рядка strSource у рядок strDest,  розміром numberOfElements |
| `char *_strdup(const char *strSource);` | Дублювання рядка strSource |
|Об'єднання (конкатенація) рядків  |
| `errno_t strcat_s(char *strDestination, size_t numberOfElements, const char *strSource);` | Склеювання рядків strDestination і strSource у рядок strDestination, розміром numberOfElements |
| `errno_t strncat_s(char *strDest, size_t numberOfElements, const char *strSource, size_t count);` | Додавання до рядка strDest count символів рядка  strSource,  розміром numberOfElements |
|Порівняння рядків |
| `int strcmp(const char *string1, const char *string2);` | Порівняння рядків string1 і string2 |
| `int _stricmp(const char *string1, const char *string2);` | Порівняння рядків string1 і string2 без урахування регістра |
| `int strncmp(const char *string1, const char *string2, size_t count);` | Порівняння перших  count  символів рядків string1 і string2 |
| `int strnicmp(const char *string1, const char *string2, size_t count);` | Порівняння перших  count  символів рядків string1 і string2 без урахування регістра |
|Пошук у рядку |
| `char *strchr(const char *str, int c);` | Пошук першого входження символа с у рядок  str |
| `char *strrchr(const char *str, int c);` | Пошук останнього входження символа с у рядок str |
| `char *strstr(const char *str, const char *strSearch);` | Пошук першого входження підрядка strSearch у рядок str |
| `char *strtok_s(char *strToken, const char *strDelimit, char **context);` | Визначення в рядку strToken лексем, описаних у рядку роздільників strDelimit, context зберігає залишок рядока між викликами strtok_s|
|Перетворення рядка |
| `errno_t _strlwr_s(char *str, size_t numberOfElements);` | Приведення символів рядка str до нижнього регістру, розміром numberOfElements |
| `errno_t _strupr_s(char *str, size_t numberOfElements);` | Приведення символів рядка str до верхнього регістру, розміром numberOfElements |
| `errno_t _strset_s(char *str, size_t numberOfElements, int c );` | Заміна усіх символів у рядку str, розміром  numberOfElements на символ с |
| `errno_t _strnset_s(char *str, size_t numberOfElements, int c, size_t count);` | Заміна перших count символів у рядку str, розміром  numberOfElements на символ с |
| `char *_strrev (char *str);` | Інвертування рядка str |

## Вимоги до програми

1.	Відповідність структурному підходу.
2.	Виведення вхідних, проміжкових і вихідних даних.
3.	Наявність прототипів функцій.
4.	Використання параметрів-рядків. 

## Приклад програми 

**Задача.** Нехай заданий рядок слів, які відокремлюються одне від одного пробілами, комами або крапками. Визначити перелік введених слів, їх кі-лькість та найдовше слово у рядку.

### Алгоритм

1.	Початок.
2.	Ввести рядок.
3.	Визначити перелік і кількість слів у рядку.  
	3.1	Цикл визначення лексем рядка:  
		-	3.1.1	Виділити поточну лексему.  
		-	3.1.2	Зберегти поточну лексему у масиві слів.  
		-	3.1.3	Вивести поточну лексему.  
		-	3.1.4	Збільшити значення лічильника лексем на 1.  
		-	3.1.5	Якщо виділені усі лексеми рядка, то кінець циклу; інакше перейти до виділення наступної лексеми  
	3.2	Вивести визначену кількість слів у рядку.  
4.	Знайти найдовше слово у масиві слів і його довжину  
	4.1	Прийняти, як найдовше, перше слово рядка (із запам’ятовуванням його довжини).  
	4.2	Цикл перегляду усіх слів рядка (відповідних елементів масиву):  
		- 4.2.1	Якщо довжина поточного слова більша, то воно стає найдо-вшим (із запам’ятовуванням його довжини).  
		- 4.2.2	Якщо переглянуті усі слова, то кінець циклу; інакше перейти до наступного слова.  
	4.3	Вивести найдовше слово рядка і його довжину.  
5.	Кінець.

## Текст програми
```cpp
#include <iostream>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>

using namespace std;

char s[100];                         // вихідний рядок
const int n = 20;
typedef char array[n][n];
array arr;                           // масив слів

int create_words(char[], array);     // визначення переліку і кількості слів
void long_word(array, int);          // пошук найдовшого слова

//==================== головна функцiя ====================
int main()
{
    int i;                           // кількість слів у рядку
    puts("enter string:");
    gets(s);                         // ввести рядок
    i = create_words(s, arr);        // визначити перелік і кількість слів у рядку
    long_word(arr, i);               // знайти найдовше слово і його довжину
    system("pause");
}

//============ визначення переліку і кількості слів =============
int create_words(char str[], array mas)
{
    int k = 0;                       // кількість лексем у рядку
    char *delimiter = "., ";         // покажчик на розділові символи
    char *p;                         // покажчик на поточну лексему
    cout << "List of Words:" << endl;
    p = strtok(s, delimiter);        // визначити першу лексему
    while (p != NULL)                // поки є рядку є лексеми
    {
        strcpy(mas[k], p);           // копіювати поточну лексему в масив
        puts(p);                     // вивести поточну лексему на екран
        k++;                         // перейти до наступної лексеми
        p = strtok(NULL, delimiter); // продовжити пошук лексем
    }
    cout << "number of words=" << k << endl;
    return k;                        // повернути кількість слів
}

//============== пошук найдовшого слова =============
void long_word(array mas, int k)
{
    int maxlen;                      // довжина шуканого слова
    char maxword[20];                // найдовше слово 
    strcpy(maxword, mas[0]);         // значення першого слова
    maxlen = strlen(maxword);        // довжина першого слова
    for (int j = 1; j < k; j++)      // перегляд усіх слів рядка
    if (strlen(mas[j]) > maxlen)
    {
        strcpy(maxword, mas[j]);     // поточне найдовше слово
        maxlen = strlen(maxword);    // поточна найбільша довжина
    }
    cout << "masxword=" << maxword << endl;
    cout << "its length=" << maxlen << endl;
}
```

## Варіанти завдань
1. 	У заданому рядку символів визначити кількість слів, довжина яких більша за вказану користувачем.
2. 	Заданий рядок символів, що містить цифри і пробіли. Групи цифр, що розділені пробілами (одним або декількома), вважаємо словами. Розг-лядаючи кожне слово як число, визначити їх суму.
3. 	Заданий рядок, що містить розділені пробілами слова. Відсортувати слова за зростанням їхньої довжини.
4. 	Ввести два рядки, вилучити з першого рядка всі слова, які зустрічаються у другому рядку.
5. 	У заданому рядку символів визначити слова, довжина яких співпадає із заданою користувачем.
6. 	У заданому рядку символів підрахувати кількість слів, які починаються групою заданих символів.
7. 	Із заданого рядка символів вилучити слова, довжина яких менша, за вказану користувачем.
8. 	У заданому рядку символів визначити кількість слів, у яких співпадають перший та останній символи. Слова відділяються довільною кількістю пробілів.
9. 	Ввести рядок символів, переформатувати його, подовживши до довжини 60 символів рівномірним додаванням пробілів між словами. Визначити кількість доданих пробілів.
10. 	У заданому рядку символів визначити символи, які зустрічаються по одному разу і надрукувати номери їх позицій.
11. 	У заданому рядку символів підрахувати кількість кожного із сим-волів. 
12. 	Із заданого рядка символів вилучити всі слова, які закінчуються групою заданих символів. Підрахувати кількість вилучень.
13. 	У заданому рядку символів визначити слова, які починаються та закінчуються на задані символи. 
14. 	У заданому рядку символів підрахувати кількість слів, що знахо-дяться між симвлоами ';’. 
15. 	Із заданого рядка символів вилучити символи, що співпадають. Підрахувати кількість вилучень. 
16. 	У заданому рядку символів визначити слова, що мають однакові перший та останній символи. Підрахувати кількість таких слів.
17. 	У заданому рядку символів вилучити слова, що мають парні порядкові номери. 
18. 	Заданий рядок символів, що містить цифри і пробіли. Групи цифр, що розділені пробілами (одним або декількома), вважаємо словами. Розглядаючи кожне слово як число, визначити найбільше і найменше із них і поміняти знайдені слова місцями.
19. 	У заданому рядку символів знайти символи з максимальною і мінімальною частотою входження.
20. 	У заданому рядку символів вилучити всі слова, що зустрічаються більше двох раз. 
21. 	У заданому рядку символів всі слова, що стоять на парних позиціях, вивести в зворотньому порядку. 
22. 	Заданий рядок, що містить розділені пробілами слова. Визначити всі наявні в рядку слова-паліндроми (слова, які пишуться однаково зліва направо і справа наліво) і їхню кількість. 
23. 	У заданому рядку символів поміняти місцями саме довге і саме коротке слово.
24. 	Заданий рядок символів, що містить цифри і пробіли. Групи цифр, що розділені пробілами (одним або декількома), вважаємо словами. Розг-лядаючи кожне слово як число, упорядкувати їх по зростанню числових значень.
25. 	Ввести рядок символів, у якому містяться круглі дужки. Перевірити, чи є баланс дужок у рядку: для кожної дужки, яка відкривається, справа має бути дужка, що закривається. Дужки можуть бути вкладені одна в одну.
26. 	З рядка символів видалити слова, номери яких парні. Серед слів з непарними номерами визначити найдовше. 
27. 	Ввести рядок, перетворити послідовності цифрових символів в ньому на числа та знайти їх суму.
28. 	У рядку символів визначити кількість повторень кожного слова та видалити дублікати слів. Слова відокремлюються пробілами.
29. 	Увести масив рядків, що містить фрагмент програми мовою С. Надрукувати список ідентифікаторів, що зустрічаються у правій частині операторів присвоєння.
30. 	Розбити на склади згідно з правилами перенесення слів кожне слово на парній позиції у введеному з клавіатури рядку. Визначити слова, перенесення яких неможливе.

## Контрольні питання
1.	Чим відрізняється поточна довжина рядка від його загальної довжини?
2.	Як позначається кінець рядка у С/С++?
3.	Як ініціалізувати рядок під час його оголошення у С/С++?
4.	Як може  здійснюватися доступ до елемента рядка у С/С++?
5.	Як може  вводитися та виводитися рядок у С/С++?
6.	Які бібліотечні функції визначені для змінних рядкового типу у С/С++?
7.	Чи можна у С/C++ виконати операції присвоєння рядків?
8.	Як реалізуються операції порівняння рядків?
9.	У чому особливість застосування функції розкладання рядка на лексеми у С/С++?
