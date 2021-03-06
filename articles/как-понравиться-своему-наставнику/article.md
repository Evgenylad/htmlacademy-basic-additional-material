#Как понравиться своему наставнику
Для того чтобы стать хорошим специалистом, необходимо не только уметь переводить макеты в готовый документ, но и делать это правильно и понятно для других специалистов. В данной заметке указаны основные ошибки, а так же рекомендации к оформлению кода для начинающих верстальщиков.

##Быть уверенным в себе и в своих силах

##Единообразно оформлять код
Важное качество каждого верстальщика - наличие собственного стиля. Верстка по определённой методологии позволяет самому верстальщику проще и понятнее формировать конечный документ, а другим верстальщикам понимать этот документ. Существует большое количество методологий, которые описывают правила создания документов и стилевых файлов. Они достаточно объемные и требуют изучения на более поздних стадиях становления верстальщика.

Хорошим началом будет единообразное оформление документа:

* определитесь с разделителями названия классов `_` или `—`;
* определитесь с типами кавычек `""` или `''`;
* определитесь с последовательность атрибутов и тега и свойств у css;
* определитесь с количеством пробелов, которое вы будете использовать для каскада. Два или четыре проблеа.

В дальнейшем ваша задача использовать эти правила во всех последующих документах.

##Использовать каскад для разделения и вложенности элементов
Каскад полезен не только для внешнего вида документа, но и для самого верстальщика. На первое время он поможет избегать ошибок с неправильным закрытием тегов.

Несколько правил хорошего каскада (данные правила являются примером, а не парадигмой):

* Каждый вложенный элемент начинается с новой строки и имеет отступ(tab) от родительского элемента.
* Текстовые элементы не нуждаются в дополнительной табуляции.
* Каждое описание в CSS имеет название на первой строчке и свойства на последующих строчках с отступом.

Пример плохого каскада

```html
<div class="container">
<ul>
<li>
<a href=""></a><a href=""></a><a href=""></a>
</li>
</ul>
</div>
```
```css
h1{font-size: 36px;
line-height: 44px;
color: $black;font-weight: 800;}
```

Пример хорошего каскада

```html
<div class="container">
    <ul>
        <li>
            <a href=""></a>
            <a href=""></a>
            <a href=""></a>
        </li>
    </ul>
</div>
```
```css
h1{
   font-size: 36px;
   line-height: 44px;
   color: #000;
   font-weight: 800;
}
```

##Задавать понятные и правильные названия классов
Название класса должно откражать суть содержимого или объекта. Например:
```css
.wrapper{} //обертка
.feedback{} //отзыв
.button{} //кнопка
```

Названия классов не должны быть написаны транслитом, с ресского языка. Например:
```css
.zagolovok{}
.reklama{}
.osnovnoi-blok{}
.levo{}
```

Классы указывают на то, чем объект является, а не что в нем лежит. То есть если у вас есть блок с текстом у которого заголовок “Почему мы?” и произвольный текст, то его стоит назвать, например, `advantages-text`, а не `why-we-text`.

##Не использовать `<br>` в разметке
Перенос строки придумали для переноса строки внутри текстового элемента и только для него. Даже если внутри текстового элемента есть возможность перенести строку другими способами, например, ограничить ширину текстового элемента, то использовать этот тег не нужно. Тем более не нужно использовать его для переноса блочных элементов.

##Правильно использовать сетки
Достаточно обширное правило, но мне бы хотелось указать на два момента.

Первый - правильное определение типа сетки, `inline-block` или `float`. Сетка на `float` подходит для крупных сеточных элементов, которые занимают одну строку. Если же у вас блоки идут в несколько строк, например каталог, то лучше использовать `inline-block`.

Второй — типичные ошибки. При работе с `inline-block` родительскому элементу, который их оборачивает надо сбрасывать размер шрифта, а для самих элементов восстанавливать его.

При работе с `float` обязательно использование распорки для контейнера в котором они лежат.

##Проверять верстку на переполнение
Важно запомнить, что макет который мы верстаем может быть с тествым набором данных, поэтому необходимо проверять свою верстку с другим количеством текста. Желательно делать такую верстку, которая не развалится при добавлении в нее другого текста, большего размера. Это касается не только текстовых элементов, но и, например, пунктов навигационного меню.

##Проверять верстку на кроссбраузерность
Головная боль всех верстальщиков — вопрос кроссбраузерности. Каждый браузер написан на своем движке, из-за чего некоторые свойства работаю по-разному. Другие свойства начинают работать только после добавления префиксов, а некоторые не работают вовсе.

Например свойство `box-sizing` с префиксами выглядит так:
```css
.class{
  -webkit-box-sizing: border-box;
     -moz-box-sizing: border-box;
          box-sizing: border-box;
}
```
На самом деле смысл разбирать какие свойства как работают, в этой статье, я не вижу. Это займет миллион страниц. Для вас задача на первое время научиться пользоваться Google.

Алгоритм ваших действий такой:
1. Вы определяете браузер до которого вам нужна поддержка.
2. Заходите на сервис http://caniuse.com/
3. Выбираете нужный вам тег или свойство CSS
4. Смотрите его поддержку.
5. Если у вас тег не поддерживается, то вы либо отказываетесь от него, либо ищите в Google как сделать его поддерживаемым.

Стоит отметить что в Интернет много сервисов на эту тему. Напрbмер http://css3please.com или http://css-tricks.com/snippets/ с пометкой cross-browser.

##Использовать семантику
Одним из нововведений HTML5 являются семантические теги. Отличаются от обычного `div` тем, что наделяют блок определенным смыслом. Для того чтобы научится использовать семантические теги нужно прочитать про них статью на английском http://www.w3schools.com/html/html5_semantic_elements.asp и закрепить это статьей на русском http://codeacademy.ru/blog/62/semanticheskaya-verstka-html5-nachalo-budushchego.
