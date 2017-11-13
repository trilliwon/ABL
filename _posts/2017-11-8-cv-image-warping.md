---
layout: post
title:  "Image transformation"
date:   2017-11-08 23:00:00 +0900
categories: CV
---


1. translation
    - just move the source pixel points to destination points
    `(x, y) = (x + dx, y + dy)`
2. euclidean
    - inverse warping is needed to prevent holes
    - linear interpolation is necessary
    `(x, y) = (con(theta), -sin(theta))...`
3. similarity
4. affine
5. projective
