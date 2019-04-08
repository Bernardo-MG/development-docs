---
description: Setting Up the Application
---

# Setting Up

## Authentication Manager

This will take care of authenticating users.

```text
<authentication-manager>
   <authentication-provider user-service-ref="userDetailsService">
      <!-- <password-encoder ref="passwordEncoder" /> -->
   </authentication-provider>
</authentication-manager>
```

## Method Security

To activate security annotations:

```text
<global-method-security pre-post-annotations="enabled" />
```

```text
@EnableGlobalMethodSecurity(prePostEnabled = true)
```

