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

# Upgrade tasks are failing when deploying via atlas-cli pi

```
[INFO] [talledLocalContainer] 		Error creating bean with name 'task002InitialStatuses': Instantiation of bean failed; nested exception is org.springframework.beans.BeanInstantiationException: Could not instantiate bean class [com.spartez.nbf.upgrade.Task002InitialStatuses]: No default constructor found; nested exception is java.lang.NoSuchMethodException: com.spartez.nbf.upgrade.Task002InitialStatuses.<init>()
[INFO] [talledLocalContainer] 			Could not instantiate bean class [com.spartez.nbf.upgrade.Task002InitialStatuses]: No default constructor found; nested exception is java.lang.NoSuchMethodException: com.spartez.nbf.upgrade.Task002InitialStatuses.<init>()
[INFO] [talledLocalContainer] 				com.spartez.nbf.upgrade.Task002InitialStatuses.<init>()
[INFO] [talledLocalContainer] 
```

Classes from atlassian-spring-scanner-runtime were not added to your plugin. Run `rm -rf target/dependency-maven-plugin-markers/` to force maven dependency plugin to attach all the deps again and it will solve the problem.
