# Object-to-object mapping framework microbenchmark #

Multi-layered applications often require to map between different object models (e.g. DTOs and entities). 
Writing such boiler plate mapping code is a tedious and error-prone task.
A lot of object-to-object mapping Java frameworks aims to simplify this work and automate it.
Some uses code instrospection (eg. Dozer). Other uses code generation (ex: MapStuct).
This micro-benchmark compares performance of 5 frameworks. Results could be compared to the benchmark of a code written manually. 

Benchmark are powered by a tool called [JMH](http://openjdk.java.net/projects/code-tools/jmh/) or also known as "Java Microbenchmarking Harness".
JMH is developed by the OpenJDK team. 

## Benchmarked object to object mapper frameworks ##

- [Dozer](https://github.com/DozerMapper/dozer)
- [MapStruct](http://mapstruct.org/)
- [ModelMapper](http://modelmapper.org/)
- [Selma](http://www.selma-java.org/)
- [Orika](https://github.com/orika-mapper/orika)

## Contributing to benchmark ##


Github is for social coding platform: if you want to add another mapping framework or optimize an existing one, we encourage contributions through pull requests from [forks of this repository](http://help.github.com/forking/). If you want to contribute code this way, please reference a GitHub ticket as well covering the specific issue you are addressing.


## Data model ##

The data model used by this benchmark is very basic. It comes from the [Comparison](https://github.com/jhalterman/modelmapper/blob/master/core/src/test/java/org/modelmapper/performance/Comparison.java) class from the ModelMapper framework.
It includes combinations which usually appear in Java Beans, such as:

* Object types
* Collections

![Data model UML diagram](/model.png)

## Launch the benchmark ##

_Pre-requisites: Maven 3.x and a JDK 6 (or above)_

``git clone git://github.com/arey/java-object-mapper-benchmark.git``

``mvn clean install``

``java -jar target/benchmarks.jar``

## Results ##

Tests has been performed on:

* OS: MacOSX
* CPU: Core i7 2.8GHz 6MB cache × 4 cores
* RAM: 16GB
* JVM: Oracle 1.8.0_25 64 bits

<table>
    <tr>
        <th>Benchmark</th><th>Mode</th><th>Samples</th><th>Score</th><th>Margin error (+/-)</th><th>Units</th>
    </tr>
    <tr>
        <th>Manual</th><td>thrpt</td><td>200</td><td>17 277 097</td><td>146 095</td><td>ops/s</td>
    </tr>
    <tr>
        <th>Selma</th><td>thrpt</td><td>200</td><td>17 132 979</td><td>38 209</td><td>ops/s</td>
    </tr>
    <tr>        
        <th>MapStruct</th><td>thrpt</td><td>200</td><td>14 493 144</td><td>67 522</td><td>ops/s</td>
    </tr>
    <tr>
        <th>Orika</th><td>thrpt</td><td>200</td><td>3 283 557</td><td>16 706</td><td>ops/s</td>
    </tr>
    <tr>       
        <th>ModelMaper</th><td>thrpt</td><td>200</td><td>282 039</td><td>2 176</td><td>ops/s</td>
    </tr>
    <tr>
        <th>Dozer</th><td>thrpt</td><td>200</td><td>103 006</td><td>1 362</td><td>ops/s</td>
    </tr>
</table>

Legend : Higher score is better

Total time: 00:49:06

## Documentation ##

* [Micro-benchmark of Java mapping object frameworks](http://javaetmoi.com/2015/09/benchmark-frameworks-java-mapping-objet/) (french article)


## Credits ##

* Uses [Maven](http://maven.apache.org/) as a build tool
* Uses [JMH](http://openjdk.java.net/projects/code-tools/jmh/) for Java Microbenchmarking Harness