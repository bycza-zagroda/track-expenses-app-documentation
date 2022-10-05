# Javadoc
[Javadoc coding standard](https://blog.joda.org/2012/11/javadoc-coding-standards.html)

## annotations @since and @version
[@version - oracle.com](https://www.oracle.com/technical-resources/articles/java/javadoc-tool.html#@version)  
The Java Software convention for the argument to the @version tag is the SCCS string "%I%, %G%", which converts to something like " 1.39, 02/28/97" (mm/dd/yy) when the file is checked out of SCCS.



## @author
Avoid @author

The @author feature can be used to record the authors of the class. This should be avoided, as it is usually out of date, and it can promote code ownership by an individual. The source control system is in a much better position to record authors. 
