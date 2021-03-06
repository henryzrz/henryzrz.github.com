---
layout: post
title: "二分图"
description: ""
category: ACM资料
tags: [ACM]
---
{% include JB/setup %}

#图论点、边集和二分图的相关概念和性质

 
####点覆盖、最小点覆盖		
点覆盖集即一个点集，使得所有边至少有一个端点在集合里。或者说是“点” 覆盖了所有“边”。。极小点覆盖(minimal vertex covering)：本身为点覆盖，其真子集都不是。最小点覆盖(minimum vertex covering)：点最少的点覆盖。点覆盖数(vertex covering number)：最小点覆盖的点数。
 
####边覆盖、极小边覆盖			
边覆盖集即一个边集，使得所有点都与集合里的边邻接。或者说是“边” 覆盖了所有“点”。极小边覆盖(minimal edge covering)：本身是边覆盖，其真子集都不是。最小边覆盖(minimum edge covering)：边最少的边覆盖。边覆盖数(edge covering number)：最小边覆盖的边数。
 
####独立集、极大独立集			
独立集即一个点集，集合中任两个结点不相邻，则称V为独立集。或者说是导出的子图是零图（没有边）的点集。极大独立集(maximal independent set)：本身为独立集，再加入任何点都不是。最大独立集(maximum independent set)：点最多的独立集。独立数(independent number)：最大独立集的点。
 
####团		
团即一个点集，集合中任两个结点相邻。或者说是导出的子图是完全图的点集。极大团(maximal clique)：本身为团，再加入任何点都不是。最大团(maximum clique)：点最多的团。团数(clique number)：最大团的点数。
 
####边独立集、极大边独立集		
边独立集即一个边集，满足边集中的任两边不邻接。极大边独立集(maximal edge independent set)：本身为边独立集，再加入任何边都不是。最大边独立集(maximum edge independent set)：边最多的边独立集。边独立数(edge independent number)：最大边	独立集的边数。
 
边独立集又称匹配(matching)，相应的有极大匹配(maximal matching)，最大匹配(maximum matching)，匹配数(matching number)。
 
####支配集、极小支配集		
支配集即一个点集，使得所有其他点至少有一个相邻点在集合里。或者说是一部分的“点”支配了所有“点”。极小支配集(minimal dominating set)：本身为支配集，其真子集都不是。最小支配集(minimum dominating set)：点最少的支配集。支配数(dominating number)：最小支配集的点数。
 
####边支配集、极小边支配集		
边支配集即一个边集，使得所有边至少有一条邻接边在集合里。或者说是一部分的“边”支配了所有“边”。极小边支配集(minimal edge dominating set)：本身是边支配集，其真子集都不是。最小边支配集(minimum edge dominating set)：边最少的边支配集。边支配数(edge dominating number)：最小边支配集的边数。
 
####最小路径覆盖		
最小路径覆盖(path covering)：是“路径” 覆盖“点”，即用尽量少的不相交简单路径覆盖有向无环图G的所有顶点，即每个顶点严格属于一条路径。路径的长度可能为0(单个点)。
最小路径覆盖数＝G的点数－最小路径覆盖中的边数。应该使得最小路径覆盖中的边数尽量多，但是又不能让两条边在同一个顶点相交。拆点：将每一个顶点i拆成两个顶点Xi和Yi。然后根据原图中边的信息，从X部往Y部引边。所有边的方向都是由X部到Y部。因此，所转化出的二分图的最大匹配数则是原图G中最小路径覆盖上的边数。因此由最小路径覆盖数＝原图G的顶点数－二分图的最大匹配数便可以得解。
 
####匹配		
	匹配(matching)是一个边集，满足边集中的边两两不邻接。匹配又称边独立集(edge independent set)。
	在匹配中的点称为匹配点(matched vertex)或饱和点；反之，称为未匹配点(unmatched vertex)或未饱和点。
	交错轨(alternating path)是图的一条简单路径，满足任意相邻的两条边，一条在匹配内，一条不在匹配内。
	增广轨(augmenting path)：是一个始点与终点都为未匹配点的交错轨。
	最大匹配(maximum matching)是具有最多边的匹配。
	匹配数(matching number)是最大匹配的大小。
	完美匹配(perfect matching)是匹配了所有点的匹配。
	完备匹配(complete matching)是匹配了二分图较小集合（二分图X，Y中小的那个）的所有点的匹配。
	增广轨定理：一个匹配是最大匹配当且仅当没有增广轨。
所有匹配算法都是基于增广轨定理：一个匹配是最大匹配当且仅当没有增广轨。这个定理适用于任意图。
 
####二分图的性质	

	
二分图中，点覆盖数是匹配数。
		
	(1) 二分图的最大匹配数等于最小覆盖数，即求最少的点使得每条边都至少和其中的一个点相关联，很显然直接取最大匹配的一段节点即可。	
	(2) 二分图的独立数等于顶点数减去最大匹配数，很显然的把最大匹配两端的点都从顶点集中去掉这个时候剩余的点是独立集，这是|V|-2*|M|，同时必然可以从每条匹配边的两端取一个点加入独立集并且保持其独立集性质。  
	(3) DAG的最小路径覆盖，将每个点拆点后作最大匹配，结果为n-m，求具体路径的时候顺着匹配边走就可以，匹配边i→j',j→k',k→l'....构成一条有向路径。		
	(4) 最大匹配数=左边匹配点+右边未匹配点。因为在最大匹配集中的任意一条边，如果他的左边没标记，右边被标记了，那么我们就可找到一条新的增广路，所以每一条边都至少被一个点覆盖。  
	(5)最小边覆盖=图中点的个数-最大匹配数=最大独立集。		