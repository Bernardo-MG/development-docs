---
description: Setting Up the Application
---

# Setting Up

## Authentication Manager

This will take care of authenticating users.

```
<authentication-manager>
   <authentication-provider user-service-ref="userDetailsService">
      <!-- <password-encoder ref="passwordEncoder" /> -->
   </authentication-provider>
</authentication-manager>
```

## Method Security

To activate security annotations:

```
<global-method-security pre-post-annotations="enabled" />
```

```
@EnableGlobalMethodSecurity(prePostEnabled = true)
```
