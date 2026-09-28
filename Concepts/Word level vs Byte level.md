ref: [Byte vs Word](https://stackoverflow.com/questions/53337246/is-there-any-way-to-get-a-non-8-bit-multiple-data-type) 

When working with data, you can work with at byte level or word level.

At **Byte level** you are writing and storing data in byte groups (so 8-bits per group of data)

Whereas working on a **Word level** is where you write, store and read multiples of data with a single processing group (commonly 16-bit, 32-bit, 64-bit). This can typically rely on the biggest chunk of data a processor can process.