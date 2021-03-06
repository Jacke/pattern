# Overview

[Pattern](http://www.cascading.org/pattern/) is a Cascading framework and library for machine learning model
scoring at scale.

Pattern can read [PMML](http://en.wikipedia.org/wiki/Predictive_Model_Markup_Language) models as workflow
specifications for generating Cascading flows which can run on Apache Hadoop.

Pattern is still under active development under the wip-1.0 branch. Thus all wip releases are made available
from the `files.concurrentinc.com` domain. When Pattern hits 1.0 and beyond, final releases will be under
`files.cascading.org`.

See the `pattern-examples` subdirectory for sample apps.

For more information, visit: http://www.cascading.org/pattern/

# PMML

Pattern currently supports the following PMML model types:

  * General Regression
  * Regression
  * Clustering
  * Tree
  * Mining - ensembles of the above models like Random Forest

In progress are:

  * Neural Network
  * Support Vector Machine

Not all aspects of each of the above models are supported. To request support for a particular model or model
parameter, [report an issue](#reporting-issues).

These PMML model types translate or compose into:

  * [Random Forest](http://en.wikipedia.org/wiki/Random_forest) in [PMML 4.0+](http://www.dmg.org/v4-0-1/MultipleModels.html) exported from [R/Rattle](http://cran.r-project.org/web/packages/rattle/index.html)
  * [Linear Regression](http://en.wikipedia.org/wiki/Linear_regression) in [PMML 1.1+](http://www.dmg.org/v1-1/generalregression.html)
  * [K-Means Clustering](http://en.wikipedia.org/wiki/K-means_clustering) in [PMML 2.0+](http://www.dmg.org/v2-0/ClusteringModel.html)
  * [Logistic Regression](http://en.wikipedia.org/wiki/Logistic_regression) in [PMML 4.0.1+](http://www.dmg.org/v4-0-1/Regression.html)
  * [Multinomial Model](http://en.wikipedia.org/wiki/Multinomial_distribution) in [PMML 2.0+](http://www.dmg.org/v2-0/Regression.html)

Note: [Hierarchical Clustering](http://en.wikipedia.org/wiki/Hierarchical_clustering) is also implemented. The unit test
for that algorithm currently excludes two data points. In regression tests with the Iris data set, we've
isolated edge cases where the classifiers in R and Pattern do not agree. Then again, Iris data gets used to illustrate model behaviors
with such properties. This will take some digging into numerical operations inside R.

# Using

To use Pattern, there is no installation other than adding the necessary dependencies to Maven, Ivy, or Gradle.

To include the base core model libraries, use:

    <dependency>
      <groupId>cascading</groupId>
      <artifactId>pattern-core</artifactId>
      <version>x.y.z</version>
    </dependency>

To include the PMML parsing libraries and the `PMMLPlanner`, use:

    <dependency>
      <groupId>cascading</groupId>
      <artifactId>pattern-pmml</artifactId>
      <version>x.y.z</version>
    </dependency>

Other sub-projects and artifacts are simply in place to faciliate testing on various platforms, the above dependencies
have no dependencies on Cascading Hadoop or local modes, they are completely independent of the underying platforms.

# Reporting Issues

The best way to report an issue is to add a new test to `SimplePMMLPlatformTest` along with the expected result set
and submit a pull request on GitHub.

Failing that, feel free to open an [issue](https://github.com/Cascading/pattern/issues) on the [Cascading/Pattern](https://github.com/Cascading/pattern)
project site or mail the [mailing list](https://groups.google.com/forum/?fromgroups#!forum/pattern-user).

# Developing

Running:

    > gradle idea

from the root of the project will create all IntelliJ project and module files, and retrieve all dependencies.
