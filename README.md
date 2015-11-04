# How to check if user can access Application?

Don't have time to search if this is somewhere in the dev guide already.

If you want to know which application user is associated with (like ServiceDesk, Software, Core) use following interfaces.

`ApplicationRoleManager` is the place to go to check what roles are in the system and what roles user has.

`ApplicationKey` is the application the user has access to.

If you are wondering what Applications there are, look no further, there's `ApplicationKeys`.
