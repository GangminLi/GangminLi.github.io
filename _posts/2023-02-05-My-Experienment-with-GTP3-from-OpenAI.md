---
title: "My conversation with GPT3"
style:  app
date: 2023-02-06 12:12:20

author_profile: true

toc_label: "Page Content"

tags:
  - OpenAI
  - GPT3
  - AI
  - auto code
  - ASSMEBLY
  - MIPS
  

header:
  teaser: "/assets/posts/openai/gpt3.png"
---
![GPT3 form OpenAI](/assets/posts/openai/gpt3.png)

## Introduction

Access GPT-3, which performs a variety of natural language tasks, Codex, which translates natural language to code, and DALL·E, which creates and edits original images.

I had many examinitions in the past. Today I put it in to a somple test for coding.

## The tasks

Write MIPS code for calculating a recursive sequence as: 
1. $$ a_n = a_{n-1} + 2b_{n-2}; \\$$
   $$b_n = a_{n-1} - b_{n-2}; \\$$
   with $$a_0 = b_0 = 1$$ and $$a_1 = 2, b_1 = 1. $$ 
2. The code should prompt the user to enter the value of $n$ and display the results in the console. note that you should use recursion with nested procedure linking to implement the code.
3. You should also determine the smallest positive value of $n$ for which your code results in an error and explain the cause of error.


## Here are our conversition

![my question](/assets/posts/openai/Screenshot 1.png "my intial question")
![GPT3](/assets/posts/openai/Screenshot 2.png "GPT3 Answer")
    
    # MIPS code to calculate the recursive sequence
    # an= an-1 + 2bn-2; bn = an-1 - bn-2, a0=b0=1 and a1 = 2, b1 = 1.

    .data
    prompt: .asciiz "Enter the value of n: "
    result_a: .asciiz "a(n) = "
    result_b: .asciiz "b(n) = "
    
    .text
    .globl main
    
    main:
    # read the value of n
    li $v0, 4 # syscall code for print_str
    la $a0, prompt # address of prompt
    syscall
    li $v0, 5 # syscall code for read_int
    syscall
    move $s0, $v0 # save the value of n in $s0

    # call the recursive function to calculate a(n) and b(n)
    li $a0, 1 # initial value of a0
    li $a1, 2 # initial value of a1
    li $t0, 1 # initial value of b0
    li $t1, 1 # initial value of b1
    jal calc

    # print the result
    li $v0, 4 # syscall code for print_str
    la $a0, result_a # address of result_a
    syscall
    li $v0, 1 # syscall code for print_int
    move $a0, $t2 # value of a(n)
    syscall

    li $v0, 4 # syscall code for print_str
    la $a0, result_b # address of result_b
    syscall
    li $v0, 1 # syscall code for print_int
    move $a0, $t3 # value of b(n)
    syscall

    # exit the program
    li $v0, 10 # syscall code for exit
    syscall

    calc:
    addi $sp, $sp, -8 # allocate space for two more variables
    sw $ra, 0($sp) # save return address
    sw $s0, 4($sp) # save the value of n

    beq $s0, 0, end_a # if n = 0, return a0
    beq $s0, 1, end_a # if n = 1, return a1
    subi $s0, $s0, 1 # decrement n
    move $a0, $a1 # pass a1 as the new a0
    move $t0, $t1 # pass b1 as the new b0
    jal calc # call the function again
    add $t2, $v0, $t0 # calculate a(n) = a(n-1) + 2b(n-2)
    sub $t3, $v0, $t0 # calculate b(n) = a(n-1) - b(n-2)
    j end

    end_a:
    move $t2, $a0 # return a0 if n = 0
    move $t3, $t0 # return b0 if n = 0
    
![mq](/assets/posts/openai/Screenshot 3.png "GPT3 Answer")
![GPT3](/assets/posts/openai/Screenshot 4.png "GPT3 Answer")
![GPT3](/assets/posts/openai/Screenshot 5.png "GPT3 Answer")

## Summary
I have no doubt that GPT3 cvan definitly write code. My concern is that if I give this task to student, the studetn can simple opy and paste my question to GPT3 and get answer!

For details of GPT3, see [OpenAI](https://openai.com/api/)

<p>
{% include  share.html %}
</p>

<span style="color:#9e9696"><i> Last updated: 06/02/2023</i> </span>

<p>
{% include  license.html %}
</p>