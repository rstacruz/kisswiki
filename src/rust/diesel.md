- https://www.reddit.com/r/rust/comments/52or2h/is_it_feasible_to_use_diesel_without_automatic/

> There are various things I don't really like about ORMs in general, like the fact that using regular functions to build a query is confusing, or that you have to write your models in Rust even though you already have your schema in SQL form in another file.
But what really kills it for now is the fact that you have to do codegen in a build script. I don't use serde because of this, and I don't use diesel because of this.
Things will become interesting once plugins become stable, which is why I included "Again, procedural macros could come to our rescue.".
> -- https://www.reddit.com/r/rust/comments/53yoxz/my_adventures_in_rust_webdev/d7xhaqm

##

If you're using a fixed data set with structs, diesel can provide some functionality 
If you want to just generate raw queries, you probably don't need diesel

## comparting to rust-postgres

https://hackernoon.com/comparing-diesel-and-rust-postgres-97fd8c656fdd
