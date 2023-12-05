# mpmd386
Reproducer for Maven PMD Plugin Issue MPMD-386

# Basic Setup
* Install build tools via `mvn install`
* Install META-POM via `mvn install`

Keep the following property in mind which is used to set up the path to supresssfiles of pmd (and 

> <path.to.suppressfile.wo.slash>${project.basedir}/..</path.to.suppressfile.wo.slash>

The single module projects overwrite this, elemenating the "/.." as there are no modules.

Note: We also use spotsbugs-plugin (currectly 4.7.3.5, not shown here) which works fine with this setup since it was even findbugs plugin. The checkstyle plugin (as listed in ticket) never needed such a property, regardless of single-module or multi-module project.


# PMD 3.14.0
Run the four projects from their "root" folder (see file "execute_maven_here") with `mvn clean verify site -f pom` or `mvn clean verify site -f subfolder/pom` (depending if its a root or subfolder project) to use the file argument.
You will see that all projects build correctly and generate site report.


# PMD 3.14.0
Run the four projects from their "root" folder (see file "execute_maven_here") with `mvn clean verify site -f pom` or `mvn clean verify site -f subfolder/pom` (depending if its a root or subfolder project) to use the file argument.
You will see that the multi module projects will fail as the "exclude-pmd.properties" is now searched from root folder and not anymore from module folder as it was before with version 3.14 and therefore the plugin looks in the folder "in front of" the projects root folder, while the single module build it




