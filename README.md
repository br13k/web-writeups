<div align="center">

# WEB. Разборы задач с forkbomb.

</div>

# 📌 Menu
- [level1](https://github.com/br13k/web-writeups#-level1)
- [level2](https://github.com/br13k/web-writeups#-level2)
- [level3](https://github.com/br13k/web-writeups#-level3)
- [level4](https://github.com/br13k/web-writeups#-level4)
- [level5](https://github.com/br13k/web-writeups#-level5)
- [level6](https://github.com/br13k/web-writeups#-level6)
- [level23]()
- [Чай](https://github.com/br13k/web-writeups#-чаек)
- [So easy](https://github.com/br13k/web-writeups#-so-easy)
- [Ez](https://github.com/br13k/web-writeups#-ez)

## 📌 level1

<div align="center">

  ​​​​​​</br>![image](https://user-images.githubusercontent.com/121574230/212356325-1311d956-f441-494b-9b72-a57f46e5c71a.png)
  
</div>

Задача для тупых, люблю такие) Переходим по ссылке и смотрим флаг: `KSL{fc813aadb96c4a00b6887f73cee4efde}`

[Menu](https://github.com/br13k/writeups#-menu)

## 📌 level2

<div align="center">

  ​​​​​​</br>![image](https://user-images.githubusercontent.com/121574230/212356632-8905f8b6-21f6-4cff-a330-4ec0f5968e21.png)
  
</div>

Через инструменты разработчика глядим код страницы и находим флаг: `KSL{4dc7b79ae6f3c46c904970ff7cdcecda}`

[Menu](https://github.com/br13k/writeups#-menu)

## 📌 level3

<div align="center">

  ​​​​​​</br>![image](https://user-images.githubusercontent.com/121574230/212357941-874cabda-4abc-4916-9e6b-64bdbbc68f25.png)
  
</div>

Зоходим через curl и получаем флаг: `KSL{1cd1426c8929600867035e44edf22329}`


![image](https://user-images.githubusercontent.com/121574230/212357676-c866c1ee-9df4-4722-a658-4ce5c418603e.png)


[Menu](https://github.com/br13k/writeups#-menu)

## 📌 level4

<div align="center">

  ​​​​​​</br>![image](https://user-images.githubusercontent.com/121574230/212358018-7c7bc6ad-088b-4b0a-b610-292f2413e519.png)
  
</div>

Отправляем нужный post запрос через curl или например python requests и получаем: `KSL{a6354c29e728214e69c8fda2298b35fb}`

```Python 3
import requests

s = requests.Session()

data = {
	'want_flag': 'YES',
	'code': 1337
}

r = s.post('http://kslweb1.spb.ctf.su/first/level4/', data=data)

print(r.text)

```

[Menu](https://github.com/br13k/writeups#-menu)

## 📌 level5

<div align="center">

  ​​​​​​</br>![image](https://user-images.githubusercontent.com/121574230/212362756-bea22818-2f40-4bb6-8018-b89193968985.png)
  
</div>

То же самое, единственное, если делать через curl, то нужно правильно записать пробелы и символы &: 

```
curl -d "fun=Kaspersky+%26+Summer+%26+Lab" http://kslweb1.spb.ctf.su/first/level5/
```


Флаг: `KSL{72772dd0eee640322a3ecfb24ecab17b}`


[Menu](https://github.com/br13k/writeups#-menu)

## 📌 level6

<div align="center">

  ​​​​​​</br>![image](https://user-images.githubusercontent.com/121574230/212364139-0da3fc2b-02b1-4424-9f36-65b803afa6ba.png)
  
</div>

Здесь нужно указать header. Я делал на Python ツ

``` Python 3
import requests

header = {'SPbCTF': 'Pretty cool'}

r = requests.get('http://kslweb1.spb.ctf.su/first/level6/', headers=header)

print(r.text)
```


Флаг: `KSL{72772dd0eee640322a3ecfb24ecab17b}`


[Menu](https://github.com/br13k/writeups#-menu)

## 📌 Level23

<div align="center">

  ​​​​​​</br>![image](https://user-images.githubusercontent.com/121574230/217216363-7e2487c6-fbff-4780-a4ed-31da62e30804.png)

</div>

Задача на куки. Нам нужно набрать 1337 голосов, для этого пишем скриптец:

``` Python
import requests

s = requests.Session()
c = '1:7bc858c0d521f3bdf696f7187c2da177'

for i in range(1337):
	s.cookies.set('votes', c)
	r = s.get('http://kslweb1.spb.ctf.su/second/level23/')
	a = str(r.text)
	c = a[a.find("votes=") + 6:]
	c = c.partition('\n')[0]
	print(r.text)
```

Флаг: `KSL{a3908a69183647a1e68e515b6e52880a}`

[Menu](https://github.com/br13k/writeups#-menu)

## 📌 Чаек

<div align="center">

  ​​​​​​</br>![image](https://user-images.githubusercontent.com/121574230/209860261-8ae82fb2-96a1-4e6d-89a0-d47c12d0986d.png)

</div>

ПеРеРыВ нА чАй

[Menu](https://github.com/br13k/writeups#-menu)

## 📌 So easy

<div align="center">

  ​​​​​​</br>![image](https://user-images.githubusercontent.com/121574230/212365987-df1c67a6-fd6e-4db8-b19c-6221f29721a0.png)
  
</div>

Requests session


```Python 3
import requests

s = requests.Session()

s.params.update({'view_flag': 'yes'})

s.get('https://intro.spbctf.com/soeasy/')

data = {
	'fake': 'no'
}

r = s.post('https://intro.spbctf.com/soeasy/', data=data)

print(r.text)
```


Флаг: `spbctf{r3st_c1i3n7_1s_th3_b35t_w4y}`


[Menu](https://github.com/br13k/writeups#-menu)

## 📌 Ez

<div align="center">

  ​​​​​​</br>![image](https://user-images.githubusercontent.com/121574230/216763435-cd84e6d6-4bc2-45bf-82b4-e16cc3fbdf34.png)
  
</div>

Простейший SSTI. Зырим страницу: https://simple.ssti.2537ly.space и видим код приложения, заходим в директорию **/vulnerable**, которую отрыли в коде и видим, что можно поиграться с именем пользователя. Вводим в адресную строку следующее:

```
https://simple.ssti.2537ly.space/vulnerable?username={{config}}
```

![image](https://user-images.githubusercontent.com/121574230/216763815-781654a3-dacd-4b99-9097-af7efab0728c.png)

Получаем флаг: `spbctf{GoOooD_job_with_first_SSTI}`


[Menu](https://github.com/br13k/writeups#-menu)

# 📌 ВСЁ!

<div align="center">

  ​​​​​​</br>![image](https://media.tenor.com/HoFb_jBbB48AAAAC/ералаш.gif)
  
</div>

