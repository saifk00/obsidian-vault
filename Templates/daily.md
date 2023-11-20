<%* const DATE = moment(tp.file.title); %>[[<% DATE.clone().subtract(1, 'd').format('YYYY-MM-DD') %>|Yesterday]] [[<% DATE.clone().add(1, 'd').format('YYYY-MM-DD') %>|Tomorrow]]
# Notes
<% tp.file.cursor(1) %>
# Journal

# Notes created today
```dataview
List FROM ""
WHERE file.cday = date("<% tp.file.title %>")
SORT file.ctime asc
```

# Notes last touched today
```dataview
List FROM ""
WHERE file.mday = date("<% tp.file.title %>")
SORT file.mtime asc
```
