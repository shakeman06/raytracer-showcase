# Project 4: Antialias

The project handout can be found [here](https://cs1230.graphics/projects/ray/3).

## Output Comparison

| File/Method To Produce Output | Expected Output | Your Output |
| :---------------------------------------: | :--------------------------------------------------: | :-------------------------------------------------: | 
| shadow_test_4spp_grid.ini |  ![](https://raw.githubusercontent.com/BrownCSCI1230/scenefiles/main/antialias/required_outputs/shadow_test_4spp_grid.png) | ![](student_outputs/antialias/required/shadow_test_4spp_grid.png) |
| shadow_test_4spp_rand.ini |  ![](https://raw.githubusercontent.com/BrownCSCI1230/scenefiles/main/antialias/required_outputs/shadow_test_4spp_rand.png) | ![](student_outputs/antialias/required/shadow_test_4spp_rand.png) |
| shadow_test_4spp_strat.ini |  ![](https://raw.githubusercontent.com/BrownCSCI1230/scenefiles/main/antialias/required_outputs/shadow_test_4spp_strat.png) | ![](student_outputs/antialias/required/shadow_test_4spp_strat.png) |
| mirror_primitives_64spp_strat.ini |  ![](https://raw.githubusercontent.com/BrownCSCI1230/scenefiles/main/antialias/required_outputs/mirror_primitives_64spp_strat.png) | ![](student_outputs/antialias/required/mirror_primitives_64spp_strat.png) |
| mirror_primitives_colordebug.ini | ![](https://raw.githubusercontent.com/BrownCSCI1230/scenefiles/main/antialias/required_outputs/mirror_primitives_colordebug.png) | ![](student_outputs/antialias/required/mirror_primitives_colordebug.png) |
| cube_bilinear.ini |  ![](https://raw.githubusercontent.com/BrownCSCI1230/scenefiles/main/antialias/required_outputs/cube_bilinear.png) | ![](student_outputs/antialias/required/cube_bilinear.png) |
| unit_checkerboard_bilinear.ini |  ![](https://raw.githubusercontent.com/BrownCSCI1230/scenefiles/main/antialias/required_outputs/unit_checkerboard_bilinear.png) | ![](student_outputs/antialias/required/unit_checkerboard_bilinear.png) |
| sphere_checkerboard_bilinear.ini |  ![](https://raw.githubusercontent.com/BrownCSCI1230/scenefiles/main/antialias/required_outputs/sphere_checkerboard_bilinear.png) | ![](student_outputs/antialias/required/sphere_checkerboard_bilinear.png) |
| unit_checkerboard_mipmap_bilinear.ini |  ![](https://raw.githubusercontent.com/BrownCSCI1230/scenefiles/main/antialias/required_outputs/unit_checkerboard_mipmap_bilinear.png) | ![](student_outputs/antialias/required/unit_checkerboard_mipmap_bilinear.png) |
| sphere_checkerboard_mipmap_bilinear.ini |  ![](https://raw.githubusercontent.com/BrownCSCI1230/scenefiles/main/antialias/required_outputs/sphere_checkerboard_mipmap_bilinear.png) | ![](student_outputs/antialias/required/sphere_checkerboard_mipmap_bilinear.png) |
| cone_checkerboard_mipmap_bilinear.ini |  ![](https://raw.githubusercontent.com/BrownCSCI1230/scenefiles/main/antialias/required_outputs/cone_checkerboard_mipmap_bilinear.png) | ![](student_outputs/antialias/required/cone_checkerboard_mipmap_bilinear.png) |
| cylinder_checkerboard_mipmap_bilinear.ini |  ![](https://raw.githubusercontent.com/BrownCSCI1230/scenefiles/main/antialias/required_outputs/cylinder_checkerboard_mipmap_bilinear.png) | ![](student_outputs/antialias/required/cylinder_checkerboard_mipmap_bilinear.png) |
| moire_checkerboard_mipmap_bilinear.ini |  ![](https://raw.githubusercontent.com/BrownCSCI1230/scenefiles/main/antialias/required_outputs/moire_checkerboard_mipmap_bilinear.png) | ![](student_outputs/antialias/required/moire_checkerboard_mipmap_bilinear.png) |
| moire_checkerboard_colordebug_bilinear.ini | ![](https://raw.githubusercontent.com/BrownCSCI1230/scenefiles/main/antialias/required_outputs/moire_checkerboard_colordebug_bilinear.png) | ![](student_outputs/antialias/required/moire_checkerboard_colordebug_bilinear.png) |
| unit_checkerboard_trilinear.ini |  ![](https://raw.githubusercontent.com/BrownCSCI1230/scenefiles/main/antialias/required_outputs/unit_checkerboard_trilinear.png) | ![](student_outputs/antialias/required/unit_checkerboard_trilinear.png) |
| sphere_checkerboard_trilinear.ini |  ![](https://raw.githubusercontent.com/BrownCSCI1230/scenefiles/main/antialias/required_outputs/sphere_checkerboard_trilinear.png) | ![](student_outputs/antialias/required/sphere_checkerboard_trilinear.png) |
| cone_checkerboard_trilinear.ini |  ![](https://raw.githubusercontent.com/BrownCSCI1230/scenefiles/main/antialias/required_outputs/cone_checkerboard_trilinear.png) | ![](student_outputs/antialias/required/cone_checkerboard_trilinear.png) |
| cylinder_checkerboard_trilinear.ini |  ![](https://raw.githubusercontent.com/BrownCSCI1230/scenefiles/main/antialias/required_outputs/cylinder_checkerboard_trilinear.png) | ![](student_outputs/antialias/required/cylinder_checkerboard_trilinear.png) |
| moire_checkerboard_trilinear.ini |  ![](https://raw.githubusercontent.com/BrownCSCI1230/scenefiles/main/antialias/required_outputs/moire_checkerboard_trilinear.png) | ![](student_outputs/antialias/required/moire_checkerboard_trilinear.png) |
| moire_checkerboard_colordebug_trilinear.ini | ![](https://raw.githubusercontent.com/BrownCSCI1230/scenefiles/main/antialias/required_outputs/moire_checkerboard_colordebug_trilinear.png) | ![](student_outputs/antialias/required/moire_checkerboard_colordebug_trilinear.png) |

## Design Choices

Sampling offsets live in `sampler.cpp` for readability, and `mipmap.cpp` holds the mipmap helpers. Added a `MipLevel` struct and made `Texture` hold a vector of `MipLevels`. Each shape's mip chain builds when the scene loads and gets cached, with `HitPoint` storing a pointer to it. `Ray` stores both the unnormalized and normalized direction vectors.

## Known Bugs

The random sampler's aliasing looks a bit fuzzier than the reference output, likely from rounding error (confirmed the underlying logic was correct in office hours). The reflection colors in `mirror_primitives_colordebug` don't exactly match the reference image either; this is expected, the reference uses an extra-credit feature not implemented here.
