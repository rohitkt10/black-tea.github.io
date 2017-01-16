---
category: Vision Zero
---
# Crash Maps: Tufte Inspired
One of the problems that had previously been vexing me was how to accurately depict the incidence of collisions and injuries on our streets. It is very common to see heat maps of collisions or injuries. 

After attending a Tufte lecture here in Los Angeeles this past fall, I was reminded of his criticsm of newspaper charts from the 1980s.
These were some truly terrible charts, in case you forgot:

Because we map the collision incidence as a circle, the solution to this problem ends up being quite elegant.

The general thinking behind this approach:
- KSIs stand out because of the darker color and higher opacity. Since those are the focus of Vision Zero, we want them to stand out. 
- However, you can still see all collisions as well. This is important to show why we may propose engineering safety countermeasures even if there is a low KSI rate, especially if we are doing a corridor at a time. Since KSI is a subset of all collisions, the KSIs will never obscure the collision incidence charts.
- Using Tufte principles, I no longer have to worry about bucketing the circle radii into categories, which results in misrepresenting those at the boundary (eg. If we assign a collision count of 1-4 to have a radius = X and 5+ to have a radius = 2X, we are really misrepresenting the difference between 4 and 5 collisions by doubling the radius even though the incidence only increased by 1).

### How we do this in practice
