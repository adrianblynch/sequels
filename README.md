# Sequels

## Single line

  var sql = 'SELECT * FROM table WHERE column = value';

### Pros

- Simple
- Minimal typing

### Cons

- Can't grow without becoming unreadable

## Multi line concatenated statements

  var sql = 'SELECT * ';
  sql += 'FROM table ';
  sql += 'WHERE column = value ';
  
Or if you'd like things to line up:
  
  var sql = '' ;
  sql  = 'SELECT *' ;
  sql += 'FROM table ';
  sql += 'WHERE column = value ';

### Pros

- Simple(ish)
- Can grow as needed
- Each line is consistent

### Cons

- A space is needed on each line (beginning or end)
- A bunch more typing for each line
