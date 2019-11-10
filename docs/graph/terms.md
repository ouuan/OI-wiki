## 图

**图** 是一个二元组 $(V, E)$，其中 $V$ 和 $E$ 为集合 (多重集)。图常用 $G$, $H$ 等表示，如：$G = (V, E)$。

图分为 **无向图 (Undirected graph)** 和 **有向图 (Directed graph)** 两种，若 $G$ 为无向图，则 $E$ 中的每个元素为一个无序二元组 $(u, v)$，称作 **无向边 (Undirected edge)**，简称 **边 (Edge)**，其中 $u, v \in V$。设 $e = (u, v)$，则 $u$ 和 $v$ 称为 $e$ 的 **端点 (Endpoint)**。

若 $G$ 为有向图，则 $E$ 中的每一个元素为一个有序二元组 $(u, v)$，有时也写作 $u \to v$，称作 **有向边 (Directed edge)** 或 **弧 (Arc)** ，在不引起混淆的情况下也可以称作 **边 (Edge)** 。设 $e = u \to v$，则此时 $u$ 称为 $e$ 的 **起点 (Tail)** ，$v$ 称为 $e$ 的 **终点 (Head)** ，起点和终点也称为 $e$ 的 **端点 (Endpoint)**。

???+note "为什么起点是 Tail，终点是 Head？"
    边通常用箭头表示，而箭头是从“尾”指向“头”的。

对于 $V$ 中的每个元素，我们称其为 **顶点 (Vertex)** 或 **节点 (Node)**，简称 **点**，顶点的集合称为 **点集 (Vertex set)**，边的集合称为 **边集 (Edge set)**。

图 $G$ 的点集和边集可以表示为 $V(G)$ 和 $E(G)$，在不引起混淆的情况下，也能表示成 $V$ 和 $E$。图 $G$ 的点数 $\left| V(G) \right|$ 也被称作图 $G$ 的 **阶 (Order)**。

形象地说，图是由若干点以及连接点与点的边构成的。

## 简单图

**简单图 (Simple graph)**：若一个图中没有自环和重边，它被称为简单图。

**自环 (Loop)**：对 $E$ 中的边 $e = (u, v)$，若 $u = v$，则 $e$ 被称作一个自环。

**重边 (Multiple edge)**：若 $E$ 中存在两个完全相同的元素 (边) $e_1, e_2$，则它们被称作 (一组) 重边。

如果一张图中有自环或重边，则称它为 **重图 (Multigraph)**。

!!! warning
    在无向图中 $(u, v)$ 和 $(v, u)$ 算一组重边，而在有向图中，$u \to v$ 和 $v \to u$ 不为重边。

!!! warning
    在题目中，如果没有特殊说明，是可以存在自环和重边的，在做题时需特殊考虑。

## 邻域

在无向图 $G = (V, E)$ 中，若点 $v$ 是边 $e$ 的一个端点，则称 $v, e$ 是 **关联的 (Incident)** 或 **相邻的 (Adjacent)** 。对于两顶点 $u, v$，若存在边 $(u, v)$，则称 $u, v$ 是 **相邻的 (Adjacent)** 。

一个顶点 $v \in V$ 的 **邻域 (Neighborhood)** 是所有与之相邻的顶点所构成的集合，记作 $N(v)$ 。

一个点集 $S$ 的邻域是所有与 $S$ 中至少一个点相邻的点所构成的集合，记作 $N(S)$，即：

$$
N(S) = \bigcup_{v \in S} N(v)
$$

## 度数

与一个顶点 $v$ 关联的边的条数称作该顶点的 **度 (Degree)** ，记作 $d(v)$。特别地，对于边 $(v, v)$，则每条这样的边要对 $d(v)$ 产生 $2$ 的贡献。

对于无向简单图，有 $d(v) = \left| N(v) \right|$。

握手定理：对于任何无向图 $G = (V, E)$，有 $ \sum_{v \in V} d(v) = 2 \left| E \right|$ 。

若 $d(v) = 0$，则称 $v$ 为 **孤立点 (Isolated vertex)** 。

若 $d(v) = 1$，则称 $v$ 为 **叶节点 (Leaf vertex)** / **悬挂点 (Pendant vertex)** 。

若 $2 \mid d(v)$，则称 $v$ 为 **偶点 (Even vertex)** 。

若 $2 \nmid d(v)$，则称 $v$ 为 **奇点 (Odd vertex)** 。图中奇点的个数是偶数。

若 $d(v) = \left| V \right| - 1$，则称 $v$ 为 **支配点 (Universal vertex)** 。

对一张图，所有节点的度数的最小值称为 $G$ 的 **最小度 (Minimum degree)** ，记作 $\delta (G)$；最大值称为 **最大度 (Maximum degree)** ，记作 $\Delta (G)$。即：$\delta (G) = \min_{v \in G} d(v)$, $\Delta (G) = \max_{v \in G} d(v)$。

在有向图 $G = (V, E)$ 中，以一个顶点 $v$ 为起点的边的条数称为该顶点的 **出度 (Out-degree)** ，记作 $d^+(v)$。以一个顶点 $v$ 为终点的边的条数称为该节点的 **入度 (In-degree)** ，记作 $d^-(v)$。

对于任何有向图 $G = (V, E)$，有：

$$
\sum_{v \in V} d^+(v) = \sum_{v \in V} d^-(v) = \left| E \right|
$$

若对一张无向图 $G = (V, E)$，每个顶点的度数都是一个固定的常数 $k$，则称 $G$ 为 **$k$-正则图 ($k$-Regular Graph)** 。

## 路径

**途径 (Walk)** / **链 (Chain)**：一个点和边的交错序列，其中首尾是点——$v_0, e_1, v_1, e_2, v_2, \ldots, e_k, v_k$，有时简写为 $v_0 \to v_1 \to v_2 \to \cdots \to v_k$。其中 $e_i$ 的两个端点分别为 $v_{i-1}$ 和 $v_i$ 。通常来说，边的数量 $k$ 被称作这条途径的 **长度** （如果边是带权的，长度通常指路径上的边权之和，题目中也可能另有定义）。(以下设 $w = \left[ v_0, e_1, v_1, e_2, v_2, \cdots, e_k, v_k \right]$ 。)

**迹 (Trail)**：对于一条途径 $w$，若 $e_1, e_2, \cdots, e_k$ 两两互不相同，则称 $w$ 是一条迹。

**路径 (Path)** (又称 **简单路径 (Simple path)** )：对于一条迹 $w$，除了 $v_0$ 和 $v_k$ 允许相同外，其余点两两互不相同，则称 $w$ 是一条路径。

**回路 (Circuit)**：对于一个迹 $w$，若 $v_0 = v_k$，则称 $w$ 是一个回路。

**环/圈 (Cycle)** (又称 **简单回路/简单环 (Simple circuit)** )：对于一条简单路径 $w$，若 $v_0 = v_k$，则称 $w$ 是一个环。

!!! warning
    关于路径的定义在不同地方可能有所不同，如，“路径”可能指本文中的“途径”，“环”可能指本文中的“回路”。如果在题目中看到类似的词汇，且没有“简单路径”/“非简单路径”（即本文中的“途径”）等特殊说明，最好询问一下具体指什么。

## 子图

对一张图 $G = (V, E)$，若存在另一张图 $H = (V', E')$ 满足 $V' \subseteq V$ 且 $E' \subseteq E$，则称 $H$ 是 $G$ 的 **子图 (Subgraph)** ，记作 $H \subseteq G$。

若对 $H \subseteq G$，满足对 $\forall u, v \in V'$，只要 $(u, v) \in E$，均有 $(u, v) \in E'$，则称 $H$ 是 $G$ 的 **导出子图/诱导子图 (Induced subgraph)** 。

容易发现，一个图的导出子图仅由子图的点集决定，因此点集为 $V'$ ($V' \subseteq V$) 的导出子图称为 $V'$ 导出的子图，记作 $G \left[ V' \right]$。

若 $H \subseteq G$ 满足 $V' = V$，则称 $H$ 为 $G$ 的 **生成子图/支撑子图 (Spanning subgraph)**。

如果一张无向图 $G$ 的某个生成子图 $F$ 为 $k$-正则图，则称 $F$ 为 $G$ 的一个 **$k$-因子 ($k$-Factor)** 。

如果有向图 $G = (u, v)$ 的导出子图 $H = G \left[ V^* \right]$ 满足 $\forall v \in V^*, (v, u) \in E$，就有 $u \in V^*$，则称 $H$ 为 $G$ 的一个 **闭合子图 (Closed subgraph)** 。

## 连通

### 无向图

对于一张无向图 $G = (V, E)$，对于 $u, v \in V$，若存在一条途径使得 $v_0 = u, v_k = v$，则称 $u, v$ 是 **连通的 (Connected)**。由定义，任意一个顶点和自身连通，任意一条边的两个端点连通。

若无向图 $G = (V, E)$，满足其中任意两个顶点均连通，则称 $G$ 是 **连通图 (Connected graph)** ，$G$ 的这一性质称作 **连通性 (Connectivity)** 。

若 $H$ 是 $G$ 的一个连通子图，且不存在 $F$ 满足 $H\subsetneq F \subseteq G$ 且 $F$ 为连通图，则 $H$ 是 $G$ 的一个 **连通块/连通分量 (Connected component)** （极大连通子图）。

### 有向图

对于一张有向图 $G = (V, E)$，对于 $u, v \in V$，若存在一条途径使得 $v_0 = u, v_k = v$，则称 $u$ **可达** $v$。由定义，任意一个顶点可达自身，任意一条边的起点可达终点。（无向图中的连通也可以视作双向可达。）

若一张有向图的节点两两互相可达，则称这张图是 **强连通的 (Strongly connected)** 。

若一张有向图的边替换为无向边后可以得到一张连通图，则称原来这张有向图是 **弱连通的 (Weakly connected)** 。

与连通分量类似，也有 **弱连通分量 (Weakly connected component)** （极大弱连通子图） 和 **强连通分量 (Strongly Connected component)** （极大强连通子图）。

### 割

在本部分中，有向图的“连通”一般指“强连通”。

对于连通图 $G = (V, E)$ ，若 $V'\subseteq V$ 且 $G\left[V\\V'\right]$ （即从 $G$ 中删去 $V'$ 中的点）不是连通图，则 $V'$ 是图 $G$ 的一个 **点割集 (Vertex cut / Separating set)** 。大小为一的点割集又被称作 **割点 (Cut vertex)** 。

对于连通图 $G = (V, E)$ 和整数 $k$ ，若 $|V|\ge k+1$ 且 $G$ 不存在大小为 $k-1$ 的点割集，则称图 $G$ 是 **$k$-点连通的 ($k$-vertex-connected)** ，而使得上式成立的最大的 $k$ 被称作图 $G$ 的 **点连通度 (Vertex connectivity)** ，记作 $\kappa(G)$ 。（对于非完全图，点联通度即为最小点割集的大小，而完全图 $K_n$ 的点连通度为 $n-1$ 。）

对于图 $G = (V, E)$ 以及 $u, v\in V$ 满足 $u\ne v$ ， $u$ 和 $v$ 不相邻，$u$ 可达 $v$ ，若 $V'\subseteq V$ ， $u, v\notin V'$ ，且在 $G\left[V\\V'\right]$ 中 $u$ 和 $v$ 不连通，则 $V'$ 被称作 $u$ 到 $v$ 的点割集。 $u$ 到 $v$ 的最小点割集的大小被称作 $u$ 到 $v$ 的 **局部点连通度 (Local connectivity)**，记作 $\kappa(u, v)$ 。

还可以在边上作类似的定义：

对于连通图 $G = (V, E)$ ，若 $E'\subseteq E$ 且 $G' = (V, E\\E')$ （即从 $G$ 中删去 $E'$ 中的边）不是连通图，则 $E'$ 是图 $G$ 的一个 **边割集 (Edge cut)** 。大小为一的边割集又被称作 **桥 (Bridge)** 。

对于连通图 $G = (V, E)$ 和整数 $k$，若 $G$ 不存在大小为 $k-1$ 的边割集，则称图 $G$ 是 **$k$-边连通的 ($k$-edge-connected)** ，而使得上式成立的最大的 $k$ 被称作图 $G$ 的 **边连通度 (Edge connectivity)** ，记作 $\lamda(G)$ 。（对于任何图，边联通度即为最小边割集的大小。）

对于图 $G = (V, E)$ 以及 $u, v\in V$ 满足 $u\ne v$ ， $u$ 可达 $v$ ，若 $E'\subseteq E$ ，且在 $G'=(V, E\\E')$ 中 $u$ 和 $v$ 不连通，则 $E'$ 被称作 $u$ 到 $v$ 的边割集。 $u$ 到 $v$ 的最小边割集的大小被称作 $u$ 到 $v$ 的 **局部边连通度 (Local edge-connectivity)**，记作 $\lamda(u, v)$ 。

**点双连通 (Biconnected)** 几乎与 $2$-点连通完全一致，除了一条边连接两个点构成的图，它是点双连通的，但不是 $2$-点连通的。换句话说，没有割点的连通图是点双连通的。

**边双连通 ($2$-edge-connected)** 与 $2$-边双连通完全一致。换句话说，没有桥的连通图是边双连通的。

与连通分量类似，也有 **点双连通分量 (Biconnected component)** （极大点双连通子图） 和 **边双连通分量 ($2$-edge-connected component)** （极大边双连通子图）。

Whitney 定理：对任意的图 $G$ ，有 $\kappa(G)\le \lamda(G)\le \delta(G)$ 。（不等式中的三项分别为点连通度、边连通度、最小度。）

## 稀疏图/稠密图

若一张图的边数远小于其点数的平方，那么它是一张 **稀疏图 (Sparse graph)** 。

若一张图的边数接近其点数的平方，那么它是一张 **稠密图 (Dense graph)** 。

这两个概念并没有严格的定义，一般用于讨论 [时间复杂度](../misc/complexity.md) 为 $O(|V|^2)$ 的算法与 $O(|E|)$ 的算法的效率差异（在稠密图上这两种算法效率相当，而在稀疏图上 $O(m)$ 的算法效率明显更高）。

## 补图

对于无向简单图 $G = (V, E)$，它的 **补图 (Complement graph)** 指的是这样的一张图：记作 $\bar G$，满足 $V \left( \bar G \right) = V \left( G \right)$，且对任意节点对 $(u, v)$，$(u, v) \in E \left( G \right)$ 当且仅当 $(u, v) \notin E \left( G' \right)$ 。

## 反图

对于有向图 $G = (V, E)$ ，它的 **反图 (Transpose Graph)** 指的是点集不变，每条边反向得到的图，即：若 $G$ 的反图为 $G'=(V, E')$ ，则 $E'=\{(v, u)|(u, v)\in E\}$ 。

## 特殊的图

若无向简单图 $G$ 满足任意两点间均有边，则称 $G$ 为 **完全图 (Complete graph)** ，$n$ 阶完全图记作 $K_n$。

边集为空的图称为 **零图 (Null graph)** ，$n$ 阶零图记作 $N_n$。易知，$N_n$ 为 $K_n$ 互为补图。

若有向简单图 $G$ 满足任意不同两点间都有恰好一条边（单向），则称 $G$ 为 **竞赛图 (Tournament graph)** 。

若无向简单图 $G = \left( V, E \right)$ 的所有边恰好构成一个圈，则称 $G$ 为 **环图/圈图 (Cycle graph)** ，$n$ ($n \geq 3$) 阶圈图记作 $C_n$。易知，一张图为圈图的充分必要条件是，它是 $2$-正则连通图。

若无向简单图 $G = \left( V, E \right)$ 满足，存在一个点 $v$ 为支配点，其余点之间没有边相连，则称 $G$ 为 **星图/菊花图 (Star graph)** ，$n + 1$ ($n \geq 1$) 阶星图记作 $S_n$。

若无向简单图 $G = \left( V, E \right)$ 满足，存在一个点 $v$ 为支配点，其它点之间构成一个圈，则称 $G$ 为 **轮图 (Wheel Graph)** ，$n + 1$ ($n \geq 3$) 阶轮图记作 $W_n$。

若无向简单图 $G = \left( V, E \right)$ 的所有边恰好构成一条简单路径，则称 $G$ 为 **链 (Chain/Path Graph)** ，$n$ 阶的链记作 $P_n$ 。易知，一条链由一个圈图删去一条边而得。

如果一张无向连通图不含环，则称它是一棵 **树 (Tree)** 。相关内容详见 [树基础](./tree-basic.md) 。

如果一张无向连通图包含恰好一个环，则称它是一棵 **基环树** 。

如果一张有向弱连通图每个点的入度都为 $1$ ，则称它是一棵 **基环外向树** 。

如果一张有向弱连通图每个点的出度都为 $1$ ，则称它是一棵 **基环内向树** 。

多棵树可以组成一个 **森林 (Forest)** ，多棵基环树可以组成 **基环森林** ，多棵基环外向树可以组成 **基环外向树森林** ，多棵基环内向树可以组成 **基环内向森林 (Functional graph)** 。

如果一张无向连通图的每条边最多在一个环内，则称它是一棵 **仙人掌 (Cactus)** 。多棵仙人掌可以组成 **沙漠** 。

如果一张图的点集可以被分为两部分，每一部分的内部都没有连边，那么这张图是一张 **二分图 (Bipartite graph)** 。相关内容详见 [二分图](./bi-graph.md) 。

## 同构

对两个阶数相等的简单图 $G, H$，如果存在一个双射 $f : V(G) \to V(H)$，满足对于两个顶点 $u, v$ ($u \neq v$)，$u, v$ 在 $G$ 中相邻当且仅当 $f(u)$ 和 $f(V)$ 在 $H$ 中相邻，则我们称 $f$ 为 $G$ 到 $H$ 的一个 **同构 (Isomorphism)** ，且图 $G$ 与图 $H$ 是 **同构的 (Isomorphic)** ，记作 $G \cong H$。

## 无向简单图的二元运算

对于无向简单图，我们可以定义如下二元运算：

**交 (Intersection)**：两张图 $G = \left( V_1, E_1 \right), H = \left( V_2, E_2 \right)$ 的交定义成图 $G \cap H = \left( V_1 \cap V_2, E_1 \cap E_2 \right)$。

容易证明两个无向简单图的交还是无向简单图。

**并 (Union)**：两张图 $G = \left( V_1, E_1 \right), H = \left( V_2, E_2 \right)$ 的并定义成图 $G \cup H = \left( V_1 \cup V_2, E_1 \cup E_2 \right)$。

**和 (Sum)/直和 (Direct sum)** ：对于 $G = \left( V_1, E_1 \right), H = \left( V_2, E_2 \right)$，任意构造 $H' \cong H$ 使得 $V \left( H' \right) \cap V_1 = \varnothing$ ($H'$ 可以等于 $H$)。此时与 $G \cup H'$ 同构的任何图称为 $G$ 和 $H$ 的和/直和/不交并，记作 $G + H$ 或 $G \oplus H$。

若 $G$ 与 $H$ 的点集本身不相交，则 $G \cup H = G + H$。

比如，森林可以定义成若干棵树的和。

???+note "并与和的区别"
    可以理解为，“并”会让两张图中“名字相同”的点、边合并，而“和”则不会。



## 参考资料

[OI 中转站 - 图论概念梳理](https://yhx-12243.github.io/OI-transit/memos/14.html)

[Wikipedia](https://en.wikipedia.org/wiki/Glossary_of_graph_theory_terms)（以及相关概念的对应词条）

离散数学（修订版），田文成 周禄新 编著，天津文学出版社，P184-187