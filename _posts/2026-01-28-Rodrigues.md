---
title: Rodrigues方程推导
date: 2026-01-28
categories: [数学]
tags: [几何,代数]
math: true
---
# Rodrigues方程
将一个向量 $v$绕轴 $s$逆时针旋转 $\theta$度角，这样一个变换我们应该如何表示？Rodrigues方程就是对该问题的解答，有一个十分自然的方法可以证明Rodrigues方程，我将其梳理如下。  

## 1. 矩阵与 $ℝ^3$上的叉乘
先回忆叉乘的定义，$s\times v$是一个同时垂直于s与v，大小等于s,v构成的平行四边形面积相等的，且使得s,v, $s\times v$构成一右手坐标系的向量（如果s,v都不为0）。
我们知道，如果设 $s=(s_1,s_2,s_3),v=(v_1,v_2,v_3)$，则 $s\times v=(s_2 v_3 -v_2 s_3,s_3v_1-v_3s_1,s_1v_2-s_2v_1)$，从此公式容易看出，如果将s固定，则
将 $v$映射到 $s\times v$的这个变换这是一个线性变换，可以用矩阵 $A_s=[0,-s_3,s_2;s_3,0,-s_1;-s_2,s_1,0]$表示。因为s固定，所以为了方便，设s为单位向量。 

## 2. 单参数变换群
我们注意到，如果设 $R_\theta$为我们开头设的那个变换，有 $R_{a+b}=R_aR_b$这个性质成立，也就是说，用常微分方程中的术语，它是一个单参数变换群，于是，我们自然而然地要去求它的无穷小生成元，也就是
 $\lim _{θ \to 0} \frac{R _\theta - E }{\theta}$，其中E是单位矩阵。  
 我们考虑一个向量v，通过简单的画图可以知道，如果设w为v垂直于s的分量，则 $R _\theta v- v = R _\theta w -w$，这在一个圆内，所以通过平面的知识可以知道 $\lim _{θ \to 0} \frac{R _\theta v- v }{\theta}$
 存在，且与原来的w垂直，而且它当然与s垂直，至于它的大小，易知实际上与 $w$是一致的，也就是，与 $s\times v$一致， 从而其等于 $± s\times v$，而逆时针的选择，又使得它们的符号一致，所以，我们得到 $\lim _{θ \to 0} \frac{R _\theta - E }{\theta}=A_s$  
 
## 3. 指数映射
 现在，我们容易看出 $\lim _{θ \to a} \frac{R _\theta v - R_av }{\theta-a}=A_sR_av$，也就是说 $F(t)=R_tv$满足 常微分方程 $F'(t)=A_sF(t)$。  
 唯一性告诉我们，这样的方程解是唯一的。  
 指数映射告诉我们，这样的解可以通过 $exp(A_s\theta)v$得出，其中exp定义为 $exp(A)=\sum _{n=0}^{\infty} \frac{A^n}{n!}$。
 所以我们得到了一个 $R _\theta$表达式： $R _\theta=exp(A_s\theta)$。  
 
## 4. 叉乘恒等式
 不过这还不是Rodrigues方程，因为它不容易计算，实际上，使用一些叉乘的恒等式，我们就能进一步化简。  
 回忆一下双重叉积恒等式: $a\times(b\times c)=b (a·c) - c (a·b)$，应用到我们这里，就是$s\times(s\times a)=(s·a)s-v$，从而$s\times(s\times(s\times a))=(s·a)s\times- s\times v=-s \times v$  
 转为矩阵的语言，就是恒等式$A_s^3=-A_s$，利用这个恒等式，我们就有 $exp(A_s\theta)=\sum _{n=0}^{\infty} \theta^n\frac{A_s^n}{n!}=E+A_s\sum _{n=1}^{\infty}(-1)^{n-1} \frac{\theta^{2n-1}}{(2n-1)!}+A_s^2\sum _{n=1}^{\infty}(-1)^{n-1} \frac{\theta^{2n}}{(2n)!}=E+sin\theta A_s + (1-cos \theta) A_s^2$，其中E为单位矩阵。  
 这样，我们就得到了最终的结果： $R _\theta =E+sin\theta A_s + (1-cos \theta) A_s^2$
