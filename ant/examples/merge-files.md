# Merge Files

```markup
<target name="concatenateLocaleDesktop">
   <echo message="Concatenating locale in: ${frontend.locale.path}/build-es.js" level="debug" />
   <echo message="Obtaining from path: ${frontend.locale.app.path}app-es.js" level="debug" />
   <echo message="Obtaining from path: ${frontend.packages.path}" level="debug" />
   <echo message="Obtaining from path: ${frontend.locale.extension.path}" level="debug" />
   <concat encoding="UTF8" destfile="${frontend.locale.path}/build-es.js">
      <fileset dir="${frontend.locale.app.path}" includes="app-es.js" />
      <fileset dir="${frontend.packages.path}" includes="**/*-es.js" excludes="**/*mobile*-*.js" />
      <fileset dir="${frontend.locale.extension.path}" includes="**/*-es.js" erroronmissingdir="false" />
   </concat>
</target>
```

