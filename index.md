---
layout: default
title: Uyanga Turmunkh
---

<!-- === ABOUT SECTION === -->
<section id="about" class="home-section">
  <div class="container">
    <div class="row">
      <!-- LEFT COLUMN: photo & info -->
      <div class="col-xs-12 col-md-5 text-center">
               <img src="{{ '/assets/turmunkh_bright.png' | relative_url }}"
             alt="Uyanga Turmunkh"
             class="img-circle img-responsive center-block">

        <div class="name-row">
          <h1 class="profile-name">Uyanga Turmunkh</h1>
          <span class="name-icons">
            <a href="https://scholar.google.com/citations?user=3NgcfZIAAAAJ&hl=en" target="_blank" rel="noopener">
              <i class="ai ai-google-scholar big-icon"></i>
            </a>
            <a href="https://www.linkedin.com/in/uyangaturmunkh" target="_blank" rel="noopener">
              <i class="fa fa-linkedin big-icon"></i>
            </a>
          </span>
        </div>
      </div>


      <!-- RIGHT COLUMN: biography text -->
      <div class="col-xs-12 col-md-6 col-md-offset-1">
        <h1>Biography</h1>
        <p>I am Associate Professor at <a href="www.ieseg.fr" target="_blank">IESEG School of Management</a>, Department of
<a href="https://www.ieseg.fr/en/faculty-and-research/
departments/economics-and-quantitative-methods/" target="_blank">Economics and Quantitative Methods</a>. 
I am faculty member at the <a href="https://lem.univ-lille.fr/" target="_blank">LEM</a> research laboratory (CNRS UMR 9221) and at the <a href="https://
irisk.ieseg.fr/" target="_blank">iRISK</a> Research Center on Risk and Uncertainty.</p>
<p>I graduated from <a href="https://www.eur.nl/en/ese" target="_blank">Erasmus University Rotterdam</a> in 2017 with a
PhD in Economics, specialising in Behavioral Economics. I study decision-making under risk and
ambiguity. I am particularly interested in applications in the areas of environmental economics,
public economics, and learning and development. Complete <a href="{{ site.baseurl }}/assets/Turmunkh_CV.pdf" target="_blank">CV</a>.
        </p>

      </div>

      <!--<div class="col-xs-12 col-md-6 col-md-offset-1">
        <h1>News</h1>
        <p>Insert News Here</p>

      </div>-->
    </div>
  </div>
</section>

<!-- === PUBLICATIONS === -->
<section id="publications" class="home-section">
  <div class="container">
    <div class="row">
      <div class="col-md-4 col-xs-12">
        <h1>Publications</h1>
      </div>
      <div class="col-md-8 col-xs-12">
        <ul class="pub-list">
        {% for p in site.data.publications %}
          <li class="pub-item row">
            <div class="col-sm-9">
              <h3 class="pub-title">{{ p.title }}</h3>

              <div class="pub-venue">
                {% if p.venue_link %}
                  <a href="{{ p.venue_link }}" target="_blank" rel="noopener">{{ p.venue }}</a>
                {% else %}
                  {{ p.venue }}
                {% endif %}{% if p.year %}, {{ p.year }}.{% endif %}
              </div>

              <div class="pub-authors">{{ p.authors }}</div>

              {% if p.links %}
              <div class="pub-actions">
                {% for l in p.links %}
                  {% assign href = l.url %}
                  {% if href contains '://' %}
                    {% assign final_href = href %}      
                  {% else %}
                    {% assign final_href = href | relative_url %} 
                  {% endif %}
                  <a class="btn-linkchip" href="{{ final_href }}" target="_blank" rel="noopener">
                    {% if l.icon and l.icon contains 'ai' %}
                      <i class="{{ l.icon }}"></i>
                    {% elsif l.icon %}
                      <i class="fa {{ l.icon }}"></i>
                    {% endif %}
                    {{ l.label }}
                  </a>
                {% endfor %}
              </div>
              {% endif %}
            </div>

            <div class="col-sm-3 hidden-xs">
              {% if p.thumb %}
                <img
                  src="{{ '/assets/' | append: p.thumb | relative_url }}"
                  class="pub-thumb img-responsive"
                  alt="Cover for {{ p.title }}">
              {% endif %}
            </div>
          </li>
        {% endfor %}
        </ul>

      </div>
    </div>
  </div>
</section>



<!-- === ONGOING PROJECTS === -->
<section id="projects" class="home-section">
  <div class="container">
    <div class="row">
      <div class="col-md-4 col-xs-12">
        <h1>Ongoing Projects</h1>
      </div>
      <div class="col-md-8 col-xs-12">

        <ul class="og-list" style="list-style:none;padding-left:0;margin:0;">
          {% for w in site.data.ongoing %}
          <li class="og-item">
            <!-- Meta (authors + date) -->
            {% if w.authors or w.date %}
            
<div class="og-meta">
  {% if w.authors %}
    <div class="og-authors">{{ w.authors }}</div>
  {% endif %}
  {% if w.date %}
    <div class="og-date">{{ w.date }}</div>
  {% endif %}
</div>

            {% endif %}

            <!-- Title -->
            <h3 class="og-title">{{ w.title }}</h3>

            <!-- Summary or note (fallback) -->
            {% if w.summary %}
              <p class="og-summary">{{ w.summary }}</p>
            {% elsif w.note %}
              <p class="og-summary">{{ w.note }}</p>
            {% endif %}

            <!-- Actions: PDF + custom links + fallback single link -->
            <div class="og-actions">
              {% if w.pdf %}
                <a class="btn-linkchip" href="{{ w.pdf | relative_url }}" target="_blank" rel="noopener">
                  <i class="fa fa-file-pdf-o"></i> PDF
                </a>
              {% endif %}

              {% if w.links %}
                {% for l in w.links %}
                  {% assign href = l.url %}
                  {% if href contains '://' %}
                    {% assign final_href = href %}
                  {% else %}
                    {% assign final_href = href | relative_url %}
                  {% endif %}
                  <a class="btn-linkchip" href="{{ final_href }}" target="_blank" rel="noopener">
                    {% if l.icon and l.icon contains 'ai' %}
                      <i class="{{ l.icon }}"></i>
                    {% elsif l.icon %}
                      <i class="fa {{ l.icon }}"></i>
                    {% endif %}
                    {{ l.label }}
                  </a>
                {% endfor %}
              {% endif %}

              {% if w.link and (w.links == nil) and (w.pdf == nil) %}
                <!-- Fallback single link from your current schema -->
                <a class="btn-linkchip" href="{{ w.link }}" target="_blank" rel="noopener">
                  <i class="fa fa-external-link"></i> Project URL
                </a>
              {% endif %}
            </div>
          </li>
          {% endfor %}
        </ul>

      </div>
    </div>
  </div>
</section>

<!-- === Teaching === -->
<section id="teaching" class="home-section">
  <div class="container">
    <div class="row">
      <div class="col-md-4 col-xs-12">
        <h1>Teaching</h1>
      </div>

      <div class="col-md-8 col-xs-12">

        <ul class="teaching-list">
          <li>
            <strong>Behavioral Economics & Managerial Decisions</strong><br>
            <span class="teaching-note">(Program: Master, Grande Ecole), Fall 2025</span>
          </li>
          <li>
            <strong>Applied Economics</strong><br>
            <span class="teaching-note">(Program: Bachelor in International Business), Spring 2026</span>
          </li>
          <li>
            <strong>Environmental Problems and Human Behavior</strong><br>
            <span class="teaching-note">(Program: Master in Management for Sustainability), Spring 2026</span>
          </li>
        </ul>
      </div>
    </div>
  </div>
</section>

<!-- === CONTACT === -->
<section id="contact" class="home-section">
  <div class="container">
    <div class="row">
      <div class="col-md-4 col-xs-12">
        <h1>Contact</h1>
      </div>
      <div class="col-xs-12 col-md-8">
        <ul class="fa-ul" style="margin-left:0;">
          <li><i class="fa-li fa fa-envelope"></i> <a href="mailto:u.turmunkh@ieseg.fr">u.turmunkh@ieseg.fr</a></li>
          <li><i class="fa-li fa fa-map-marker"></i> IESEG School of Management, Lille, France</li>
        </ul>
      </div>
    </div>
  </div>
</section>
