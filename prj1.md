project1-1 LRU REPLACEMENT POLICY
实现lru replacer

- pin表示线程要使用了，所以不能被回收，所以从replacer中移出
- unpin表示最近使用完，加入队列
- 有新的要加入，或者扫描触发，Victim移出最旧的，

project1-2 BufferPoll
- 调度page的使用
- Page Object (容器，装从硬盘加载出的数据)
    - page_id 代表哪一个物理page 
    - 无指向 INVALID_PAGE_ID
    - pin了这个page的thread的计数（pin了就不能free）
    - 是否dirty
- freelist为回收的，未初始化的page
- pagetable为已经与物理page的绑定关系
- replacer负责处理未被使用的（pin引用数为0）frame销毁工作（其中数据依然有效，指向某个page），每次freelist page不够时就从replacer取出，replacer取出来的需要从pagetable解绑，并且如果是dirty需要保存

project1-3 Parrallel
- 单个mananger会导致多个访问时，过度竞争锁，所以把page的管理分散到多个manager里，每次新申请page，都从新的manager偏移开始尝试申请page，以分散page在managers中的分布