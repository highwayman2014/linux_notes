# Скрипты на bash  
Скрипт начинается с вызова командной оболочки, пример:  
```#!/usr/bin/bash```

## Переменные  
Запись:  
```<имя>=<значение>```  
При объявлении переменной пробелов рядом с = быть не должно!  

Чтение:  
```$<имя> или ${<имя>}```

## Аргументы скрипта  
Передача аргументов скрипту:  
```./script.sh arg1 arg2 ...```  
Обработка внутри скрипта:  
$1 первый аргумент  
$2 второй аргумент  
...  
$0 имя скрипта  
\$# количество аргументов  

## Условия  
```bash
if [[ условие ]]
then
  ...
elif [[ условие ]]
then
  ...
else
  ...
fi
```  

```bash
case переменная in
  1)
    # равно 1
    ...
    ;;
  [2-9])
    # в диапазоне со 2 по 9
    ...
    ;;
  10|2[0-5])
    # 10 или с 20 до 25
    ;;
  [3-4][0-9]|50)
    # c 30 до 50
    ;;
*)
  # в остальных случаях
  ...
esac
```  
### Условия со строками  
-z <строка> - строка пуста  
-n <строка> - строка не пуста  
<строка1> == <строка2>  
<строка1> != <строка2>  

### Условия числа/строки  
-eq - ==, равно  
-ne - !=, неравно  
-lt - <, меньше  
-le - меньше или равно  
-gt - >, больше  
-ge - больше или равно  

### Условия файлы  
-e - путь существует  
-f - это файл  
-d - это директория  
-s - размер файла больше 0  
-x - файл исполняемый

### Условия логические  
! - отрицание  
&& - И  
|| - ИЛИ  

## Циклы  
```bash
for переменная in список_значений # например for i in 1 2 3 4 5
do
  ...
done
```
break - прервать  
continue - продолжить  

```bash
while [[ условие ]]
do
  ...
done
```

## Команды  
**read** *переменная1* *переменная2* ... - записать введенное пользователем значение в переменную  
### Внешние программы  
```bash
переменная=`программа`

a=`echo "test"`
# в переменную запишется test
files=`ls ~`
# в files запишется содержимое домашней директории
```

Код возврата:
0 - корректное завершение  
не 0 - в процессе работы были ошибки  

\$? - узнать код
exit код - выйти с кодом

## Арифметика  
### Синтаксис  

```bash
let "переменная + выражение"
```

```bash
let "c = 1 + 2"
let "c = a + b" # a и b - переменные
let c=1+2 # без кавычек
let "c+=1"
```

### Операции  
+, -, /, * - стандартные  
% - остаток от деления  
\** - возведение в степень  

## Функции  

```bash
имя_функции ()
{
  # действия
  # параметры $1, $2, ... $#
}
```

Использование функции:
```bash
имя_функции аргумент1 аргумент2 ...
```

Переменные:
```bash
имя_функции ()
{
  var_global=1
  lосаl var_lосаl=1
}
```

