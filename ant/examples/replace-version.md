# Replace Version

```markup
<target name="replace">
   <echo message="Replacing app versions with: ${newVersion}" />
   <echo message="Replacing in path: ${project.build.webapp}" />
   <path id="appPath">
      <fileset dir="${project.build.webapp}">
         <exclude name="**/build/**" />
      </fileset>
   </path>
   <echo message="Replacing in files: ${toString:appPath}" />
   <!-- "version" : "1.2.3" -->
   <replaceregexp match="(?&lt;=&quot;version&quot;)\s*\:\s*&quot;(.*)(?=&quot;)" replace="\: &quot;${newVersion}" flags="g">
      <fileset dir="${frontend.packages.path}" includes="**/package.json" />
   </replaceregexp>
</target>
```

