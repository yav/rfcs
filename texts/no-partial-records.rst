- Feature Name: No partial records
- Start Date: 04 October 2016
- RFC PR: Leave this empty, filled on proposal accept
- Haskell Report Issue: Leave this empty, filled on proposal accept



#######
Summary
#######

Do not allow the definition of records with missing fields.



##########
Motivation
##########

The current Haskell standard allows omitting fields when defining
record values---omitted fields are automatically initialized to contain
an undefined value.  This is error prone because it is usually not the
behavior intended by the programmer and, indeed, GHC has the option
of warning when such fields are omitted.  The current behavior is also
not very well specified, as it is unclear exactly what sort of undefined
value one should put in the omitted fields
(e.g., should it be a catchable error).


###############
Detailed design
###############

I propose that we disallow records with uninitialized fields, essentially
promoting GHC's warning into an error.

This solves two problems:
    1. Programmers would not be able to accidentally forget to initialize a
       field. For example, if a record declaration gains a new field, the
       program will not compile until all record constructions are updated
       to initialize the new field.
    2. If programmers wish to leave a field as undefined, then they will
       have to provide an explicit undefined value.  This makes it obvious
       that something interesting is going on with this record, and it
       allows them to be explicit about the kind of error they would like to
       use (e.g., `undefined` or throw some sort of more useful error).

Implementing this should be fairly straight forward---implementations already
have to do this check for strict fields, and GHC already has code to emit
warnings for uninitialized non-strict fields.



#########
Drawbacks
#########

This is not a fully backward compatible change as programs that relied on
uninitialized record fields would stop compiling.

Fixing this is easy though---one simply needs to add explicit definitions
for the uninitialized value.  This is a fully backward compatible change,
and it does not require any sort of CPP or other hacks.

############
Alternatives
############

None known so far.


####################
Unresolved questions
####################

None known so far.

