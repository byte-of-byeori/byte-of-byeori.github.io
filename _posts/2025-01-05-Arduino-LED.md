---
layout: single
title: "[Arduino Tutorial] 1. LED"
categories: Arduino
tags: [arduino, tutorial] 
# toc: true
# author_profile: false
# sidebar:
#     nav: "docs"
---

### Define Pins

```
# define BLUE 3
# define GREEN 5
# define RED 6
```

### Setup function

```
void setup()
{
pinMode(RED, OUTPUT);
pinMode(GREEN, OUTPUT);
pinMode(BLUE, OUTPUT);

digitalWrite(RED, HIGH);
digitalWrite(GREEN, LOW);
digitalWrite(BLUE, LOW);
}
```