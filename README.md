# Installation

1. Clone this repository
    ```shell
    $ git clone https://github.com/miloserdow/shadows
    ```
2. Create a build directory
    ```shell
    $ mkdir build
    $ cd build
    ```
3. Run cmake
    ```shell
    $ cmake -DBUILD_EXAMPLES=y ../shadows
    ```
4. Build the project
    ```shell
    $ make
    ```
# Citation Details
  If you use this code in your research and/or software,
  please cite the following journal article:
    
    A. Sanin, C. Sanderson, B.C. Lovell.
    Shadow Detection: A Survey and Comparative Evaluation of Recent Methods.
    Pattern Recognition, Vol. 45, No. 4, pp. 1684-1695, 2012.
    
    DOI: 10.1016/j.patcog.2011.10.001
  
  
  You can obtain a copy of this paper via:
  http://dx.doi.org/10.1016/j.patcog.2011.10.001
  
  
-------------------------------------------------------------------------------
  License
-------------------------------------------------------------------------------
  
  The source code is provided without any warranty of fitness for any purpose.
  You can redistribute it and/or modify it under the terms of the
  GNU General Public License (GPL) as published by the Free Software Foundation,
  either version 3 of the License or (at your option) any later version.
  A copy of the GPL license is provided in the "LICENSE" file.
  
  
-------------------------------------------------------------------------------
  Source code structure
-------------------------------------------------------------------------------
  
  - src       -> contains the five shadow removers with their parameters
  - src/utils -> contains helper classes used by the shadow removers
  - samples   -> frames and masks used in the usage example
  - main.cpp  -> usage example
  
-------------------------------------------------------------------------------
  Dependencies
-------------------------------------------------------------------------------
  
  OpenCV >= 3.0 is required. 
