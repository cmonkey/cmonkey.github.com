---
layout: page
title: About
permalink: /about/
---

    #lang racket
    (define calc
      (lambda (exp)
        (match exp                                  ;; 匹配表达式的两种情况
               [(? number? x) x]                    ;; 是数字，直接返回
               [`(,op ,e1 ,e2)                      ;; 匹配并且提取出操作符 op 和两个操作数e1, e2
                (let ([v1 (calc e1)]                ;; 递归调用calc自己，得到e1的值
                      [v2 (calc e2)])               ;; 递归调用calc自己，得到e2的值
                  (match op                         ;; 分支;处理操作符op的4中情况
                         ['+ (+ v1 v2)]             ;; 如果是+号，输出结果为（+ v1 v2)
                         ['- (- v1 v2)]             ;; 如果是-号，输出结果为(- v1 v2)
                         ['* (* v1 v2)]             ;; 如果是×号，输出结果为(* v1 v2)
                         ['/ (/ v1 v2)]             ;; 如果是/号，输出结果为(/ v1 v2)
                         ))
                ]

               )
        )
      )


