# hadoop-mahout-recosys
A recommender system built on hadoop and mahout

## References:
- `mahout in action`
- [基于hadoop下的mahout推荐系统实现](http://blog.csdn.net/sun_wangdong/article/details/59483790)

## Notes:
1. Build and Generate .jar  

File | Project Structure | Artifacts then you should press alt+insert or click the plus icon and create new artifact choose --> jar --> From modules with dependencies.
Next goto Build | Build artifacts --> choose your artifact.

2. Move input data to hdfs
```shell
hdfs dfs -put mywiki.txt /user/a/data
```
3. Run hadoop
```shell
hadoop jar ../out/artifacts/wiki_jar/wiki.jar com.szywind.wiki.wikiDriver /user/a/data/mywiki.txt /user/a/wiki_output
```
Note that
Exception may occur:
```
Exception in thread "main" java.io.IOException: Mkdirs failed to create /var/folders/2p/3955pwwd153cn8x2b5sn11r00000gp/T/hadoop-unjar9040728181254931342/META-INF/license
	at org.apache.hadoop.util.RunJar.ensureDirectory(RunJar.java:128)
	at org.apache.hadoop.util.RunJar.unJar(RunJar.java:104)
	at org.apache.hadoop.util.RunJar.unJar(RunJar.java:81)
	at org.apache.hadoop.util.RunJar.run(RunJar.java:209)
	at org.apache.hadoop.util.RunJar.main(RunJar.java:136)
```
To fix this, just remove META-INF/LICENSE in the .jar package as follows:
```shell
zip -d ../out/artifacts/wiki_jar/wiki.jar META-INF/LICENSE
```
