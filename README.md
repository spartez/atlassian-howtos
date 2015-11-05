# How to check if user can access Application?

Don't have time to search if this is somewhere in the dev guide already.

If you want to know which application user is associated with (like ServiceDesk, Software, Core) use following interfaces.

`ApplicationRoleManager` is the place to go to check what roles are in the system and what roles user has.

`ApplicationKey` is the application the user has access to.

If you are wondering what Applications there are, look no further, there's `ApplicationKeys`.

# How to set your plugin's license during tests?

For JIRA test you can do following. The first thing is to create [Backdoor client](https://bitbucket.org/atlassian/jira-testkit/)

```
backdoor = new Backdoor(new TestKitLocalEnvironmentData());
```

In case you extended `BaseJiraWebTest` for your test you already have access to `backdoor` class from it. Once you have backdoor, just call:

```
backdoor.plugins().setPluginLicense("key-of-your-plugin", TIMEBOMB_LICENSE_FOR_TESTING);
```

You can obtain TIMEBOMB_LICENSE_FOR_TESTING from [Developers site](https://developer.atlassian.com/market/add-on-licensing-for-developers/timebomb-licenses-for-testing)
