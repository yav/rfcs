- Feature Name: Record Puns
- Start Date: 03 October 2016
- RFC PR:
- Haskell



#######
Summary
#######

Add record puns to language.



##########
Motivation
##########

Record puns are a syntactic short-hand for extracting and defining the fields
of a record.   They are useful because they provide a concise syntax
for a common pattern of using records.  Record pun patterns are
similar to Pascal's `with` construct, and also to the import lists of
Haskell's module system.  Record pun expressions are dual to the patterns
and provide a concise notation for defining record values.


###############
Detailed design
###############

Record puns are implemented in GHC and may be enabled with the
`-XNamedFieldPuns` language extensions.

To illustrate their use we use the following Haskell data-type:

    data Color = Color { red, green, blue :: Float }

A record pun pattern allows us to abbreviate the pattern `Color { red = red }`
to simply `Color { red }`.  Similarly, a record pun expression allows us
to abbreviate the expression `Color { red = red, green = green, blue = blue }`
to `Color { red, green, blue }`.  Here is an example of using record puns
to define a function that only keeps the red channel of a color:

    onlyRed Color { red } = Color { red, green = 0, blue = 0 }

Record patterns are a completely syntactic feature, and could be implemented
entirely in the parser, where the puns could be expanded---no contextual
knowledge is needed at all.  Thus, whenever the parser encounters a field
`x` in a record pattern or expression, this should be expanded to `x = x`.
This also works with qualified names, except that the expansion uses an
unqualified name, so `Q.x` is expanded to `Q.x = x`.

Of course, an implementation may choose to keep the puns in its internal
representation so that it can report better error messages.



#########
Drawbacks
#########

Some programmers do not like record puns because one cannot freely rename
the punned variables.  For examples, we can't just change the pattern
(or expression) `Color { red, green, blue }` to
`Color { red1, green, blue }` and have the program still work, we'd have
to use `Color { red = red1, green, blue }` instead.


############
Alternatives
############

No known, so far.


####################
Unresolved questions
####################

None, so far.


