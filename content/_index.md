---
# Leave the homepage title empty to use the site title
title: 
date: 2023-10-15
type: landing

sections:
  - block: hero
    content:
      title: |
        Computational Mechanics 4 The Curious Engineer
      image:
        filename: welcome.jpg
      text: |
        <br>
        
        Let's explore Computational Mechanics together! Whether you're a seasoned researcher, a student just starting your journey, or someone with a curious mind, this blog is your resource for all things related to computational mechanics.
  
  - block: collection
    content:
      title: Latest Publications
      subtitle:
      text:
      count: 5
      filters:
        author: ''
        category: ''
        exclude_featured: false
        publication_type: ''
        tag: ''
      offset: 0
      order: desc
      page_type: post
    design:
      view: card
      columns: '1'
  
  - block: markdown
    content:
      title:
      subtitle: ''
      text:
    design:
      columns: '1'
      background:
        image: 
          filename: coders.jpg
          filters:
            brightness: 1
          parallax: false
          position: center
          size: cover
          text_color_light: true
      spacing:
        padding: ['20px', '0', '20px', '0']
      css_class: fullscreen
---
