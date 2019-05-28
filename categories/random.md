---
layout: page-doc
title: Random
subheading: Learn what I do apart from these technical stuff.
description: Learn what I do apart from these technical stuff.
color: grad-blog
image: /images/gems/random.png
permalink: /random
---

<div class="home-container">
  <div class="home-articles">
    <div class="home-wrapper">
      <div class="page-holder">
        <ul>
        {% for post in site.posts %}
          {% if post.category contains 'random' %}
            {% if post.class contains 'Entertainment' %}
                <li>
                  <a class="post-link" href="{{ site.baseurl }}{{ post.url }}">
                    <div class="page-treasure">
                      <h2>{{ post.title }}</h2>
                      <p>{{ post.description }}</p>
                    </div>
                  </a>
                </li>
              {% endif %}
              {% if post.class contains 'Travel' %}
                <li>
                  <a class="post-link" href="{{ site.baseurl }}{{ post.url }}">
                    <div class="page-treasure">
                      <h2>{{ post.title }}</h2>
                      <p>{{ post.description }}</p>
                    </div>
                  </a>
                </li>
              {% endif %}
            {% endif %}
        {% endfor %}
        </ul>
      </div>
    </div>
  </div>
</div>