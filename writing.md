<div id="articles">
{% for category in site.categories %}
  <h3>{{ category | first }}</h3>
    {% for posts in category %}
      {% for post in posts %}
      <ul>
        <li><a href="{{ post.url }}">{{ post.title }}</a></li>
      {% endfor %}
      </ul>
    {% endfor %}
{% endfor %}
</div>
