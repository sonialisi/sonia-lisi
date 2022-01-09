---
layout: page
title: Publications
---

{% assign hashes = site.data.publications %}
{% capture posts %}
  {% for hash in hashes %}
    |{{ hash.year }}###{{ hash.title }}###{{ hash.paper-type }}###{{ hash.doc-url }}###{{ hash.journal-url }}###{{ hash.title }}###{{ hash.booktitle }}###{{ hash.journal }}###{{ hash.authors }}###{{ hash.code }}###{{ hash.bibtex }}###
  {% endfor %}
{% endcapture %}

{% capture conf_names %}
{% for hash in hashes %}
    |{{ hash.shortname }}
  {% endfor %}
{% endcapture %}


{% assign sortedhashes = posts | split: '|' | sort | reverse %}
{% for hash in sortedhashes %}
  {% assign hashitems = hash | split: '###' %}
  [comment]: <> {{ hashitems[0] }}
  {% if hashitems[5] == "" or hashitems[5] == nil %}
    {% break %}
  {% endif %}

  {% if hashitems[2] == "inproceedings" and hashitems[3] != "" %}
  * <a target="_blank" href="{{ hashitems[3] }}">{{ hashitems[5] }}</a>
  {% elsif hashitems[2] == "article" and hashitems[4] != "" %}
  * <a target="_blank" href="{{ hashitems[3] }}">{{ hashitems[5] }}</a>
  {% else %}
  * {{ hashitems[5] }}
  {% endif %}<br/>
  
  {{ hashitems[8] }}.

  {% if hashitems[2] == "inproceedings" %}*In: {{ hashitems[6] }}*, {{ hashitems[0]}}.
  {% elsif hashitems[2] == "article" %}*{{ hashitems[7] }}*, {{ hashitems[0]}}.
  {% endif %}
  {% if hashitems[10] != "" %}
 <code style="
     background: #f7f7f7;
     border-radius: 0.35em;
     border: solid 2px #efefef;
     font-family: 'Courier New', monospace; 
     display: block;
     overflow: scroll;
     white-space: nowrap;
 ">{{ hashitems[10] | linebreaksbr }}</code>
  {% endif %}

{% endfor %}