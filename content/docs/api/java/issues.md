---
weight: 20
---

# javaDataPipeline Issues

Issues can be attached to Object_components, as well as to the Submission Script, Config File, and Code Repo.

Issues can be created and then linked to the elements that they apply to, or they can be raised directly on the element it refers to.

Here is an example of the creation then linking of an Issue to components, Script, and Code Repo:

```Java

try (Coderun coderun = new Coderun(configPath, scriptPath, token)) {
    Data_product_read dp = coderun.get_dp_for_read("existing/dpname");
	Object_component_read oc1 = dp.getComponent("comp1");
	Object_component_read oc2 = dp.getComponent("comp2");
    Issue i = coderun.raise_issue("A serious issue", 10);
    i.add_components(oc1, oc2);
	i.add_fileObject(coderun.getScript(), coderun.getCode_repo());
}
```

And here is an example of raising an issue directly with a component and a Script:

```Java

try (Coderun coderun = new Coderun(configPath, scriptPath, token)) {
    Data_product_read dp = coderun.get_dp_for_read("existing/dpname");
	Object_component_read oc1 = dp.getComponent("comp1");
	oc1.raise_issue("A serious issue", 10);
	coderun.getScript().raise_issue("Another pretty serious issue", 9);
}
```
