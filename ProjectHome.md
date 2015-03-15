T3 is a powerful automated unit testing tool to test Java classes. Given a target class to test, it randomly generates sequences of calls to the class' methods to test it. It catches unexpected exception; but if you had written assertions in the class, then violations to those will be caught as well.

Note: the predecessor of T2 is phased out.

T3's main features:

  * Sequence-based testing: it does not test a method individually, but instead generate sequences of method calls to trigger interactions between methods of the target class.
  * Fast, able to generate thousands of test sequences in few seconds.
  * Generated test suite can be saved and replayed.
  * A combinator-based approach to compose custom value/object generators, ala QuickCheck.
  * It can be run from the command line, or called as an API from a JUnit test class.


I also provide a Groovy 'front-end' called T3i, that facilitates more powerful use of T3.
T3i offers these additional features:

  * We can do interactive testing through Groovy interactive shell.
  * Provide a convenient way to configure T3, including specifying custom value/object generators.
  * We can experiment with different configurations to generate multiple suites; combine them, filter them, and combine them again.
  * We can query generated test suites for Hoare triples, LTL formulas, or algebraic formulas.

T3 needs Java 8, and T3i also needs Groovy at least 2.3.

**License**: GPL version 3.

<a href='Hidden comment: 
[http://www.cs.uu.nl/wiki/pub/WP/TTwoScreenShots/screenshot1.png Screenshot], T2 in combination with Junit and IDE.

Read more in [http://www.cs.uu.nl/wiki/WP/T2Framework T2 home page].
'></a>


**Binary download** (ignore the download tab on the left:)  : [here](https://bitbucket.org/uprime815/t3/downloads)


**Manuals**:

  * [T3-manual](http://uprime815.bitbucket.org/t3/docs/manual.html)
  * [T3i-readme](http://uprime815.bitbucket.org/t3i/README.TXT)
  * [T3i-manual](http://uprime815.bitbucket.org/t3i/docs/manual.html)

**Source** is hosted at Bitbucket :)

  * https://uprime815@bitbucket.org/uprime815/t3.git
  * The older t2: https://uprime815@bitbucket.org/uprime815/t2.git



**Contact**: [Wishnu Prasetya](http://www.cs.uu.nl/~wishnu), owner and developer.

### If you want to cite ###

For now, cite this T2 paper. I will upload T3 paper soon.

  * _[Trace-based Reflexive Testing of OO Programs with T2](http://doi.ieeecomputersociety.org/10.1109/ICST.2008.12)_, I.S.W.B. Prasetya, T.E.J. Vos, A.I. Baars, in the proceeding of IEEE International Conference on Software Testing Verification and Validation (ICST), 2008.

### Other Papers ###

  * _[Smart Regression Testing with the T2 Testing Framework](http://www.cs.uu.nl/docs/vakken/mcosc/2011/JeielSchalkwijk.pdf)_, J. Schalkwijk. Master thesis, ICA-0216070. Dept. of Inf. and Comp. Sciences, Utrecht Univ. 2011.

  * _[Strategies for Directed Generation of Test Sequences](http://www.cs.uu.nl/docs/vakken/mcosc/2011/ChristiaanHees.pdf)_, C. Hees.  Master thesis, ICA-0122106. Dept. of Inf. and Comp. Sciences, Utrecht Univ. 2011.

  * _[THEMIS: Framework for Automated Testing of Graphical User Interfaces](http://www.cs.uu.nl/wiki/pub/WP/T2Framework/SCR-2007-105.pdf)_, M. Stobbe. Master thesis, INF/SCR-2007-105. Dept. of Inf. and Comp. Sciences, Utrecht Univ. 2008.

  * _[Extending T2 with Prime Path Coverage Exploration](http://www.cs.uu.nl/wiki/pub/WP/T2Framework/SCR-2008-014.pdf)_, M. Gerritsen. Master thesis, INF/SCR-2008-014. Dept. of Inf. and Comp. Sciences, Utrecht Univ. 2008.

  * _[Automated Testing for Java-Based Programs with Java PathFinder and T2 Framework](http://www.cs.uu.nl/wiki/pub/WP/T2Framework/Paper6halaman.pdf)_, A.Y Prasetyo, R. Suryadharma, A. Azurat, B.H. Widjaja, in the Asia Pacific Conf. on Art, Science, Engineering & Technology (ASPAC) 2008, Solo, Indonesia.

  * _[Patterns for In-code Algebraic Testing](http://www.cs.uu.nl/research/techreps/repo/CS-2008/2008-037.pdf)_, I.S.W.B. Prasetya, T.E.J. Vos. Tech. Rep UU-CS-2008-037.


