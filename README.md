# 深入理解Hadoop集群和网络

create 20170911



深入理解Hadoop集群和网络 http://os.51cto.com/art/201211/364374.htm

商业及政府都存在大量的数据需要被快速的分析和处理。把这些大块的数据切开，然后分给大量的计算机，让计算机并行的处理这些数据 — 这就是Hadoop能做的。


任务部署


Client机器  把数据加载到集群中，递交给Map Reduce数据处理工作的描述，并在工作结束后取回或者查看结果。
主节点 负责Hadoop两个关键功能模块HDFS、Map Reduce的监督 
从节点 负责了机器运行的绝大部分，担当所有数据储存和指令计算的苦差


名称节点只负责提供数据的位置和数据在族群中的去处（文件系统元数据）。

所以每块数据都会在集群上被重复的加载。Hadoop的默认设置是每块数据重复加载3次。


每个Map任务完成后，每个节点在其临时本地存储中存储其本地计算的结果。这被称作“中间数据”。下一步将通过网络传输发送此中间数据到Reduce任务最终计算节点上运行。


则必须有人知道数据节点的位置，并根据实际情况在集群中作出明智的位置分配。这个人就是名称节点
