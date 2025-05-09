---
layout: blog
title: Quire
draft: false
date: 2025-03-02T13:46:00
date_updated: 2025-03-02T13:46:00
featured_image: /media/uploads/Screen%20Shot%202025-05-05%20at%2013.36.49.png
page_bg: oklch(26.9% 0.09 313.79)
excerpt: 'My second app launch of 2025: Quire, a Goodreads alternative with 100% local-first functionality.'
---
Quire is a book tracking app which integrates with the Open Library API and has basic features like “shelves”, reading history timelines, ratings, and comments. Track what books you’ve read and what you thought of them quickly and easily, and all completely locally on your computer.

## Stuff I learned while I was building

- I came back to SQLocal and Kysely for this, just like I did for NotesVac. It's a superb stack to work with, and I really enjoyed using both of these libraries again.

- I had to write some slightly more complex SQL to come up with views that I wanted.

- I built all of the views using DaisyUI v5, a Tailwind plugin that provides pre-styled and good-looking CSS components which is themable easily with CSS variables.

## My Favourite Feature

My favourite feature here is the history detail page, where you can see the book cover, title, author, and your reading history in a beautiful timeline. Not a particularly fascinating feature from a coding perspective, but I am quite pleased with how it looks.

## My Favourite Piece of Code

![](/media/uploads/carbon%284%29.svg)

I think this is my favourite piece of code, especially the \`orderBy\` clause. This piece of SQL ensures that unfinished reading sessions are sorted properly in the view, taking into consideration that the timeline of someone's readings of a particular book may be ongoing and not completed. The reason this is my favourite is not because it's particularly good, but because it took me a fair bit of reading to work it out, and it took quite a lot of tweaking and testing before I actually got a result I was happy with.

Anyway, if you want to check it out, it's live at https://quire.innes.hu
