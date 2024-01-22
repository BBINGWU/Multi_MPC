# Multi_MPC
## 文件说明
修改的内容为rand.py，acss.py，admpc.py，在这三个文件里，分别有拆开的Rand_Foll, Rand_Pre, ACSS_Pre, ACSS_Foll，控制整个过程的ADMPC_Multi_Layer_Control，和继承了ADMPC的ADMPC_Dynamic。
测试文件为test_multi_mpc.py

## 目前存在的问题：
不设置任何断点，会有直接卡住的现象。
目前设置的方法是在每个作为dealer 的ADMPC_Dynamic Node中增加一个self.Signal，这个在ADMPC_Dynamic初始化的时候就初始化了这个信号。接着在上一层进行optqrbc的任务设置后会set这个信号。在下一层设置了optqrbc的任务的时候会await这个信号

