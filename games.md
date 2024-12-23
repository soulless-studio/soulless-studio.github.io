---
layout: page
title: Our Games
permalink: /games/
---

<!-- Font Awesome -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">

{% assign platform_info = 
  '{ "windows": { "name": "Windows", "icon": "fa-brands fa-windows" },
     "macos": { "name": "macOS", "icon": "fa-brands fa-apple" },
     "linux": { "name": "Linux", "icon": "fa-brands fa-linux" },
     "ps5": { "name": "PlayStation 5", "icon": "fa-brands fa-playstation" },
     "xbox": { "name": "Xbox Series X", "icon": "fa-brands fa-xbox" },
     "switch": { "name": "Nintendo Switch", "icon": "fa-solid fa-gamepad" },
     "web": { "name": "Web", "icon": "fa-solid fa-globe" },
     "ios": { "name": "iOS", "icon": "fa-brands fa-app-store-ios" },
     "android": { "name": "Android", "icon": "fa-brands fa-google-play" }
   }' | jsonify %}

<div class="game-grid">
  {% for game in site.data.games %}
    <div class="game-card">
      <div class="game-card-inner">
        <div class="game-card-front">
          <div class="game-cover-container">
            <img class="game-cover" src="{{ game.cover_image }}" alt="{{ game.title }}" />
            <div class="dvd-overlay"></div>
          </div>
          <div class="game-info">
            <h3 class="game-title">{{ game.title }}</h3>
            <p class="game-description">Click to see platforms</p>
          </div>
        </div>
        <div class="game-card-back">
          <h3 class="game-title">{{ game.title }}</h3>
          <p class="game-description">{{ game.description }}</p>
          <div class="platform-grid">
            {% assign platform_data = platform_info | fromjson %}
            {% assign sorted_platforms = game.platforms | sort %}
            {% for platform_id in sorted_platforms %}
              {% assign platform = platform_data[platform_id] %}
              <div class="platform-icon">
                <i class="{{ platform.icon }}"></i>
                <span>{{ platform.name }}</span>
              </div>
            {% endfor %}
          </div>
        </div>
      </div>
    </div>
  {% endfor %}
</div>

<script>
document.querySelectorAll('.game-card').forEach(card => {
  card.addEventListener('click', () => {
    card.classList.toggle('flipped');
  });
});
</script>