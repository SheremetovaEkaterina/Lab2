# Лабораторная работа №2. Основы верстки
- _Выполнила:_ Шереметова
- _Язык программирования:_ Java

## Что делает приложение?
Приложение состоит из 4 экранов:
1. [Меню](#activity1).
2. [Экран 2](#activity2), который сверстан с использованием `LinearLayout`.
3. [Экран 3](#activity3), который сверстан с использованием `RelativeLayout`.
4. [Экран 4](#activity4).

<p align="center">
    <img src="https://github.com/user-attachments/assets/7f5ed5c2-0e3d-47b3-810f-da584de1e1fa" width="200"> 
    <img src="https://github.com/user-attachments/assets/b2b759a7-0cb5-44a4-a942-c47bea82737e" width="200">
    <img src="https://github.com/user-attachments/assets/44c97abf-2866-4755-91ab-1dc3dbc12c48" width="200"> 
    <img src="https://github.com/user-attachments/assets/6149cf78-ee76-4d47-88bf-6c06dc8729cb" width="200">
</p> 
Возврат на предыдущий экран осуществляется при помощи системной кнопки / бэксвайпа

---
### <a id="activity1"> Меню (экран 1) </a>

**_Меню состоит из 4х кнопок:_**
- **"Перейти к экрану 2"**. По тапу - > открытие [`SecondActivity`](#activity2)
- **"Перейти к экрану 3"**. По тапу -> открытие [`ThirdActivity`](#activity3)
- **"Перейти к экрану 4"**. По тапу -> открытие [`FourthActivity`](#activity4)
- **"Выйти"**. По тапу -> выход из приложения.

_**Общее по кнопкам:**_
- высота каждой кнопки составляет **20%** от высоты экрана
- расстояние между кнопками - **2%**
- ширина кнопок - **75%**
- расстояние от первой кнопки до верхнего края **==** расстоянию от последней кнопки до нижнего края **== 7%**
- кнопки выровнены по центру.
  <p align="center">
    <img src="https://github.com/user-attachments/assets/7f5ed5c2-0e3d-47b3-810f-da584de1e1fa" width="200"> 
</p> 

---
### <a id="activity2"> Экран 2 (SecondActivity)</a>
**_Особенность экрана:_** сверстан с использованием `LinearLayout`.  

**Состоит из 7 кнопок:**
- 3 расположены в верхней части экрана (`android:layout_gravity="top"`) и занимают равную ширину
- 2 расположены по центру (`android:layout_gravity="center"`), занимают равные части, но имеют отступы от краев
- 3 расположены в нижней части экрана (`android:layout_gravity="bottom"`):
    - 1 занимает половину всей ширины экрана
    - 2 делят оставшуюся часть поровну между собой
  <p align="center">
    <img src="https://github.com/user-attachments/assets/b2b759a7-0cb5-44a4-a942-c47bea82737e" width="200">
</p> 

Для задания размеров и положения использовались следующие **свойства `LinearLayout`**:
- `android:layout_weight` // отвечает за соотношение размеров между элементами
- `android:layout_gravity` // указывает расположение внутри `LinearLayout`

---

### <a id="activity3"> Экран 3 (ThirdActivity)</a>
**_Особенность экрана:_** сверстан с использованием `RelativeLayout`, т.е. местоположение объектов задается относительно других.

**Состоит из 6 кнопок:**
- 2 расположены в верхней части экрана и занимают по половине экрана
- 3 расположены по центру
- 1 расположена в нижней части экрана

<p align="center">
    <img src="https://github.com/user-attachments/assets/44c97abf-2866-4755-91ab-1dc3dbc12c48" width="200"> 
</p> 

Для задания размеров и положения использовались следующие **свойства `RelativeLayout`**:
- _относительно родительского `RelativeLayout`_:
    - `android:layout_alignParentStart="true"` // левый верхний угол
    - `android:layout_alignParentRight="true"` // правый верхний угол
    - `android:layout_centerInParent="true"` // центр
    - `android:layout_alignParentBottom="true"` // нижняя часть
- _относительно других объектов:_
    - `android:layout_toLeftOf = "@+id/.."` // "Left 50%" и "Center_left"
    - `android:layout_toRightOf="@+id/.."` // "Right 50%" и "Center_right"
  

 ---
 ### <a id="activity4"> Экран 4 (FourthActivity)</a>
 
На экране расположена всего 1 кнопка. Ее особенности:
- выровнена по центру экрана
- имеет темно-зеленый цвет
- слева от текста изображена иконка приложения
- цвет обводки кнопки `#505050`
- толщина обводки `12px` (т.к. я родилась в декабре)
- радиус скругления кнопки `24dp`
- при нажатии на кнопку ее цвет изменяется на светло-зеленый.
<p align="center">
    <img src="https://github.com/user-attachments/assets/6149cf78-ee76-4d47-88bf-6c06dc8729cb" width="200">
    <img src="https://github.com/user-attachments/assets/dc166769-c10a-4558-a716-dcbf301fd017" width="200"> 
</p> 

Для выполнения выше указанных условий был создан файл `my_button_bg` внутри папки `drawable`:
- т.к. при нажатии цвет должен изменяться, используется класс `selector`, включающий в себя 2 объекта `item` (для состояния "нажато" и "не нажато").
- каждый объект имеет одинаковую структуру:
    - ``` java
      <item android:state_focused="false"
        android:state_pressed="true" // если объект не нажат, то будет false
        android:state_enabled="true">
        <shape xmlns:android="http://schemas.android.com/apk/res/android"
        android:shape="rectangle" > // создается фигура прямоугольник
            <solid android:color="@android:color/holo_green_light" /> // указывается цвет фигуры
            <corners android:radius="24dp"/> // определяется радиус скругления
            <stroke android:width="12px" android:color="#505050" /> // задается толщина и цвет обводки
        </shape>
      </item>
      ```

Чтобы подтянулись все параметры, внутри файла с версткой экрана (`activity_fourth.xml`) указано следующее:
  - `android:background="@drawable/my_button_bg"` // фон кнопки
  - `android:drawableLeft="@drawable/ic_launcher_foreground"` // добавление иконки в левой части кнопки
