---
layout: default
title: Effect of contacts on spin lifetime measurements in graphene
author: Evan Sosenko
short_url: goo.gl/rc8q83
src_url: https://github.com/razor-x/deck-spin-lifetime
ucr_url: http://www.physics.ucr.edu/
coauthors: [ Vivek Aji ]
---

<style>h2::after{content:"{{ page.short_url }}"};</style>

{% slide header %}

<div style="text-align:center">
  <button id="auth-login" style="display:none">login</button>
  <button id="auth-logout" style="display:none">logout</button>
</div>

# {{ page.title }}
<ul class="authors">
  <li class="author"><a href="http://{{ site.data.meta.site_name }}">{{ page.author }}</a>
  </li>
  <li class"connector">with</li>
{% for coauthor in page.coauthors %}
  <li class="author coauthor">{{ coauthor }}</li>
{% endfor %}
</ul>
<div class="url">
  <div class="qrcode"></div>
  <a class="short_url" href="https://{{ page.short_url }}">{{ page.short_url }}</a>
</div>
<a class="ucr_logo" href="{{ page.ucr_url }}"></a>

{% endslide %}{% slide %}

## Body

{% endslide %}{% slide.my-class %}

## More body

{% endslide %}{% slide footer %}

## Final slide

{% if site.social %}
  {% capture social_buttons %}{% include social-buttons.html %}{% endcapture %}
{% endif %}

<div class="footer">
  <a class="ucr_logo" href="{{ page.ucr_url }}"></a>
  <ul class="colophon">
    <li><a href="http://{{ site.data.meta.site_name }}">{{ site.data.meta.site_name }}</a></li>
    <li><a class="src_url" href="{{ page.src_url }}">Source available on GitHub.</a></li>
  </ul>
  <div class="web-colophon">
    <a class="html5-badge" href="http://www.w3.org/html/logo/" title="HTML5 Powered with CSS3 / Styling, and Semantics"></a>
    {{ social_buttons | strip_newlines }}
  </div>
</div>

{% endslide %}

<div class="deck-status"><div class="deck-status-current"></div></div>