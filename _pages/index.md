---
layout: page
title: Начало
id: home
permalink: /
---

<h1 class="custom-h">Прагмалогия</h1>


## Описание
Ислледование полезных действий.
<br>Продуктивность. Мышление. Взаимодействие.



<div>
  <input type="search" id="search-input" placeholder="Начните вводить для поиска" aria-label="Search">
</div>

<ul id="search-results"></ul>
<hr>

  <script src="/assets/simple-jekyll-search.min.js"></script>

  <script type="text/javascript">
    var sjs = SimpleJekyllSearch({
    searchInput: document.getElementById('search-input'),
    resultsContainer: document.getElementById('search-results'),
    json: '/assets/search.json',});
  </script>

<script type="text/javascript">
document.addEventListener('keydown', logKey);
function logKey(e) {
  var input = document.getElementById("search-input");
  if(input.value == ""){
    input.focus();
    //input.value = e.key;
  }
}
</script>

<!--<hr>-->

## Разделы

<ul>

{% assign sorted_projects = site.projects | sort: 'priority' %}
{% for proj in sorted_projects %}

<li>
  <h3><a href = "/{{proj.slug}}" class="internal-link">{{proj.title}}</a></h3>
  {{proj.description}}
    <ul>
        {% for taggroup in proj.intags %}

        {% assign current = 0 %}
        {% assign intags = taggroup | split: ',' %}
        {% assign count = intags.size %}

          <li>
            {% for tag in intags %}
              {% for t in site.tagpages %}
                {% if t.slug contains tag %}
                {% assign current = current | plus: 1 %}
                  <a class="internal-link" href="tagpage/{{t.slug}}">{{t.titles}}</a>
                  <span style="opacity: 0.5; padding: 0px; margin: 0px;">{% if current != count %}.{% endif %}</span>
                  {% break %}
                {% endif %}
              {% endfor %}
            {% endfor %}
          </li>
          {% endfor %}

    </ul>

  
</li>
<!--<hr>-->
{% endfor %}
</ul>


<h2>Хронология <a class = "internal-link" href = "timeline">→</a></h2>

{% assign sorted_notes = site.notes | sort: "date" | reverse  %}
{% assign count_notes = 0 %}
<ul>
      {% for note in sorted_notes  %}
        {% if note.tag contains "verbum" or note.tag contains "personality" or note.tag contains "ex" or note.tag contains "essentia" or note.tag contains "hmanalysis" or note.tag contains "hmcycles" or note.tag contains "hmglossary" or note.tag contains "hmphilosophy" or count_notes > 4 or note.date == nil %}

        {% else %}

            {% assign variable = note.tag %} 
            {% for item in site.tagpages %}
                {% if note.tags[0] contains item.slug %}
                    {% assign variable = item %}
                    {% break %}
                {% endif %}
            {% endfor %}

          <li><a class="internal-link" href="{{note.url}}">{{note.title}}</a>&nbsp;<a class="taglink" href="tagpage/{{variable.slug}}">#{{variable.title | downcase}}</a></li>
          {% assign count_notes = count_notes | plus: 1 %}
        {% endif %}
      {% endfor %}
</ul>

<!--<hr>-->

<h2 id="Contacts">Контакты</h2>
  <ul>
    <strong>
      <li><a href="https://t.me/originlook">Телеграм</a></li>
      <li><a href="https://vk.com/originlook">Вконтакте</a></li>
      <li><a href="mailto:originlookup@gmail.com">Почта</a></li>
    </strong>
  </ul>

<div class="info-border" style="margin-top: 2em; padding-top: 0.5em; cursor: pointer; border-color: var(--font-color);" onclick="window.location.href='https://t.me/+HnWkHz_eJ_gwMWUy';"> 
<span style="font-weight: 800; font-size: 1.2rem; color: var(--font-color); transition: all 0.5s ease-in-out; ">Становление Умозрения</span>
    <div style="display: block;justify-content: space-between;">
      <p style="color: var(--font-color); font-weight: 400;">Закрытый Телеграм-канал в формате «дневника писателя», в котором я делюсь комментариями к опубликованным в основном блоге материалам, голосовыми размышлениями и неопубликованными записями.
      </p>
      <div style="width: 168px; height: 40px;margin-left: auto; 
margin-right: 0;/* right: 0; *//* float: right; */ color: var(--bg-color); /* align-self: right; */ text-align: center;align-self: right; background-color: var(--font-color);
  border-radius: 0.5em;
  transition: all 0.5s ease-in-out;">
        <div style="height: 100%;display:flex; font-weight: 500;
        align-items: center;
        justify-content: center;"> Присоединиться </div>      
        </div>
    </div>
</div>

