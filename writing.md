<div id="articles">
{% for category in site.categories %}
  <h3>{{ category | first }}</h3>
  <ul>
    {% for posts in category %}
      {% for post in posts %}
        {% if post.url %}
          <li><a href="{{ post.url }}">{{ post.title }}</a></li>
        {% endif %}
      {% endfor %}
    {% endfor %}
    </ul>
{% endfor %}
</div>
