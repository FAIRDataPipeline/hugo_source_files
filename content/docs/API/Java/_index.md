---
weight: 4
title: "Java"
bookCollapseSection: true
---

# javaDataPipeline

The javaDataPipeline Java library allows Java modellers to interface with the FAIR Data Pipeline.
It is available on Maven Central:

```gradle
dependencies {
    implementation 'org.fairdatapipeline:api:1.0.0-beta'
}
```

The main purpose of interfacing with the FAIR Data Pipeline is the recording of Coderuns: a Coderun is a recorded session of your modelling code, all the inputs used and outputs generated will be recorded and a [Provenance Report][prov] will be generated.

The basic idea behind the FAIR DataPipeline and Coderuns is explained on the [Data pipeline](/docs/interface/) page.








## Usage

A useful starting point to get to know the javaDataPipeline is to explore the [java Simple Model](https://github.com/FAIRDataPipeline/javaSimpleModel). This shows example [config.yaml](https://www.fairdatapipeline.org/docs/interface/config/) files, example
`main(String[] args)` code that allows `fair run` to call your code, and example `Coderun()` code for reading/writing input/output Data Products.


The links below give a basic introduction to the javaDataPipeline; these should be read in conjunction with the [javaDocs][docs] which give more precise specification of the java API.

[Basic Coderun](coderun)  
[Issues](issues)   
[Parameters](parameters)  
[HDF5](hdf5)   
[Run](run)  
[Debug](debug)  

See the [package documentation][docs] for Javadoc.


## License/copyright

Copyright (c) 2021: Bram Boskamp, Biomathematics and Statistics Scotland and the Scottish COVID-19 Response Consortium

GNU GENERAL PUBLIC LICENSE Version 3


## Source code

See the package's [code repo][repo].

[docs]: https://www.fairdatapipeline.org/javaDataPipeline
[repo]: https://github.com/FAIRDataPipeline/javaDataPipeline
[prov]: /docs/data_registry/prov_report/
