---
layout: page
use-site-title: true
---

<h2><u>Research Highlights</u></h2>

<div class="posts-list">
  {% for post in paginator.posts %}
  <article class="post-preview">
    <a href="{{ post.url | prepend: site.baseurl }}">
	  <h3 class="post-title">{{ post.title }}</h3>

	  {% if post.subtitle %}
	  <h3 class="post-subtitle">
	    {{ post.subtitle }}
	  </h3>
	  {% endif %}
    </a>

    <p class="post-meta">	    
      	<!--Posted on {{ post.date | date: "%B %-d, %Y" }}-->
	{{post.publish}}
    </p>
	  
    <div class="post-entry-container">
      <div class="post-entry">
        {{ post.excerpt | strip_html | xml_escape | truncatewords: site.excerpt_length }}
        {% assign excerpt_word_count = post.excerpt | number_of_words %}
        {% if post.content != post.excerpt or excerpt_word_count > site.excerpt_length %}
          <a href="{{ post.url | prepend: site.baseurl }}" class="post-read-more">[Read&nbsp;More]</a>
        {% endif %}
      </div>
    </div>
	  
    <p class="post-meta">
	{% if post.paperlink %}  
	    <!--[<a href="{{post.paperlink}}">paper</a>]-->
	    <span style="color: #0000ff;">[<a href="{{post.paperlink}}">paper</a>]</span>
	{% endif %} 
	{% if post.codelink %}  
	    <span style="color: #0000ff;">[<a href="{{post.codelink}}">code</a>]</span>
	{% endif %} 
	{% if post.resourcelink %}  
	    <span style="color: #0000ff;">[<a href="{{post.resourcelink}}">data</a>]</span>
	{% endif %} 
	<!--&nbsp;&nbsp; -->  	    
      	<!-- Posted on {{ post.date | date: "%B %-d, %Y" }} -->
    </p>

    {% if post.tags.size > 0 %}
    <div class="blog-tags">
      Tags:
      {% if site.link-tags %}
      {% for tag in post.tags %}
      <a href="{{ site.baseurl }}/tags#{{- tag -}}">{{- tag -}}</a>
      {% endfor %}
      {% else %}
        {{ post.tags | join: ", " }}
      {% endif %}
    </div>
    {% endif %}

   </article>
  {% endfor %}
</div>


	
