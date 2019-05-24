# Execute Command

```markup
<target name="update">
   <exec executable="sencha" dir="${frontend.path}" failonerror="true">
      <arg value="app" />
      <arg value="upgrade" />
      <arg value="${frontend.framework.install.path}" />
   </exec>
</target>
```

