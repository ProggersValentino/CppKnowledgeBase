when creating and linking out program we may be only using a few functions from the ones created which then we are wasting the compiler's having to link all the functions despite there being some functions that aren't used.

this is where LTO comes in, it has the ability to filter out the functions that aren't used during link time so its able to only do the functions that are used
