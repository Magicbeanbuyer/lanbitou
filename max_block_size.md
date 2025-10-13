#clickhouse 
In ClickHouse, data is processed by [[block]]s (sets of column [[part]]s). 
The internal processing cycles for a single block are efficient enough, but there are noticeable expenditures on each block. 

The max_block_size setting is a recommendation for what size of the block (in a count of rows) to load from tables. 

The block size shouldn’t be too small, so that the expenditures on each block are still noticeable, but not too large so that the query with LIMIT that is completed after the first block is processed quickly. 

The goal is to avoid consuming too much memory when extracting a large number of columns in multiple threads and to preserve at least some cache locality.

Default value: 65,536.

Blocks the size of max_block_size are not always loaded from the table. If it is obvious that less data needs to be retrieved, a smaller block is processed.