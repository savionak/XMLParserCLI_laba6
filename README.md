# ООП лабораторная работа №6

<p>
  В библиотеке расширяемого программирования <a href="http://sourceforge.net/projects/grom/">Grom</a> существует класс <code>PropertyTree</code>, который позволяет загружать настройки и другие данные из XML-файлов.
  В этом классе существуют 4 главных свойства: <code>name</code>, <code>text</code>, <code>items</code>, <code>children</code>.
</p>
<p>
  Следующий пример поясняет сказанное:
</p>
<pre><code>&lt;name item1="..." ... itemN="..."&gt;
    &lt;child1 .../&gt;
    &lt;child2 .../&gt;
    ...
    &lt;childN .../&gt;
    text
&lt;/name&gt;</code></pre>
<p>
  За счет того, что <code>child</code>-элемент - это объект класса <code>PropertyTree</code>, можно строить в памяти и загружать из XML-файлов любые иерархии.
</p>
<p>
  Однако класс <code>PropertyTree</code> не вполне адекватно представляет XML-файл в памяти. Дело в том, что <code>text</code> в XML-файлах может быть "размазан" среди множества <code>child</code>-элементов. Например:
<p>
<pre><code>&lt;name item1="..." ... itemN="..."&gt;
    text1
    &lt;child1 .../&gt;
    text2
    &lt;child2 .../&gt;
    text3
    ...
    &lt;childN .../&gt;
    textN
&lt;/name&gt;</code></pre>
<p>
  Если следовать формальному определению XML, то <code>text</code> - это такой же узел, как и <code>child</code>.
  Кроме того, даже атрибут - <code>item</code> - это <code>child</code>-узел.
  Т.е. XML должен быть построен следующим образом.
</p>
<p>
  Существует базовый класс - <code>XMLNode</code>. Он представляет собой любой узел XML-дерева. В нем есть список дочерних узлов. Дочерние узлы представляются производными классами:
  <ul>
    <li><code>XMLAttribute</code> - <code>item</code>,</li>
    <li><code>XMLText</code> - <code>text</code>,</li>
    <li><code>XMLElement</code> - <code>child</code>,</li>
    <li><code>XMLComment</code> - коментарий,</li>
    <li><code>XMLCData</code> - любые данные в формате ASCII,</li>
    <li><code>XMLInstruction</code> - указание кодировки/схемы.</li>
  </ul>
</p>
<p>
  Необходимо изучить класс <code>PropertyTree</code> в библиотеке Grom, а также интерфейсы библиотеки MSXML от Microsoft и создать в библиотеке Grom классы, реализующие полную поддержку XML. Написать тестовую программу, которая загружает XML в память, редактирует его и сохраняет на диск. Проверить правильность работы собственных классов с помощью классов MSXML. Таким образом, студенты ознакомятся с концепциями библиотеки Grom и одновременно изучат формат XML.
</p>
Переработать классы задания так, чтобы их можно было использовать из программ, написанных на других языках программирования. Для этого воспользоваться понятием интерфейса. Допускается применение языка C++/CLI (это позволит воспользоваться классами на платформе .NET).
