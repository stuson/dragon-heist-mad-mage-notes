---
Aliases: [ "#session" ]
---

# Sessions

```dataviewjs
const tag = dv.current().file.aliases[0];
const pages = dv.pages(tag)
const etags = pages.file.etags.distinct().sort()


etags.forEach(etag => {
  if (!etag.startsWith(tag)) return;
  const hLevel = etag.split("/").length + 1;
  dv.header(hLevel, etag);
  dv.list(pages.where(page => page.file.etags.includes(etag)).file.link.sort())
})
```
