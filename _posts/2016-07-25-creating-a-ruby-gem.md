---
layout: post
title: creating a ruby gem
---

"Facts are simple and facts are straight \\
Facts are lazy and facts are late \\
Facts all come with points of view \\
Facts don't do what I want them to."

   Talking Heads, "Crosseyed and Painless"

======
## the project
======

**requirements** >> build a CLI, packaged as a gem, that scrapes data from an external source.

**what** >> domestic_goods, a gem to help navigate you toward american-made companies.

**where** >> [rubygems](https://rubygems.org/gems/domestic_goods) / [github](https://github.com/bennorris/domestic_goods-cli-gem)

**why** >> it's hard to find ethically-made goods, and it shouldn't be. i started the project hoping to scrape a directory of companies that manufacture ethically, but wasn't able to find the perfect source. so the idea slowly transitioned to an interactive list of american-made companies separated by category.

======
## a takeaway
======

one of the most enjoyable parts of learning to write and read code is the flexibility involved with making something work. there is a certain rigidity, of course---there are boundaries that'll break your program every single time when crossed---but within those boundaries is a ton of freedom to explore different approaches.      

i've started to notice when my code gets clumsy, can sense when it's getting the job done but doing so ineloquently. the more time i spend looking through experienced programmers' work, the more i recognize the elegance of well-written code, mainly in the ability to make less do more.

the analogy with "crosseyed and painless" isn't perfect (but i'll take any excuse to quote talking heads). code, like fact, is a slippery business that's more flexible than it initially seems. and that's half the fun.

======
## lessons learned
======

-it's easy to get stuck on something trivial and spend hours wading through sites that lead nowhere particularly helpful. a great skill to develop moving forward: knowing when to take a different direction and just move on.

-

======
## simple, but helpful for other first-timers
======

when you're ready to push your gem to rubygems, you can build the package using:
``gem build gem_name.gemspec``

and then push it to rubygems with:
``gem push gem_name-0.1.0.gem``

if you need to delete after pushing, you can use:
``gem yank gem_name -v 0.1.0``
it's good to know that after using ``yank``, the version title is still visible on rubygems, but it's no longer downloadable. 
