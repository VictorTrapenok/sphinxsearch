<h4>Поиск sphinxsearch с возможностью Replace на distributed индексе. </h4>
Эта сборка предназначена для решения бага <a href="http://sphinxsearch.com/bugs/view.php?id=1701" >0001701: SphinxQL INSERT, REPLACE for distributed index</a><br>
Проблема была в том что когда мы имеем следующий индекс<br>
<pre>
index dloc{
        type  = distributed
        agent = 127.0.0.1:3101:rtdtest|127.0.0.1:3202:rtdtest
        ha_strategy = nodeads
}
</pre>

Нельзя для него выполнить запрос insert или replace потому как мы получаем ошибку.<br>
В данной сборке можно. Только есть замечание что insert отрабатывает также как и replace.<br>

<h4>Для компиляции выполните в дирректории проекта</h4>
<pre>cmake . && make</pre>
Правки внесены в файлы<br>
<pre>
/src/searchd.cpp
/src/yysphinxql.h
</pre>