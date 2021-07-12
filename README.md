Purpose
===
This is the minimal project to reproduce the problems described in 

https://github.com/renovatebot/renovate/issues/5667

What goes wrong?
===
Sometimes a project introduces a newer version with only a pom.xml that states the next version of the project has a different name (group and/or artifact have changes).

I would like renovate to also update the group and artifact to smoothly transition to the new version IF they used the official maven solution as documented by maven. 

https://maven.apache.org/guides/mini/guide-relocation.html

This demonstration uses a few dependencies that use this construct and are not updated by renovate yet. 

The git-commit-id-plugin has this in the transition from version 4.x to 5.x:

https://search.maven.org/artifact/pl.project13.maven/git-commit-id-plugin/4.9.9/pom

    <distributionManagement>
      <relocation>
        <groupId>io.github.git-commit-id</groupId>
        <artifactId>git-commit-id-maven-plugin</artifactId>
      </relocation>
    </distributionManagement>
