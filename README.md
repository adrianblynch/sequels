# Sequels

An SQL string can be built in many ways in JavaScript and other languages. Below are the variations I've seen and have used.

My personal favourite at the moment is the _Concatenated array items_.

Have your own way? Add it below.

## Single line

```javascript
var sql = 'SELECT * FROM table WHERE column = value';
```

### Pros

- Simple
- Minimal typing

### Cons

- Can't grow without becoming unreadable

## Multi line concatenated statements

```javascript
var sql = 'SELECT * ';
sql += 'FROM table ';
sql += 'WHERE column = value ';
```
  
Or if you'd like things to line up:
  
```javascript
var sql = '' ;
sql  = 'SELECT *' ;
sql += 'FROM table ';
sql += 'WHERE column = value ';
```

### Pros

- Simple(ish)
- Can grow as needed
- Each line is consistent

### Cons

- A space is needed on each line (beginning or end)
- A bunch more typing for each line

## Concatenated array items

```javascript
var sql = [
  'SELECT *',
  'FROM table',
  'WHERE column = value'
];
```

### Pros

- Nice to read
- Will grow
- No leading/trailing space needed

### Cons

- sql.join(' ') is needed when used


## Escape newline

```javascript
var sql = "SELECT * \
FROM table \
WHERE column = value";
```

### Pros

- No extra whitespace required
- No need for closing/opening quotes repeatedly
- Will grow

### Cons

- Having to escape newline looks ugly
- Whitespace after ecaped newline causes a vague error. The trailing space causes the issue `FROM•table•\•`


## Multiline npm module

```javascript
var sql = multiline(function(){/*
SELECT *
FROM table
WHERE column = value
*/});
```

### Pros

- Write everything as is
- No newline escape
- Will grow
- No extra whitespace

### Cons

- Extra package dependency
- Micro performance hit
- JavaScript only (AFAIK)

## Template strings

ES6 natively supports multiline strings.

```javascript
var sql = `
  SELECT *
  FROM table
  WHERE column = value`;
```

### Pros

- Write everything as is
- No newline escape
- Will grow

### Cons

- Requires using [es6-templates](https://github.com/esnext/es6-templates) to compile JavaScript written using template strings to use ES5-compatible syntax


## Knex

```javascript
knex('table').where({column: value})
```

### Pros

- Easy to multiline
- Easy to compose
- Limits SQL injection

### Cons

- Extra package dependency
- New syntax to learn
