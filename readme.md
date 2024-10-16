## Лабораторная работа 2

1. Создадим новый файл `system.bash`

```bash
touch system.bash
```

2. Откроем новый файл с помощью редактора gedit

```bash
gedit system.bash
```

3. Объявим переменную IFS, которая хранит внутренний разделитель полей, присвоим ей значение ` . `
   
```bash
IFS=' . '
```

4. Далее выведем в терминал фразуу: `Insert IPv4 adress: ` и прочитаем введенные данные как массив
   
```bash
echo "Insert IPv4 adress: "
read -a arr
```

5. Присвоим переменным `var, var1, var2, var3` значения элементов массива соответственно `arr[0], arr[1], arr[2], arr[3]`
   
```bash
var=${arr[0]}
var1=${arr[1]}
var2=${arr[2]}
var3=${arr[3]}
```

![изображение](https://github.com/user-attachments/assets/755458e5-9ffb-402f-830d-5dc36c9a3b69)


6. Начнем 4 цикла `until` соответственно для каждого октета. В переменные `ans, ans1, ans2, ans3` соответственно будут по порядку записываться остатки от деления чисел на 2, а сами числа будут заменяться на целую часть от деления на 2. После цикла присвоим `fi, se, th, fo` значения остатков, записанных в одну строку. 

```bash
until [ $var -eq 0" ]
do
  ost=$(($var%2))
  var=$((var/2))
  ans+=$ost
done
fi=${ans}
```
![изображение](https://github.com/user-attachments/assets/f23e7c8f-36d6-4620-9f11-c4e2bcbbdb92)


7. Т.к в каждом октете адреса в двоичной системе счисления должно быть 8 символов, а могут быть использованы числа, при переводе которых в двоичную систему счисления получаеются числа, состоящих из меньшего количства символов, то в начало этих чисел добавляется нужное количество нулей. Сделаем это с помощью цикла until, но пока будем добавлять эти нули в конец чисел

```bash
until [ $(expr length "$fi") -eq 8 ]
do
  fi="$fi"0
done
```

8. Выведем в обратном порядке получившиеся значения, разделяя их точкой для получения нужного IPv4 адреса в двоичной системе счисления

```bash
rev <<< ""$fo"."$th"."$se"."$fi""
```

![изображение](https://github.com/user-attachments/assets/c138d1d3-1f7b-4cee-a09e-e62d37a09db8)
 

9. Сделаем несколько проверок:

```bash
./system.bash
192.168.10.1
```

```bash
./system.bash
213.180.193.0
```

![изображение](https://github.com/user-attachments/assets/5070638a-10bb-41a1-894b-e2d5de5d2072)

### Слава богу все работает, ура!
