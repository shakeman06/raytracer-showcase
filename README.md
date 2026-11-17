# Ray Tracer

A C++/Qt ray tracer built from scratch for Brown's CS 1230 (Computer Graphics), supporting recursive reflections, antialiasing, and texture filtering across 4 shape types and 3 light types.

Source code is kept private per course policy. This repo shows renders only.

## Features

- Recursive reflections up to 8 bounces deep
- Grid, random, and stratified supersampling (up to 64 samples/pixel)
- Bilinear and trilinear texture filtering
- 10-level mipmap pyramids with ray differentials for automatic detail selection
- Custom scene parser and camera view matrix
- 1024x768 renders, validated across 20 test scenes

## Renders

### Reflections

![](all_outputs/illuminate/required/reflections_complex.png)
![](all_outputs/antialias/required/mirror_primitives_64spp_strat.png)

### Texture Filtering & Mipmapping

![](all_outputs/illuminate/required/texture_sphere2.png)
![](all_outputs/antialias/required/cone_checkerboard_mipmap_bilinear.png)
![](all_outputs/antialias/required/moire_checkerboard_trilinear.png)

### Lighting

![](all_outputs/illuminate/required/spot_light_2.png)
![](all_outputs/illuminate/required/shadow_special_case.png)

### Primitives

![](all_outputs/intersect/required/unit_cone_cap.png)
![](all_outputs/intersect/required/parse_matrix.png)

## Tech Stack

C++, Qt, GLM
