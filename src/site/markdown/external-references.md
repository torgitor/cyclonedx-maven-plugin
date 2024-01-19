External References
===================

Components described in SBOMs generated by the CycloneDX Maven Plugin contain a few fields and external
references that are extracted from [Maven effective POMs][maven-model]:

- of the current built `pom.xml` (with inheritance) for SBOM [`metadata.component`][metadata-component] = the component that the BOM describes,
- of the Maven dependencies for SBOM [`components`][components].

## SBOM Fields extracted from POM

3 SBOM fields are deducted from effective POM (= after POM inheritance from parents):

- `component.publisher` is filled with POM's `project.organisation.name`,
- `component.description` is filled with POM's `project.description`,
- `component.licenses[]` is filled with POM's `project.licenses[]`.

## External References extracted from POM

| [POM field][maven-model]                        | [External Reference type][external-reference-type]
|-------------------------------------------------|--------------
| `project.url`                                   | `website`
| `project.scm.url`                               | `vcs`
| `project.ciManagement.url`                      | `build-system`
| `project.issueManagement.url`                   | `issue-tracker`
| `project.mailingLists[].archive` or `subscribe` | `mailing-list`
| `project.distributionManagement.repository.url` | `distribution`


## Additional External References for `metadata.component`

You can add more external references the component that the BOM describes by plugin configuration:

```
<plugin>
  <groupId>org.cyclonedx</groupId>
  <artifactId>cyclonedx-maven-plugin</artifactId>
  <configuration>
    <externalReferences>
      <externalReference>
        <type>EXTERNAL_REFERENCE_TYPE</type><-- for "external-reference-type"-->
        <url>... value ...</url>
        <comment>(optional) comment</comment>
      </externalReference>
    </externalReferences>
  </configuration>
</plugin>
```

Notice that the type value in the plugin configuration refers to a [CycloneDX Core (Java) library constant name][external-reference-type-constants]
corresponding to [CycloneDX type][external-reference-type].

[maven-model]: https://maven.apache.org/ref/current/maven-model/maven.html
[metadata-component]: https://cyclonedx.org/docs/1.5/json/#metadata_component
[components]: https://cyclonedx.org/docs/1.5/json/#components
[external-reference-type]: https://cyclonedx.org/docs/1.5/json/#metadata_component_externalReferences_items_type
[external-reference-type-constants]: https://cyclonedx.github.io/cyclonedx-core-java/org/cyclonedx/model/ExternalReference.Type.html