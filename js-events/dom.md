<p>DOM (Document Object Model) представляет собой HTML разметку в JavaScript. Каждый тег представлен в виде JavaScript объекта и позволяет управлять (добавлять / изменять / удалять) элементы на странице из наших скриптов</p>

<p>Из помощью JavaScript можно:
  <ul>
    <li>Находить элементы на странице с помощью <code>document.querySelector</code>, <code>document.querySelectorAll</code>. Есть и другие (<code>document.getElementById</code>, <code>document.getElementByTagName</code>, <code>document.getElementByClassName</code> и т.д.), но они устарели и ими лучше не пользоваться</li> 
    <li>Создавать элементы с помощью <code>document.createElement</code></li> 
    <li>Вставлять элементы с помощью <code>element.append</code>, <code>element.prepend</code>, <code>element.after</code>, <code>element.before</code> и т.д</li> 
    <li>Считывать и задавать содержимое элементов с помощью <code>element.textContent</code>, <code>element.innerText</code>, <code>element.innerHTML</code>, <code>element.outerHTML</code> и т.д</li>
    <li>Управлять атрибутами HTML элементов с помощью <code>element.setAttribute</code> и <code>element.getAttribute</code></li>
    <li>Управлять классами HTML элементов с помощью <code>element.classList.add</code>, <code>element.classList.remove</code>, <code>element.classList.toggle</code>, <code>element.classList.contains</code> и т.д.</li>
    <li>И многое другое ...</li>
  </ul>
</p>

<h2>Поиск элементов на странице</h2>

<p>Чтобы найти элементы на странице есть много способов. В большинстве случаев нужно использовать 2 метода: <code>element.querySelector()</code> и <code>element.querySelectorAll()</code>.</p>

<p><code>element.querySelector('css selector')</code> - это метод DOM элемента. Перед точкой должен стоять DOM элемент, внутри которого будет происходить поиск. Чаще всего мы используем <code>document.querySelector</code>, чтобы искать по всему документу (да, <code>document</code> - это тоже DOM элемент).</p>

<p>При необходимости мы можем искать только внутри конкретного элемента DOM дерева (не во всем документе). Для этого нам сперва нужно найти этот элемент в документе <code>const firstElem = document.querySelector('.main-content')</code>, а потом внутри него найти тот, что вас интересует <code>const secondElem = firstElem.querySelector('.info')</code></p>

<p>В методы <code>element.querySelector</code>, <code>element.querySelectorAll</code> нужно передать как аргумент строку с CSS селектором (таким же, как мы используем в CSS для стилизации элементов). Метод <code>element.querySelectorAll</code> найдет все элементы внутри <code>element</code>, которые попадают под указанный селектор и вернет их в виде специального списка. Этот список является псевдомассивом! (не обычным массивом). Чтобы работать с этим списком, как с массивом, его нужно преобразоать к массиву например с помощью <code>Array.from(elemsList)</code></p>

<p>В свою очередь <code>element.querySelector</code> вернет лишь один первый попавшийся элемент, который подходит под CSS селектор в аргументе</p>


<h2>Считывание содержания элементов</h2>

<p>Содержимое DOM элементов можно прочитать как текст, проигнорировав все теги внутри. Или можно считать всю HTML разметку со всеми тегами и атрибутами</p>

<p>Для считывания содержимого DOM элемента в виде текста используются 2 свойства: <code>element.innerText</code> и <code>element.textContent</code>. Они работают похожим образом и возвращают весь текст (даже вложенных элементов).
  <pre>
    &lt;!-- index.html --&gt;
    &lt;div class="greeting"&gt;I am     learning    &lt;b&gt;Front-End&lt;/b&gt; &lt;/div&gt;
  </pre>
  <pre>
    /* index.js */
    const greetingElem = document.querySelector('.greeting');
    greetingElem.textContent; // 'I am     learning    Front-End'
    greetingElem.innerText; // 'I am learning Front-End'
  </pre>

  Как видите из примера выше, вывелся только текст. HTML теги проигнорировались. Разница между этими двумя способами в том, что <code>textContent</code> сохранил пробелы, что есть в HTML, а <code>innerText</code> отбросил лишние пробелы. На практике используйте тот, который лучше решает текущую задачу
</p>

<p>Cодержимое DOM элементов так же можно считывать в виде строки, но с сохранением всех тегов и атрибутов. То есть по сути HTML разметка в виде строки. Для этого используются 2 свойства: <code>element.innerHTML</code> и <code>element.outerHTML</code>
  <pre>
    &lt;!-- index.html --&gt;
    &lt;div class="greeting"&gt;I am learning &lt;b&gt;Front-End&lt;/b&gt; &lt;/div&gt;
  </pre>
  <pre>
    /* index.js */
    const greetingElem = document.querySelector('.greeting');
    greetingElem.innerHTML; // 'I am learning &lt;b&gt;Front-End&lt;/b&gt;'
    greetingElem.outerHTML; // '&lt;div class="greeting"&gt;I am learning &lt;b&gt;Front-End&lt;/b&gt; &lt;/div&gt;'
  </pre>

  <code>element.innerHTML</code> возвращает HTML разметку врутри целевого элемента, а <code>element.outerHTML</code> вернет еще и сам элемент.
</p>

<p>Все перечисленные выше элементы можно использовать и для установки содержимого элементов.<code>innerText</code> и <code>textContent</code> - для установки текстового содержимого элементов. <code>innerHTML</code> и <code>outerHTML</code> же создадут настоящие HTML элементы</code></p>

<p><code>innerHTML</code> еще, например, используется для очистки содержимого элементов. Для этого просто установите содержимое для элемента как пустую строку <code>element.innerHTML = '';</code></p>



<h2>Создание DOM элементов</h2>

<p>Из JavaScript можно создать DOM элемент и назначить ему все необходимые атрибуты. Для создания DOM элемента есть специальный метод <code>document.createElement</code>. Этот метод принимает один аргумент - строку (название тэга), которая говорит, какой именно элемент нужно создать. Например <code>const buttonElem = document.createElement('button');</code> создаст DOM элемент - кнопка</p>

<p>Все эти методы, что описаны ниже, могут быть вызваны на созданном DOM элементе, так и на DOM элементе, найденном на странице с помощью <code>document.querySelector</code></p>

<p>Из JavaScript можно задать элементу все необходимые атрибуты c помощью <code>element.setAttribute('attribute-name', 'attribute-value')</code>
  <pre>
    const imageElem = document.createElement('img');
    img.setAttribute('src', 'https://example.com/image.png');
    img.setAttribute('alt', 'Beautifull lake');
  </pre>
  Так же можно считывать атрибуты с DOM элемента с помощью <code>element.setAttribute('attribute-name')</code>:
</p>

<p>Для работы с атрибутом <code>class</code> есть специальные удобные методы
  <ul>
    <li><code>element.classList</code> - вернет список всех классов у элемента в виде специального объекта - псевдо массива</li>
    <li><code>element.classList.add('class-name')</code> - добавит элементу класс с именем <code>class-name</code></li>
    <li><code>element.classList.remove('class-name')</code> - удалит у элемента класс с именем <code>class-name</code></li>
    <li><code>element.classList.toggle('class-name')</code> - удалит у элемента класс с именем <code>class-name</code>, если такой уже есть. Или добавит, если у элемента такого класса нету</li>
    <li><code>element.classList.contains('class-name')</code> - вернет <code>true</code> если у элемента есть класс <code>class-name</code> или <code>false</code>, если у элемента такого класса нету</li>
  </ul>
</p>

<p>Иногда есть необходимость в HTML хранить некоторые данные, которые потом нужны в скриптах. Для этого существуют специальные атрибуты - data-attributes. Дата атрибуты имеют вид <code>data-user-id="123456"</code> - идет префикс <code>data-</code>, а за ним название пользовательского атрибута. Такое название связано с тем, чтобы наши пользовательские атрибуты не конфликтовали со стандартными HTML атрибутами. Для работы с такими атрибутами у DOM элементов есть специальное свойство <code>element.dataset</code>, которое позволяет работать с data-атрибутами как с объектом. Устанавливая и изменяя свойства в <code>element.dataset</code> мы автоматически изменяем data-атрибуты у HTML элемента
  <pre>
    &lt;!-- index.html --&gt;
    &lt;div data-user-id="12345" data-last-name="Johnson" class="user"&gt;Andrew&lt;/div&gt;
  </pre>
  <pre>
    /* index.js */
    const userElem = document.querySelector('.user');
    console.log(userElem.dataset); // { userId: '12345', lastName: 'Johnson' }
    userElem.dataset.age = 21;
    userElem.dataset.lastName = 'White';
  </pre>
  <pre>
    &lt;!-- index.html --&gt;
    &lt;div data-user-id="12345" data-last-name="White" data-age="17" class="user"&gt;Andrew&lt;/div&gt;
  </pre>

  Здесь интересный момент, заключается в именовании. Если название атрибута в HTML - маленькие буквы через дефиз, то свойства в <code>element.dataset</code> написаны в camelCase - убираем префикс <code>data-</code> и вместо дефисов каждое слово кроме первого начинаем с большой буквы
</p>


<h2>Вставка DOM элементов на страницу</h2>

<p>Когда вы создали DOM элемент в JavaScript, то его можно вставить на страницу несколькими способами:
  <ul>
    <li><code>parentElement.append(element)</code> - вставит DOM элемент <code>element</code> внутрь DOM элемента <code>parentElement</code>. Если в <code>parentElement</code> есть другие дочерние элементы, то <code>append</code> вставит новый элемент в конец (последним)
      <pre>
        &lt;!-- index.html before --&gt;
        &lt;ul class="list"&gt;
          &lt;li&gt;Old product&lt;/li&gt;
        &lt;/ul&gt;
      </pre>
      <pre>
        /* index.js */
        const newProductElem = document.createElement('li');
        newProductElem.textContent = 'New Product';
        const listElem = document.querySelector('.list');
        listElem.append(newProductElem);
      </pre>
      <pre>
        &lt;!-- index.html after --&gt;
        &lt;ul class="list"&gt;
          &lt;li&gt;Old product&lt;/li&gt;
          &lt;li&gt;New product&lt;/li&gt;
        &lt;/ul&gt;
      </pre>
    </li>
    <li><code>parentElement.prepend(element)</code> - вставит DOM элемент <code>element</code> внутрь DOM элемента <code>parentElement</code>. Если в <code>parentElement</code> есть другие дочерние элементы, то <code>prepend</code> вставит новый элемент в начало (первым в списке дочерних элементов)
      <pre>
        &lt;!-- index.html before --&gt;
        &lt;ul class="list"&gt;
          &lt;li&gt;Old product&lt;/li&gt;
        &lt;/ul&gt;
      </pre>
      <pre>
        /* index.js */
        const newProductElem = document.createElement('li');
        newProductElem.textContent = 'New Product';
        const listElem = document.querySelector('.list');
        listElem.prepend(newProductElem);
      </pre> 
      <pre> 
        &lt;!-- index.html after --&gt;
        &lt;ul class="list"&gt;
          &lt;li&gt;New product&lt;/li&gt;
          &lt;li&gt;Old product&lt;/li&gt;
        &lt;/ul&gt;
      </pre>
    </li>
    <li><code>someElement.before(element)</code> - вставит DOM элемент <code>element</code> перед DOM элементом <code>someElement</code>. То есть <code>someElement</code> и <code>element</code> будут сестринскими (sibling) элементами в разметке.
      <pre>
        &lt;!-- index.html before --&gt;
        &lt;ul class="list"&gt;
          &lt;li class="list-item"&gt;Old product&lt;/li&gt;
        &lt;/ul&gt;
      </pre>
      <pre>
        /* index.js */
        const newProductElem = document.createElement('li');
        newProductElem.textContent = 'New Product';
        const listItemElem = document.querySelector('.list-item');
        listItemElem.before(newProductElem);
      </pre>
      <pre>
        &lt;!-- index.html after --&gt;
        &lt;ul class="list"&gt;
          &lt;li&gt;New product&lt;/li&gt;
          &lt;li class="list-item"&gt;Old product&lt;/li&gt;
        &lt;/ul&gt;
      </pre>
    </li>
    <li><code>someElement.after(element)</code> - вставит DOM элемент <code>element</code> после DOM элемента <code>someElement</code>. То есть <code>someElement</code> и <code>element</code> будут сестринскими (sibling) элементами в разметке.
      <pre>
        &lt;!-- index.html before --&gt;
        &lt;ul class="list"&gt;
          &lt;li class="list-item"&gt;Old product&lt;/li&gt;
        &lt;/ul&gt;
      </pre>
      <pre>
        /* index.js */
        const newProductElem = document.createElement('li');
        newProductElem.textContent = 'New Product';
        const listItemElem = document.querySelector('.list-item');
        listItemElem.after(newProductElem);
      </pre>
      <pre>
        &lt;!-- index.html after --&gt;
        &lt;ul class="list"&gt;
          &lt;li class="list-item"&gt;Old product&lt;/li&gt;
          &lt;li&gt;New product&lt;/li&gt;
        &lt;/ul&gt;
      </pre>
    </li>
  </ul>

<h2>Поиск ближайшего родителя</h2>

<p>Часто бывает необходимо найти родилеля для некоторого элемениа. На родителе может хранится некая полезная информация, или с родителем нужно что-то сделать в зависимости от того, что происходит с дочерними элементами. Для это есть метод <code>element.closest(/* CSS selector */)</code>. Метод ищет ближайщий родительский элемент по DOM к <code>element</code>, который подходит под указанный CSS селлектор
  <pre>
    &lt;!-- index.html before --&gt;
    &lt;div class="one"&gt;
      &lt;p class="two"&gt;
        &lt;span class="three"&gt;&lt;/span&gt;
      &lt;/p&gt;
    &lt;/div&gt;
  </pre>
  <pre>
    /* index.js */
    const spanElem = document.querySelector('.three');
    spanElem.closest('.three'); // вернет его же (span)
    spanElem.closest('.two'); // вернет параграф
    spanElem.closest('.one'); // вернет div
  </pre>
</p>
