## 性能测试
- 测试数据：搜集APP中的SharePreferences汇总的部份key-value数据（经过随机混淆）得到总共六百多个key-value。<br>
  分别截取其中一部分，构造正态分布的输入序列，进行多次测试。
- 测试代码：[Benchmark](https://github.com/BillyWei01/FastKV/blob/main/app/src/main/java/io/fastkv/fastkvdemo/Benchmark.kt)
- 版本：MMKV 2.0.2 466KB| FastKV 2.6.0 73KB| DataStore 1.1.1 1.2MB|
- 测试结果：

|对比项目|25 - Write（ms）|25 - Read（ms）|50 - Write（ms）|50 - Read（ms）|100 - Write（ms）|100 - Read（ms）|200 - Write（ms）|200 - Read（ms）|400 - Write（ms）|400 - Read（ms）|600 - Write（ms）|600 - Read（ms）|
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|Sp-commit|955|5|1994|4|4301|10|8772|3|22922|1|33072|6|
|Sp-apply|20|2|23|4|133|3|294|3|739|1|874|6|
|DataStore|1799|684|4113|1019|10910|627|30840|934|59710|3716|120811|2614|
|SQLite|131|72|147|241|388|336|753|592|1262|615|3146|1036|
|MMKV|21|5|18|10|38|10|77|22|40|6|63|7|
|FastKV|15|5|17|11|33|16|40|23|48|18|112|60|
