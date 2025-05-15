# This project demonstrates an issue with nbm:cluster

After switching to nbm-maven-plugin >=4.6, the project no longer builds the cluster correctly.
This project has three branches, each with a different version of nbm-maven-plugin.

- *main* with **nbm-maven-plugin 4.5** ✅ working
- *4.6* with **nbm-maven-plugin 4.6** ❌ fails
- *14.3* with **nbm-maven-plugin 14.3** ❌ fails

The project uses JDK 11 and maven 3.9.9 was used.

When running `mvn -X clean package install` the output shows that files are copied from the kit cluster for each of the
modules.

`[DEBUG] FileSet: Setup scanner in dir C:\Users\marco\IdeaProjects\cluster-example\module-kit\target\nbm\clusters with patternSet{ includes: [**] excludes: [] }
[INFO] Copying 3 files to C:\Users\marco\IdeaProjects\cluster-example\module-kit\target\netbeans_clusters`

This is repeated four times for the same source directory with versions >4.6. For each module one execution is performed, including the parent. With
version 4.5 it is executed 3 times only and only for the modules, module-kit, module-a and module-b. 