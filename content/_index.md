---
# Leave the homepage title empty to use the site title
title: 
date: 2023-10-15
type: landing

sections:
  - block: hero
    content:
      title: |
        Computational Mechanics <br>
        <span style="color:#30B0E7"> 4 </span>The Curious Engineer 
      image:
        filename: ComputationalMechanics4TheCuriousEngineer-LOGO-BOX.png
      text: |
        <br>
        
        I've created this website to share my experience as a Mechanical Engineering Student. Let's explore Computational Mechanics together! 
  
  - block: collection
    content:
      title: Recent Posts
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
