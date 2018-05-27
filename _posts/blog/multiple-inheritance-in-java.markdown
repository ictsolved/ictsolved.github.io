---
layout: post
title: "Multiple Inheritance in JAVA"
description: 
date: 2018-05-25 20:34:46 +0545
author: sarad
categories:
- blog
- Programming
- JAVA
tags: JAVA, Multiple Inheritance, Diamond Problem
generes: JAVA
img: 
imagealt: 
thumb: 
---

#### Why Java does not support multiple inheritance?
Multiple Inheritance means that a class can inherit behavior from two or more parent classes. The issue with Multiple Inheritance is that both the parent classes may have different implementation for the same method. So they have different ways of doing the same thing. Now which implementation should the child class choose? This leads to ambiguity in Multiple Inheritance. This is the main reason for Java not supporting Multiple Inheritance in implementation. Lets say you have a class TV and another class AtomBomb. Both have method switchOn() but only TV has switchOff() method. If your class inherits from both these classes then you have an issue that you can switchOn() both parents, but switchOff will only switchOff() TV. But you can implement multiple interfaces in Java.

#### How can you do multiple inheritances in Java?
This is a question to trick people coming from C++ and Scala background to Java. There are many Object Oriented languages that support multiple inheritances. But Java is not one of them. Answer of this question can be that, Java does support multiple inheritances of by allowing an interface to extend other interfaces. You can implement more than one interface. But you cannot extend multiple classes. So Java doesn't support multiple inheritances of implementation. But in Java 8, the default method breaks the rule of multiple inheritances behavior.

#### How does Java 8 solve Diamond problem of Multiple Inheritance?
In Multiple Inheritance if a class extends more than one classes with two different implementation of same method then it causes Diamond problem. Consider following example to see problem and solution for Diamond problem in Java 8:

	public interface BaseInterface {
	    default void display() {}
	    public interface BaseOne extends BaseInterface {}
	    public interface BaseTwo extends BaseInterface {}
	    public class ChildClass implements BaseOne, BaseTwo {}
 
 In the above code, class ChildClass gives compile time error.Java Compiler cannot decide which display method should it invoke in ChildClass. To solve this problem, Java SE 8 has given the following remedy:

	public interface A {
	    default void display() {}
	    public interface B extends A {}
	    public interface C extends A {}
	    public class D implements B, C {
	        default void display() {
	            B.super.display();
	        }
	    }
	    public interface BaseInterface {
	        default void display() {}
	        public interface BaseOne extends BaseInterface {}
	        public interface BaseTwo extends BaseInterface {}
	        public class ChildClass implements BaseOne, BaseTwo {
	            default void display() {
	                BaseOne.super.display();
	            }
	        }

The method invocation at BaseOne.super.display(); solves the Diamond problem as it resolves the confusion for compiler.

#### How Java 8 supports Multiple Inheritance?
In Multiple Inheritance a class can inherit behavior from more than one parent classes. Prior to Java 8, a class can implement multiple interfaces but extend only one class. In Java 8, we can have method implementation within an interface. So an interface behaves like an Abstract class. Now if we implement more than one interface with method implementation in a class, it means we are inheriting behavior from multiple abstract classes. That is how we get Multiple Inheritance in Java 8.