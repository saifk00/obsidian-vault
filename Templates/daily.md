<%* const DATE = moment(tp.file.title, "YYYY-MM-DD"); %>[[<% DATE.subtract(1, 'D').format('YYYY-MM-DD') %>|Yesterday]] [[<% DATE.add(1, 'D').format('YYYY-MM-DD') %>|Tomorrow]]
# Notes
<% tp.file.cursor(1) %>
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
