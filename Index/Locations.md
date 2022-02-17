---
Aliases: [ "#location" ]
---

# Locations

```dataviewjs
const tag = dv.current().file.aliases[0];
const pages = dv.pages(tag + ' AND -"_templates"');
console.log(pages)
const etags = pages.file.etags.distinct().sort();
const previousTags = [];

etags.forEach(etag => {
  if (!etag.startsWith(tag)) return;
  
  const splitTag = etag.split("/")
  
  splitTag.forEach((h, i) => {
    if (previousTags[i] && previousTags[i] === h) return;
    
    previousTags[i] = h;
    dv.header(i + 2, splitTag.slice(0, i + 1).join("/"));
  });
  
  dv.list(pages.where(page => page.file.etags.includes(etag)).file.link.sort())
});
```
