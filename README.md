To reproduce the error you'll need a copy of the android sdk and some platform tools. See lein-droid instructions if stuck, but basically define {:android {:sdk-path "/opt/android-sdk/"}} either in your :user profile, or directly in the project.clj here.

Then run lein droid doall to see what the app should look like in debug mode - this works fine.

If you now do a release build (store pass "testtest" - you'll need to enter this twice for some reason, and then alias "testtest") then let it run, you should get the following error:

```
06-16 18:50:28.650 11421 11442 E AndroidRuntime: FATAL EXCEPTION: Thread-33480
06-16 18:50:28.650 11421 11442 E AndroidRuntime: java.lang.ExceptionInInitializerError
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at java.lang.Class.classForName(Native Method)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at java.lang.Class.forName(Class.java:217)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.RT.loadClassForName(RT.java:2140)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.RT.load(RT.java:455)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.RT.load(RT.java:436)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.core$load$fn__5066.invoke(core.clj:5640)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.core$load.doInvoke(core.clj:5640)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.RestFn.invoke(RestFn.java:408)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.core$load_one.invoke(core.clj:5446)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.core$load_lib$fn__5015.invoke(core.clj:5485)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.core$load_lib.doInvoke(core.clj:5485)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.RestFn.applyTo(RestFn.java:142)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.core$apply.invoke(core.clj:626)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.core$load_libs.doInvoke(core.clj:5524)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.RestFn.applyTo(RestFn.java:137)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.core$apply.invoke(core.clj:628)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.core$use.doInvoke(core.clj:5609)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.RestFn.invoke(RestFn.java:457)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at test.tuple.thing.main$loading__4958__auto__.invoke(main.clj:1)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at test.tuple.thing.main__init.load(Unknown Source)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at test.tuple.thing.main__init.<clinit>(Unknown Source)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at java.lang.Class.classForName(Native Method)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at java.lang.Class.forName(Class.java:217)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.RT.loadClassForName(RT.java:2140)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.RT.load(RT.java:455)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.RT.load(RT.java:436)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.core$load$fn__5066.invoke(core.clj:5640)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.core$load.doInvoke(core.clj:5640)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.RestFn.invoke(RestFn.java:408)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.Var.invoke(Var.java:379)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at test.tuple.thing.MainActivity.<clinit>(Unknown Source)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at java.lang.Class.classForName(Native Method)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at java.lang.Class.forName(Class.java:217)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at java.lang.Class.forName(Class.java:172)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at test.tuple.thing.SplashActivity$1.run(SplashActivity.java:65)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at java.lang.Thread.run(Thread.java:856)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: Caused by: java.lang.NullPointerException, compiling:(NO_SOURCE_PATH:0:0)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.Compiler.analyzeSeq(Compiler.java:6651)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.Compiler.analyze(Compiler.java:6445)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.Compiler.analyze(Compiler.java:6406)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.Compiler$BodyExpr$Parser.parse(Compiler.java:5782)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.Compiler$LetExpr$Parser.parse(Compiler.java:6100)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.Compiler.analyzeSeq(Compiler.java:6644)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.Compiler.analyze(Compiler.java:6445)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.Compiler.analyze(Compiler.java:6406)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.Compiler$BodyExpr$Parser.parse(Compiler.java:5782)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.Compiler$FnMethod.parse(Compiler.java:5217)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.Compiler$FnExpr.parse(Compiler.java:3846)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.Compiler.analyzeSeq(Compiler.java:6642)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.Compiler.analyze(Compiler.java:6445)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.Compiler.eval(Compiler.java:6700)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.Compiler.eval(Compiler.java:6666)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.core$eval.invoke(core.clj:2923)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clj_tuple$fn__792.invoke(clj_tuple.clj:362)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clj_tuple__init.load(Unknown Source)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clj_tuple__init.<clinit>(Unknown Source)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	... 36 more
06-16 18:50:28.650 11421 11442 E AndroidRuntime: Caused by: java.lang.NullPointerException
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at java.io.File.fixSlashes(File.java:185)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at java.io.File.<init>(File.java:134)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.DalvikDynamicClassLoader.defineMissingClass(DalvikDynamicClassLoader.java:84)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.DynamicClassLoader.defineClass(DynamicClassLoader.java:46)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.Compiler$NewInstanceExpr.compileStub(Compiler.java:7649)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.Compiler$NewInstanceExpr.build(Compiler.java:7514)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.Compiler$NewInstanceExpr$DeftypeParser.parse(Compiler.java:7425)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	at clojure.lang.Compiler.analyzeSeq(Compiler.java:6644)
06-16 18:50:28.650 11421 11442 E AndroidRuntime: 	... 54 more
```
