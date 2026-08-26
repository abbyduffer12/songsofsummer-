---
layout: default
title: "Top 10 Songs of the Summer"
description: "A personal countdown of the songs that made this summer unforgettable."
---

<section class="hero">
  <div class="hero__content">
    <p class="eyebrow">The annual countdown</p>
    <h1>Top 10 songs<br><span>of the summer.</span></h1>
    <p class="hero__lede">Your definitive collection of the tracks, artists, and moments that shaped the season.</p>
    <a class="button" href="#countdown">Explore the countdown <span aria-hidden="true">↓</span></a>
  </div>
  <div class="hero__orb hero__orb--one"></div>
  <div class="hero__orb hero__orb--two"></div>
  <div class="hero__notes" aria-hidden="true">♫</div>
</section>

<section class="intro section-wrap">
  <p class="eyebrow">About this project</p>
  <h2>One season.<br><em>Ten essential songs.</em></h2>
  <p class="intro__text">Use this space to introduce your ranking, explain your criteria, and share what made this summer's soundtrack special.</p>
</section>

<section id="countdown" class="countdown section-wrap">
  <div class="section-heading">
    <div>
      <p class="eyebrow">The list</p>
      <h2>Meet the countdown</h2>
    </div>
    <p class="section-heading__hint">10 tracks · 10 stories</p>
  </div>
  <div class="song-grid">
    {% assign ranked_songs = site.songs | sort: "rank" %}
    {% for song in ranked_songs %}
      <a class="song-card" href="{{ song.url | relative_url }}">
        <div class="song-card__cover" style="--accent: {{ song.accent | default: '#ff5e5b' }}">
          <span class="song-card__rank">{{ song.rank | prepend: "#" }}</span>
          <span class="cover-placeholder">Cover image<br>placeholder</span>
        </div>
        <div class="song-card__meta">
          <span class="song-card__artist">{{ song.performer | default: "Performer name" }}</span>
          <h3>{{ song.title | default: "Song title" }}</h3>
          <span class="song-card__link">Read review <span aria-hidden="true">↗</span></span>
        </div>
      </a>
    {% endfor %}
  </div>
</section>
