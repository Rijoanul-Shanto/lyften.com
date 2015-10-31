---
title: Portfolio
template: blog
---
<div class="tiles-container ">
    <div class="tiles-inner-container">

        {% for post in posts %}
        <div class="tile {{ post.tile }}">
            <figure>
                <img src="{{ post.image.full }}" alt="{{ post.title }}">
            </figure>

            <div class="tile-caption">
                <div class="caption-wrapper">
                    <a href="{{ post.url }}" class="caption-content">
                        <div>
                            <h1>{{ post.title }}</h1>
                            <div class="separator"></div>
                            <span class="subheader">{{ post.tag }}</span>
                        </div>
                    </a>
                </div>
            </div>
        </div>
        {% endfor %}
    </div>
</div>