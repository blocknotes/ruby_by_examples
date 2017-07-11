# Rails static site generator

The last week-end I decided to try to staticize a Rails website without external dependecies, a sort of fullpage cache.

Here you can find a task to do it: `rake static:generate`

To generate only a specific route: `rake static:generate[page]`

It could also be expandend to generate the sitemap (with a gem like *xml-sitemap*)