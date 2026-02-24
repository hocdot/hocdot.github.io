<!-- <h2 id="publications" style="margin: 2px 0px -15px;"><a href="{{ '/publication' | relative_url }}">Publications</a></h2> -->
<h2 id="publications" style="margin: 2px 0px -15px;">Publications</h2>

<div class="publications">
{% if group_by_year %}
  {% assign grouped = site.data.publications.main | group_by: "year" | sort: "name" | reverse %}
  {% assign counter = 1 %}
  {% for year_group in grouped %}
  <h3 style="margin: 1em 0 0.5em 0; font-size: 1.15rem;">{{ year_group.name }}</h3>
  <ol class="bibliography" start="{{ counter }}">
    {% for link in year_group.items %}
    <li>
      <div class="pub-row">
        <div class="col-sm-9" style="position: relative;padding-right: 0px;padding-left: 20px;">
          <div class="title">
            <span class="pub-counter">{{ counter }}.</span>
            <a href="{{ link.pdf }}">{{ link.title }}</a>
          </div>
          <div class="author">{{ link.authors }}</div>
          <div class="periodical">
            <em>
              {{ link.conference }} ({{ link.conference_short}})
              {% if link.notes %} - <i style="color:#e74d3c">{{ link.notes }}</i>{% endif %}
              {% if link.track %} - <i>{{ link.track }}</i>{% endif %}
            </em>
          </div>
          <div class="links">
            {% if link.pdf %} <a href="{{ link.pdf }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">PDF</a>{% endif %}
            {% if link.code %} <a href="{{ link.code }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">Code</a>{% endif %}
            {% if link.others %} {{ link.others }} {% endif %}
          </div>
        </div>
      </div>
    </li>
    {% assign counter = counter | plus: 1 %}
    {% endfor %}
  </ol>
  {% endfor %}
{% else %}
  <ol class="bibliography">
  {% assign counter = 1 %}
  {% for link in site.data.publications.main %}
  <li>
    <div class="pub-row">
      <div class="col-sm-9" style="position: relative;padding-right: 0px;padding-left: 20px;">
        <div class="title">
          <span class="pub-counter">{{ counter }}.</span>
          <a href="{{ link.pdf }}">{{ link.title }}</a>
        </div>
        <div class="author">{{ link.authors }}</div>
        <div class="periodical">
          <em>
            {{ link.conference }} ({{ link.conference_short}})
            {% if link.notes %} - <i style="color:#e74d3c">{{ link.notes }}</i>{% endif %}
            {% if link.track %} - <i>{{ link.track }}</i>{% endif %}
          </em>
        </div>
        <div class="links">
          {% if link.pdf %} <a href="{{ link.pdf }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">PDF</a>{% endif %}
          {% if link.code %} <a href="{{ link.code }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">Code</a>{% endif %}
          {% if link.others %} {{ link.others }} {% endif %}
        </div>
      </div>
    </div>
  </li>
  {% assign counter = counter | plus: 1 %}
  {% endfor %}
  </ol>
{% endif %}
</div>
