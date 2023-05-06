# MySQL

## Scenario 1: Invalid default value for '...'

1. Check the current sql_modes by command:
```mysql
show variables like 'sql_mode'; 
```
2. Modify `sql_mode`:
```mysql
SET sql_mode = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION';
```

## Scenario 2: Disable autocommit

1. Check the status of `autocommit`:
```mysql
show variables like 'autocommit';
```
2. Disable `autocommit`:
```mysql
SET AUTOCOMMIT = 0;
```

## Scenario 3: Perform a multiple-statement transaction

Here is an example:

```mysql
BEGIN;
SELECT *
FROM stock
WHERE id = 1 FOR
UPDATE;
UPDATE stock
SET name = 'AAA'
WHERE id = 1;
COMMIT; 
```

## Scenario 4: Select Charset

**utf8mb4**: A UTF-8 encoding of the Unicode character set using one to four bytes per character.

**utf8mb3**: A UTF-8 encoding of the Unicode character set using one to three bytes per character. This character set is
deprecated in MySQL 8.0, and you should use utfmb4 instead.

**utf8**: An alias for utf8mb3. In MySQL 8.0, this alias is deprecated; use utf8mb4 instead. utf8 is expected in a
future release to become an alias for utf8mb4.

**ucs2**: The UCS-2 encoding of the Unicode character set using two bytes per character. Deprecated in MySQL 8.0.28; you
should expect support for this character set to be removed in a future release.

**utf16**: The UTF-16 encoding for the Unicode character set using two or four bytes per character. Like ucs2 but with
an extension for supplementary characters.

**utf16le**: The UTF-16LE encoding for the Unicode character set. Like utf16 but little-endian rather than big-endian.

**utf32**: The UTF-32 encoding for the Unicode character set using four bytes per character.

## Scenario 5: Select Collation

A collation is a set of rules that defines how to compare and sort character strings.

**ci**: case-insensitive

**cs**: case-sensitive

**utf8mb4_bin**: case-sensitive as it compares the binary values of the character