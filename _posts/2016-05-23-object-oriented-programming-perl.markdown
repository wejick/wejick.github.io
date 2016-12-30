---
author: wejick
comments: true
date: 2016-05-23 05:55:37+00:00
layout: post
link: http://blog.ggiovani.com/object-oriented-programming-perl/
slug: object-oriented-programming-perl
title: Perl and Object Oriented Programming
wordpress_id: 92
categories:
- Programming
tags:
- moose
- oop
- perl
---

## Perl as OOP language



![perl moose ggiovani.com](http://articles.mongueurs.net/comptes-rendus/fpw-2007/moose.gif)

Object oriented programming today is something like air, we breath with it every single time. That's why the first thing to ask when learning new programming language is 'Does this language support OOP ?' if yes then 'How does one able to write a class then using the object ?". I always use that question, also this time when learning about Perl.

Basically Perl does support OOP however it doesn't recommend you to use it, instead it recommends to use higher level OOP or in Perl terms is other Object Oriented System. Perl native OO System is called [perlobj](http://perldoc.perl.org/perlobj.html#DESCRIPTION) , it has all we need to do all OOP thingy. However as the documentation said, it doesn't practical to use it for everyday need. So the first question is answered, yes Perl does support OOP.<!-- more -->

After spending some times to explore the idea of 'other OO System', I found there are several popular OO System with Moose as the most popular choice. Before I learned about Moose, I was struggling with understanding the logic behind perlobj. Learning Perlobj needs familiarity with some Perl concepts which is very much different from C.

So the second question also answered, One can learn Moose to write OOP on perl.

Moose really make creating class more pleasant than perlobj, look this example I got from [here ](http://www.houseabsolute.com/presentations/intro-moose-class/)



## Using Moose




    
    <code>package Person;
    use Moose;
    
    has last_name => (
        is  => 'rw',
        isa => 'Str',
    );
    </code>





## Without Moose




    
    <code>package Person;
    use strict;
    use warnings;
    use Carp 'confess';
    
    sub new {
        my $class = shift;
        my %args  = @_;
        my $self  = {};
    
        if (exists $args{last_name}) {
            confess "Attribute (last_name) does not pass the type constraint because: "
                    . "Validation failed for 'Str' with value $args{last_name}"
                if ref($args{last_name});
            $self->{last_nane} = $args{last_name};
        }
    
        return bless $self, $class;
    }
    
    sub last_name {
        my $self = shift;
    
        if (@_) {
            my $value = shift;
            confess "Attribute (last_name) does not pass the type constraint because: "
                    . "Validation failed for 'Str' with value $value"
                if ref($value);
            $self->{last_name} = $value;
        }
    
        return $self->{last_name};
    }</code>




