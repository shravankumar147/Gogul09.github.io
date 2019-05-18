---
layout: page-default
heading: creations
title: Creations
subheading: my journey as a creator
description: This page contains all the creative stuff such as interactive demos and infographics related to machine intelligence which uses HTML5, CSS3, JavaScript, jQuery and Sass.
color: grad-creations
permalink: /creations/
---

<div class="blog-intro {{ page.color }}">
  <div>
    <h1>{{ page.heading }}</h1>
    <p>{{ page.subheading }}</p>
  </div>
</div>

<div class="home-container">
  <div class="home-articles">
    <div class="home-wrapper">
      <!--Demo STARTS-->
      <div style="display: block !important;">
        <div class="category-box">
          <ul>
            {% for post in site.posts %}
              {% if post.category contains 'software' %}
                {% if post.class contains 'Demo' %}
                  <li>
                    <a class="post-link" href="{{ site.baseurl }}{{ post.url }}">
                        <div class='demo_box'>
                          <img src="{{ post.image }}" />
                          <h4>{{ post.title }}</h4>
                          <p>{{ post.description }}</p>
                        </div>
                     </a>
                  </li>
                {% endif %}
              {% endif %}
            {% endfor %}
            <li>
              <div class='demo_box'>
                <a href="https://docs.google.com/presentation/d/e/2PACX-1vR2c4s31uAiZpRumnZfXwZVC1WK-0WtOhatyQ44JhhZo3MdqByqzHkL37t92_thzUW2tOo_gVsRStbY/pub?start=false&loop=false&delayms=3000" target="_blank"><img alt="first-meetup.png" src="/images/school-of-ai/first-meetup.png" /></a>
                <p>Chennai School of AI - First Meetup</p>
              </div>
            </li>
            <li>
              <div class='demo_box'>
                <img id="infographics-1" alt="ai-basics.png" src="/images/infographics/ai-basics.png" onclick="showHideModal(this.id);" />
                <p>Artificial Intelligence - Basics</p>
              </div>
            </li>
            <li>
              <div class='demo_box'>
                <img id="infographics-2" alt="supervised-learning.png" src="/images/infographics/supervised-learning.png" onclick="showHideModal(this.id);" />
                <p>Supervised Machine Learning</p>
              </div>
            </li>
          </ul>
        </div>
      </div>
      <!--Demo ENDS-->
    </div>
  </div>
</div>

<div id="creative_modal" class="modal">
  <button class="modal_download" id="modal_download" onclick="downloadImage()">Download</button>
  <span class="close">&times;</span>
  <img class="modal-content" id="modal_image">
</div>