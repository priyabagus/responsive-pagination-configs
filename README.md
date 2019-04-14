# Responsive Pagination Configs

This is set of predefined configurations for implementing responsive pagination.

## Limitation

At the moment, this repository only supports responsive pagination configurations :


- Maximum 25 pages
- 3 device breakpoints (small, medium, large devices)
  - Small : 0 - 2 edge & mid items
  - Medium : 0 - 3 edge & mid items
  - Large : 0 - 4 edge & mid items




## Components

_Mid items_ are pagination items surrounding the _current page_ item.
_Edge items_ are the rightmost & leftmost pagination items until dots.

Consider this example.

A pagination with 25 pages in total, and the current page is 12.

> 1  2  3  ... 10  11  **12**  13  14  ...  23  24  25

- Page 1, 2, 3 and 23, 24, 25 are _edge items_
- Page 10, 11 and 13, 14 are _mid items_
- Between page 3 & 10 also 14 & 23 are _dots_

## File Naming Format

Example : 
>config.s01.m12.l32.json

- `s`, `m`, and `l` are small, medium, and large device keys.
- `s01` means, for small devices it uses 0 edge item and 1 mid item.
- `m12` means, for medium devices it uses 1 edge item and 2 mid items.
- `l32` means, for large devices it uses 3 edge items and 2 mid items.

## JSON Elements
- Top level JSON config has an array of 25 elements, ordered by the number of total pages used in pagination. This defines the pagination which has _t_ number of total pages. 
So, first element is for the pagination which has total page of 1, while the last element is for the pagination which has the total page of 25.
- Second level : Inside the top level JSON config, there lies an array ordered by what page is the current page. So, if the current page of a pagination is 1, then it should use the first element of this second level array.

- Third level : Inside the second level array, there is another array. The length is dynamic. This array contains data of items that should be rendered.



## Reading the Items Data
Recap : If we store the configs to a variable named `config`, to get what items should be rendered for the _t_ total number of pages, and the current page is _c_, we can call it by:
> config[ t ] [ c ]

and it will return the set of items (array of objects) that should be rendered.

For each element of this returned array holds the data for a single item for the pagination. which could represent a _pagenumber_, a _dots_, or a _current page_. A single item is stored in form of object.

Object's key for an item:

- `p` : The page number of this item points to
- `t` : Type of item. The value could be the following
  - `nm` : This item is a _pagenumber_
  - `dt` : This item is a _dots_
  - `cr` : This item is the _current page_ item
- `x` : Exclusions (this item should be hidden in these device breakpoints) 

## License
[GPLv2](https://choosealicense.com/licenses/gpl-2.0/)

