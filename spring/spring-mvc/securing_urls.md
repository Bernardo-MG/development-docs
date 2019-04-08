# Securing URLS

This will set up three access settings:

```markup
<http>
   <intercept-url pattern="/static/**" access="permitAll" />
   <intercept-url pattern="/login*" access="permitAll" />
   <intercept-url pattern="/**" access="isAuthenticated()" />
</http>
```

| URL | Access control |
| :--- | :--- |
| /static/\*\* | None. Everybody can access. |
| /login\* | None. Everybody can access. |
| /\*\* | Only authenticated users. |

Note that the wildcard for authenticated URLs covers the other two. But as these are located before they will get a higher priority, and override the more restrictive control.

