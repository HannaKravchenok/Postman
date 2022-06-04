**[HW_Postman_2_Kravchenok](#HW_Postman_2_Kravchenok)**
___
[first](#first)  
[user_info_3](#user_info_3)  
[object_info_3](#object_info_3)  
[object_info_4](#object_info_4)  
[user_info_2](#user_info_2)  
___
# HW_Postman_2_Kravchenok<a name="HW_Postman_2_Kravchenok"></a>   
___
## first<a name="first"></a>  
___
*Create new collection - New request*  
*метод GET*  
*в поле "Enter request URL" вписать http://162.55.220.72:5007/first и нажать Save*

1. Отправить запрос.     
в url ввела http://162.55.220.72:5005/first  
Нажать Send  
ответ    
```
This is the first responce from server!
```  
2. Статус код 200   

перейти в поле Tests  
выбрать из списка справа Status Code is 200  
в поле ввода кода тестов:  
```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});  

```
Save - Send  
во вкладке Test Results  
```
PASS Status code is 200
```
3. Проверить, что в body приходит правильный string.  
```javascript
pm.test("Проверить, что в body приходит правильный string", function () {
    pm.response.to.have.body("This is the first responce from server!");
});
```
____
## user_info_3<a name="user_info_3"></a>
___
*Add request * 
*метод POST*  
*в поле "Enter request URL" вписать http://162.55.220.72:5005/user_info_3 и нажать Save*

1. Отправить запрос.    

нажать Send

2. Статус код 200

перейти в поле Tests  
выбрать из списка справа Status Code is 200  
в поле ввода кода тестов:  
```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
Save - Send  
во вкладке Test Results  
```
PASS Status code is 200
```
3. Спарсить response body в json.  

из списка справа выбрать Response body: JSON value check  
в окне редактирования тестов оставить код:  
```javascript
let jsonData = pm.response.json();
console.log(jsonData)
```

Проверить содержимое переменной, выводя ее в Console:
```
{age: "36", family: {…}, name: "Anna"…}
```
4. Проверить, что name в ответе равно name s request (name вбить руками.)  

из списка справа выбрать Response body: *JSON value check*  
в окне редактирования тестов оставить код:
```javascript
let name = jsonData.name
let name_1 = "Anna"
pm.test("name", function () {
        pm.expect(name).to.eql(name_1);
});
```
во вкладке Test Results
```
PASS name 
```
5. Проверить, что age в ответе равно age s request (age вбить руками.)  

в окне редактирования тестов оставить код:
```javascript
let age = jsonData.age
let age_1 = "36"
pm.test("age", function () {
        pm.expect(age).to.eql(age_1);
});
```
во вкладке Test Results
```
PASS age 
```

6. Проверить, что salary в ответе равно salary s request (salary вбить руками.)    

в окне редактирования тестов оставить код:
```javascript
let salary = jsonData.salary
let salary_1 = "1000"
pm.test("salary", function () {
        pm.expect(salary).to.eql(+salary_1);
});
```
во вкладке Test Results
```
PASS salary 
```
7. Спарсить request.  

в окне редактирования тестов оставить код:
```javascript
let req = request.data
```
8. Проверить, что name в ответе равно name s request (name забрать из request.)  

в окне редактирования тестов оставить код:  
```javascript
pm.test("name_req", function () {
        pm.expect(name).to.eql(req.name);
});
```
во вкладке Test Results
```
PASS name_req 
```
9. Проверить, что age в ответе равно age s request (age забрать из request.)  

в окне редактирования тестов оставить код:  
```javascript
pm.test("age_req", function () {
        pm.expect(age).to.eql(req.age);
});
```  
во вкладке Test Results
```
PASS age_req 
```
10. Проверить, что salary в ответе равно salary s request (salary забрать из request.)  

в окне редактирования тестов оставить код:  
```javascript
pm.test("salary_req", function () {
        pm.expect(salary).to.eql(+req.salary);
});
```
во вкладке Test Results
```
PASS salary_req 
```
11. Вывести в консоль параметр family из response.  

в окне редактирования тестов оставить код:  
```javascript
let Family = jsonData.family
console.log(Family)
```
проверить содержимое переменной, выводя ее в Console:  
```

{children: [2], u_salary_1_5_year: 4000}  
```
12. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request)  

в окне редактирования тестов оставить код:  
```javascript
pm.test("salary_1.5 year", function () {
        pm.expect(jsonData.family["u_salary_1_5_year"]).to.eql(+req.salary*4);
});
```
во вкладке Test Results
```
PASS salary_1.5 year
```
___
## object_info_3<a name="object_info_3"></a>  
___
*Add request * 
*метод GET*  
*в поле "Enter request URL" вписать http://162.55.220.72:5005/object_info_3 и нажать Save*  

1. Отправить запрос.  

нажать Send  

2. Статус код 200   

перейти в поле Tests  
выбрать из списка справа Status Code is 200  
в поле ввода кода тестов:  
```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
Save - Send  
во вкладке Test Results  
```
PASS Status code is 200
```

3. Спарсить response body в json.  

в поле ввода кода тестов: 
```javascript
let jsonData = pm.response.json();
```

4. Спарсить request.  

в поле ввода кода тестов:
 ```javascript
let req = pm.request.url.query.toObject()
```

5. Проверить, что name в ответе равно name s request (name забрать из request.)  

в поле ввода кода тестов:
 ```javascript
let name = jsonData.name
let name_r = req.name
pm.test("Name", function () {
        pm.expect(name).to.eql(name_r);
});
``` 
во вкладке Test Results  
```
PASS Name
```
6. Проверить, что age в ответе равно age s request (age забрать из request.)  

в поле ввода кода тестов:
 ```javascript
let age = jsonData.age
let age_r = req.age
pm.test("Age", function () {
        pm.expect(age).to.eql(age_r);
});
```
во вкладке Test Results
```
PASS Age
````

7. Проверить, что salary в ответе равно salary s request (salary забрать из request.)

в поле ввода кода тестов:

```javascript
let salary = jsonData.salary
let salary_r = req.salary
pm.test("Salary", function () {
        pm.expect(salary).to.eql(+salary_r);
});
``` 
во вкладке Test Results
```
PASS Salary
````
8. Вывести в консоль параметр family из response.  

в поле ввода кода тестов:

```javascript
let Family = jsonData.family
console.log(Family)
```
в Console:
```
{children: [2], pets: {…}, u_salary_1_5_year: 4000}
````

9. Проверить, что у параметра dog есть параметры name.  

в поле ввода кода тестов:
```javascript
pm.test("dog_name", function () {  
    pm.expect(jsonData.family.pets.dog).to.haveOwnProperty('name');   
});
```
во вкладке Test Results
```
PASS dog_name
````
10. Проверить, что у параметра dog есть параметры age.  

в поле ввода кода тестов:
```javascript
pm.test("dog_age", () => {
    pm.expect(jsonData.family.pets.dog).to.haveOwnProperty('age');   
});
```
во вкладке Test Results
```
PASS dog_age
````

11. Проверить, что параметр name имеет значение Luky.  

в поле ввода кода тестов:
```javascrip
pm.test("dog_Luky", () => {
    pm.expect(jsonData.family.pets.dog.name).to.eql( 'Luky');
});
```
во вкладке Test Results
```
PASS dog_Luky
````

12. Проверить, что параметр age имеет значение 4.  

в поле ввода кода тестов:
```javascrip
pm.test("dog_4", () => {
    pm.expect(jsonData.family.pets.dog.age).to.eql( 4);
}); 
```
во вкладке Test Results
```
PASS dog_4
````
___

## object_info_4<a name="object_info_4"></a>  
___
*Add request*  
*метод GET*  
*в поле "Enter request URL" вписать http://162.55.220.72:5005/object_info_4 и нажать Save*  

1. Отправить запрос.  

нажать Send  

2. Статус код 200   

перейти в поле Tests  
выбрать из списка справа Status Code is 200  
в поле ввода кода тестов:  
```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
Save - Send  
во вкладке Test Results  
```
PASS Status code is 200
```

3. Спарсить response body в json.  

в поле ввода кода тестов: 
```javascript
let jsonData = pm.response.json();
```

4. Спарсить request.  

в поле ввода кода тестов:
 ```javascript
let req = pm.request.url.query.toObject()
```
5. Проверить, что name в ответе равно name s request (name забрать из request.)  

в поле ввода кода тестов: 
 ```javascript
let name = jsonData.name
let name_r = req.name
pm.test("Name", function () {
        pm.expect(name).to.eql(name_r);
});
```
во вкладке Test Results  
```
PASS Name
```
6. Проверить, что age в ответе равно age из request (age забрать из request.)  

в поле ввода кода тестов: 
 ```javascript
let age = jsonData.age
let age_r = req.age
pm.test("Age", function () {
        pm.expect(age).to.eql(+age_r);
});
```
во вкладке Test Results  
```
PASS Age
```
7. Вывести в консоль параметр salary из request.  

в поле ввода кода тестов: 
 ```javascript
let Salary_req = req.salary
console.log(Salary_req)
```
в Console:  
```
"1000" 
```
8. Вывести в консоль параметр salary из response.  

в поле ввода кода тестов: 
 ```javascript
let Salary = jsonData.salary
console.log(Salary)
```
в Console:  
```
[1000, "2000", "3000"]
```

9. Вывести в консоль 0-й элемент параметра salary из response.  

в поле ввода кода тестов: 
 ```javascript
let Salary_0 = jsonData.salary[0]
console.log(Salary_0)
```
в Console:  
```
1000
```
10. Вывести в консоль 1-й элемент параметра salary параметр salary из response.  

в поле ввода кода тестов: 
 ```javascript
let Salary_1 = jsonData.salary[1]
console.log(Salary_1)
```
в Console:  
```
"2000"
```
11. Вывести в консоль 2-й элемент параметра salary параметр salary из response.  

в поле ввода кода тестов: 
 ```javascript
let Salary_2 = jsonData.salary[2]
console.log(Salary_2)
```
в Console:  
```
"3000"
```
12. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request.)  

в поле ввода кода тестов: 
 ```javascript
pm.test("Salary_0", function () {
        pm.expect(Salary_0).to.eql(+Salary_req);
});
```
во вкладке Test Results  
```
PASS Salary_0
```
13. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request.)  

в поле ввода кода тестов: 
 ```javascript
pm.test("Salary_1", function () {
        pm.expect(+Salary_1).to.eql(+Salary_req*2);
});
```
во вкладке Test Results  
```
PASS Salary_1
```
14. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request.) 

в поле ввода кода тестов: 
 ```javascript
pm.test("Salary_2", function () {
        pm.expect(+Salary_2).to.eql(+Salary_req*3);
});
``` 
во вкладке Test Results  
```
PASS Salary_2
```

15. Создать в окружении переменную name  

в меню слева выбирать *Environment - New Environment - HW_Postman_2* В строку *Variable* внести название переменной *name*, в *Current value - Anna*

16. Создать в окружении переменную age  

в меню слева выбирать *Environment - HW_Postman_2*. В строку *Variable* внести название переменной *age*, в *Current value - 36*

17. Создать в окружении переменную salary  

в меню слева выбирать *Environment - HW_Postman_2*. В строку *Variable* внести название переменной *salary*, в *Current value - 1000*

18. Передать в окружение переменную name  

вернуться в коллекции, в *object_info_4*, во вкладку *Tests*, прописать код:
```javascript
pm.environment.set("name", name);
```

19. Передать в окружение переменную age 

вернуться в коллекции, в *object_info_4*, во вкладку *Tests*, прописать код:
```javascript
pm.environment.set("age", age);
```

20. Передать в окружение переменную salary  

вернуться в коллекции, в *object_info_4*, во вкладку *Tests*, прописать код:
```javascript
pm.environment.set("salary", Salary[0]);
```
21. Написать цикл который выведет в консоль по порядку элементы списка из параметра salary.  

в поле ввода кода тестов:  
```javascript
jsonData.salary.forEach(function(s){
       console.log(s);
   });
   ```
в Console:  
```
 
1000
 
"2000"
 
"3000"
```
___
## user_info_2<a name="user_info_2"></a>
___

*Add request*  
*метод POST*  
 *в поле "Enter request URL" вписать http://162.55.220.72:5005/user_info_2 и нажать Save*

1. Вставить параметр salary из окружения в request  

перейти во вкладку *Body - from-data* в столбце *Value* напротив *'salary'* написать *{{Salary}}*

2. Вставить параметр age из окружения в age  

в столбце *Valu*e напротив *'age'* написать *{{Age}}*

3. Вставить параметр name из окружения в name  

в столбце *Value* напротив *'name'* написать *{{Name}}*

4. Отправить запрос.  

Save - Send  

5. Статус код 200

перейти во вкладку Tests, в окне редактирования тестов оставить код:
```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
во вкладке Test Results  
```
PASS Status code is 200
```
6. Спарсить response body в json.  

в поле ввода кода тестов:
```javascript
let jsonData = pm.response.json();
```

7. Спарсить request.

в поле ввода кода тестов:  
```javascript
let req = request.data
```

8. Проверить, что json response имеет параметр start_qa_salary  

в поле ввода кода тестов:
```javascript
let item_1 =  {"start_qa_salary": 1000}
pm.test("start_qa_salary", () => {
    pm.expect(jsonData).to.deep.include(item_1);
});
```
во вкладке Test Results  
```
PASS start_qa_salary
```

9. Проверить, что json response имеет параметр qa_salary_after_6_months  

в поле ввода кода тестов:
```javascript
let item_4 =  { "qa_salary_after_6_months": 2000}
pm.test("qa_salary_after_6_months", () => {
    pm.expect(jsonData).to.deep.include(item_4);
});
```
во вкладке Test Results  
```
PASS qa_salary_after_6_months
```
10. Проверить, что json response имеет параметр qa_salary_after_12_months  

в поле ввода кода тестов:
```javascript
let item_2 =  {"qa_salary_after_12_months": 2700.0}
pm.test("qa_salary_after_12_months", () => {
  
  pm.expect(jsonData).to.deep.include(item_2);
});
```
во вкладке Test Results  
```
PASS qa_salary_after_12_months
```
11. Проверить, что json response имеет параметр qa_salary_after_1.5_year  

в поле ввода кода тестов:
```javascript
let item_3 =  {"qa_salary_after_1.5_year": 3300.0}
pm.test("qa_salary_after_1.5_year", () => {
    pm.expect(jsonData).to.deep.include(item_3);
});
```
во вкладке Test Results  
```
PASS qa_salary_after_1.5_year
```
12. Проверить, что json response имеет параметр qa_salary_after_3.5_years  

в поле ввода кода тестов:
```javascript
let item_6 = { "qa_salary_after_3.5_years": 3800.0}
pm.test("qa_salary_after_3.5_years", () => {
    pm.expect(jsonData).to.deep.include(item_6);
});
```
во вкладке Test Results  
```
PASS qa_salary_after_3.5_years
```
13. Проверить, что json response имеет параметр person  

в поле ввода кода тестов:
```javascript
let item_5 =  {  "person": {
        "u_age": 36,
        "u_name": [
            "Anna",
            1000,
            36
        ],
        "u_salary_5_years": 4200.0
    },}
pm.test("person", () => {
  
  pm.expect(jsonData).to.deep.include(item_5);
});
```
во вкладке Test Results  
```
PASS person
```
14. Проверить, что параметр start_qa_salary равен salary из request (salary забрать из request.)  

в поле ввода кода тестов:
```javascript
pm.test("ЗП_старт", function () {
    
    pm.expect(jsonData.start_qa_salary).to.eql(+req.salary);
});
```
во вкладке Test Results  
```
PASS ЗП_старт
```
15. Проверить, что параметр qa_salary_after_6_months равен salary*2 из request (salary забрать из request.)  

в поле ввода кода тестов:
```javascript
pm.test("ЗП_через_6_мес", function () {
    
    pm.expect(jsonData.qa_salary_after_6_months).to.eql(+req.salary*2);
});
```
во вкладке Test Results  
```
PASS ЗП_через_6_мес
```
16. Проверить, что параметр qa_salary_after_12_months равен salary*2.7 из request (salary забрать из request.)  

в поле ввода кода тестов:
```javascript
pm.test("ЗП_через_12_мес", function () {
    
    pm.expect(jsonData.qa_salary_after_12_months).to.eql(+req.salary*2.7);
});
```
во вкладке Test Results  
```
PASS ЗП_через_12_мес
```
17. Проверить, что параметр qa_salary_after_1.5_year равен salary*3.3 из request (salary забрать из request.)  

в поле ввода кода тестов:
```javascript
pm.test("ЗП_через_1.5_года", function () {
    
    pm.expect(jsonData["qa_salary_after_1.5_year"]).to.eql(+req.salary*3.3);
});
```
во вкладке Test Results  
```
PASS ЗП_через_1.5_года
```
18. Проверить, что параметр qa_salary_after_3.5_years равен salary*3.8 из request (salary забрать из request.)  

в поле ввода кода тестов:
```javascript
pm.test("ЗП_через_3.5_года", function () {
    
    pm.expect(jsonData["qa_salary_after_3.5_years"]).to.eql(+req.salary*3.8);
});
```
во вкладке Test Results  
```
PASS ЗП_через_3.5_года
```
19. Проверить, что в параметре person, 1-й элемент из u_name равен salary из request (salary забрать из request.)  

в поле ввода кода тестов:
```javascript
pm.test("Пункт_19", function () {
    
    pm.expect(jsonData.person.u_name[1]).to.eql(+req.salary);
});
```
во вкладке Test Results  
```
PASS Пункт_19
```
20. Проверить, что что параметр u_age равен age из request (age забрать из request.)

в поле ввода кода тестов:
```javascript
pm.test("Пункт_20", function () {
    
    pm.expect(jsonData.person.u_age).to.eql(+req.age);
});
```
во вкладке Test Results  
```
PASS Пункт_20
```
21. Проверить, что параметр u_salary_5_years равен salary*4.2 из request (salary забрать из request.)  

в поле ввода кода тестов:
```javascript
pm.test("Пункт_21", function () {
    
    pm.expect(jsonData.person.u_salary_5_years).to.eql(+req.salary*4.2);
});
```
во вкладке Test Results  
```
PASS Пункт_21
`````
22. ***Написать цикл который выведет в консоль по порядку элементы списка из параметра person.  

Вариант 1:  
в поле ввода кода тестов:
```javascript
const obj = jsonData.person;
for(let el in obj) {console.log(el)}
```
в Console:
```

"u_age"
 
"u_name"
 
"u_salary_5_years"
```

Вариант 2:  
в поле ввода кода тестов:
```javascript
for(let el in obj) {console.log(`key: ${el}, value: ${obj[el]}`)}
```
в Console:
```
"key: u_age, value: 36"
 
"key: u_name, value: Anna,1000,36"
 
"key: u_salary_5_years, value: 4200"
```