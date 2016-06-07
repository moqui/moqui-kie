# Moqui KIE Tool Component

[![license](http://img.shields.io/badge/license-CC0%201.0%20Universal-blue.svg)](https://github.com/moqui/moqui-kie/blob/master/LICENSE.md)
[![release](http://img.shields.io/github/release/moqui/moqui-kie.svg)](https://github.com/moqui/moqui-kie/releases)

Moqui tool component for KIE tools including Drools, jBPM, etc.

To install run (with moqui-framework):

    $ ./gradlew getComponent -Pcomponent=moqui-kie

This will add the component to the Moqui runtime/component directory. 

The KIE, Drools, and dependent JAR files are added to the lib directory when the build is run for this component, which is
designed to be done from the Moqui build (ie from the moqui root directory) along with all other component builds. 

To use just install this component. The configuration for the ToolFactory is already in place in the 
MoquiConf.xml included in this component and will be merged with the main configuration at runtime. 

To use KIE through the ToolFactory do something like this example from the Mantle USL PriceServices.get#ProductPrice service:

    if (ec.factory.getToolFactory("KIE") != null)
        ec.getTool("KIE", KieToolFactory.class).getStatelessKieSession("ProductPriceKS").execute([])

See also the mantle-usl/kie directory for configuration of a rules module and some actual rules and a decision table spreadsheet.
