# Bookshelf 📚


---
# Introduction
This note will serve as a collection of reviews for books that I've read. Each book review will be it's own note, and those notes will be listed here. For books with extensive notes, a review will appear at the top. 

Genres include political, STEM, fiction, and non-fiction. 

See also: my [political education spreadsheet](https://docs.google.com/spreadsheets/d/1c-6TxhakZ8W11JKfjjqAnlqMNkpzgPUhMxNm5y3s0KE/edit#gid=0)

# Fiction books
```dataview 
TABLE author AS Author
FROM #book 
WHERE file.name != "001 - start"
WHERE genre = "fiction"
SORT file.name
```

# Non-fiction books
```dataview 
TABLE author AS Author
FROM #book 
WHERE file.name != "001 - start"
WHERE genre = "non-fiction"
SORT file.name
```

# Political works
```dataview 
TABLE author AS Author
FROM "Literature & Reference" 
WHERE file.name != "001 - start"
WHERE genre = "political"
SORT author
```

# STEM works
```dataview
TABLE author AS Author
FROM "Literature & Reference"
WHERE genre = "STEM"
SORT file.name
```

# Unsorted literature
```dataview
TABLE author AS Author, genre AS Genre, format AS Format
FROM "Literature & Reference"
WHERE genre = null
SORT genre
```