---
title: DrRacket使用技巧总结
date: 2018-12-03 14:27:03
categories: 技术人生
tags: [DrRacket, Lisp]
---
## 引用其他文件的函数

假设test.scm想引用max-two.scm中的一个函数max-two，可以这样，

test.scm
```scheme
#lang sicp

(#%require rackunit)
(#%require "max-two.scm")

(max-two 2 3 4)
```

<!--more-->

max-two.scm
```scheme
#lang sicp

;; 千万别忘了这一句
(#%provide (all-defined))

(define (max-two x y z)
  (define (min-three x y z)
    (cond ((>= x y) (if (>= y z) z y))
          (else (if (>= x z) z x))))
  (- (+ x y z) (min-three x y z)))
```

## Window10安装sicp包

7.1版本ui界面安装pkg报错cadr: contract violation，可以使用命令行安装，命令如下：

```scheme
raco pkg install --auto sicp
```
