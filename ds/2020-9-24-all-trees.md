面试爱问数据结构各种树，看这一篇就够了

数据结构数据在计算机中的存储、组织方式，我们在学习计算机数据结构会遇到各种各样的基础结构，比如堆栈、队列、数组、链表、树等等，这些基本的数据结构类型有各自的特点，不同数据结构适用于解决不同场景下的问题，树形结构相比数组、链表、堆栈这些数据结构来说稍微复杂一点点，今天就带大家一起学习下数据结构中的各种「树」形结构，看完你会发现，也就那么回事。



## 从树说起

在进入下面的章节之前我们先来看「树」在数据结构中的概念。

我们熟悉的数组、链表、堆栈这些都是线性结构，那什么是线性结构呢？

**线性结构**是一个有序数据元素的集合。 其中数据元素之间的关系是一对一的关系，即除了第一个和最后一个数据元素之外，其它数据元素都是首尾相接的。常用的线性结构有：线性表，栈，队列，双队列，数组，串。

可以想象，所谓的线性结构数据组织形式，就像一条线段一样笔直，元素之间首尾相接。比如现实中的火车、排队。

![线性结构图]()

树是一种**非线性的数据结构**，即节点之间是一对多的关系，是一种层次化的数据组织形式。

它长得看起来就像是一颗树，不信你看：

![img](http://data.biancheng.net/uploads/allimg/170830/2-1FS0094003158.png)



### 几个关键概念

讲到树有几个概念要先科普下，方便对后续章节的理解：

节点的度：就是每个节点有几个分叉就说这个节点的度是多少。

根节点：树最顶层的那个节点。

叶子节点：节点的度为 0 也就是没有分叉的节点称为叶子节点，直观来看就是一颗树最底层的那些节点。

树的高度：节点到**叶子节点**的最长路径长度。树的高度是根节点到叶子节点的最长路径。

树的深度：节点的深度是从**根节点**到该节点的唯一路径长，根的深度为0，树的深度所有节点中的最大深度。



## 二叉树

有了前面「树」的基础铺垫，二叉树是一种特殊的树，还记的上面我们学过「节点的度」吗？即二叉树中每个节点的度不大于 2 ，即它的每个节点最多只有两个分支，通常称二叉树节点的左右两个分支为左右子树。

是不是很简单，二叉树是很多其他树型结构的基础结构，比如下面要讲的 AVL 树、二叉查找树都是由二叉树增加约束条件进化而来。

### 二叉树的遍历

遍历就是逐个访问二叉树节点，常见的二叉树遍历方式有三种，分别是前中后序遍历，初学者分不清这几个顺序的差别。

有个简单的记忆方式，这里的前中后都是对于根节点而言，先访问根节点后访问左右子树的遍历是前序遍历，先访问左右子树最后访问根节点的遍历是后序遍历，剩下的就是中序遍历，下面详细说明：

#### 前序遍历

遍历顺序是根节点->左子树->右子树

#### 中序遍历

遍历顺序是左子树->根节点->右子树

#### 后序遍历

遍历顺序是左子树->右子树->根节点



## 二叉查找树

由于最基础的二叉树节点是无序的，想象一下如果在二叉树中查找一个数据，最坏情况可能要要遍历整个二叉树，这样的查找效率是非常低下的。

正是由于基础二叉树不利于数据的查找和插入，因此我们有必要对二叉树中的数据进行排序，所以就有了「二叉查找树」可以说是为了查找而生的二叉树。

查找二叉树理解了也不难，简单来说就是二叉树上所有节点的左子树上的节点都小于根节点，右子树上所有节点的值都大于根节点。举个例子：

![图2]()

如果对排序二叉树执行中序遍历，因为中序遍历的顺序是左子树->根节点->右子树，最终可以得到一个节点值的有序列表。

二叉查找树的最坏效率是O(n)，实际应用中有很多改进版的二叉查找树，比如AVL树和红黑树，可以将最坏效率降低至O(log n)，下面我们就来看下这两种改进的二叉树。



## AVL树

AVL树



## 红黑树

### 应用场景

红黑树在实际应用中有很多已经落地的实践，比如学习C++的同学都知道会接触到 STL 标准库，而STL容器中的map、set、multiset、multimap 底层实现都是基于红黑树。 

再比如，Linux内核中也有红黑树的实现，Linux系统在实现EXT3文件系统、虚拟内存管理系统，都有使用到红黑树这种数据结构。Linux内核中的红黑树定义在内核文件如下的位置：

```c
头文件：linux-version/include/linux/rbtree.h 
源文件：linux-version/lib/rbtree.c
```



### 结构特点

红黑树其实是一种特殊的「二叉查找树」，每个结点都被标记了红黑属性，红黑树除了有普通的「二叉查找树」特性之外，还有以下的特征：

1. 节点是红色或黑色。
2.  根是黑色。
3. 所有叶子都是黑色（叶子是NIL节点）。
4. 每个红色节点必须有两个黑色的子节点。（从每个叶子到根的所有路径上不能有两个连续的红色节点。）
5. 从任一节点到其每个叶子的所有简单路径都包含相同数目的黑色节点。

以上的这些特点能够保证最坏情况下的查找、插入、删除操作的时间复杂度不超过O(log n)，并且有较高的插入和删除效率。

### 红黑树 VS 平衡二叉树（AVL树）

- 一般认为红黑树的插入和删除操作会比 AVL 树更快。红黑树不像 AVL 树那样严格的要求平衡因子小于等于1，这就减少了为了达到平衡而进行的旋转操作次数，可以说是牺牲严格平衡性来换取更快的插入和删除时间。
- 红黑树提出节点着色的原理来达到不严格的平衡性控制，任何不平衡都会在三次旋转之内解决。
- 查找操作AVL树的效率更高。因为 AVL 树设计比红黑树更加平衡，减少了树的平均搜索长度。





## Trie树（前缀树或字典树）



## B树



