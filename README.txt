-------------------------------------------------------------------------------
  Citation Details
-------------------------------------------------------------------------------
  
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
  A copy of the GPL license is provided in the "GPL.txt" file.
  
  
-------------------------------------------------------------------------------
  Source code structure
-------------------------------------------------------------------------------
  
  - src       -> contains the five shadow removers with their parameters
  - src/utils -> contains helper classes used by the shadow removers
  - samples   -> frames and masks used in the usage example
  
  
-------------------------------------------------------------------------------
  Dependencies
-------------------------------------------------------------------------------
  
  The following OpenCV 2.0 components are required:
  
    - cv
    - cvaux
    - cxcore
    - highgui (used for image loading and display in the usage example)
    
  
-------------------------------------------------------------------------------
  Usage example
-------------------------------------------------------------------------------

#include <highgui.h>
#include "ChromacityShadRem.h"
#include "GeometryShadRem.h"
#include "LrTextureShadRem.h"
#include "PhysicalShadRem.h"
#include "SrTextureShadRem.h"

int main()
  {
	// load frame, background and foreground
	cv::Mat frame = cv::imread("samples/frame.bmp");
	cv::Mat bg = cv::imread("samples/bg.bmp");
	cv::Mat fg = cv::imread("samples/fg.bmp", CV_LOAD_IMAGE_GRAYSCALE);
  
	// create shadow removers
	ChromacityShadRem chr;
	PhysicalShadRem phy;
	GeometryShadRem geo;
	SrTextureShadRem srTex;
	LrTextureShadRem lrTex;
  
	// matrices to store the masks after shadow removal
	cv::Mat chrMask, phyMask, geoMask, srTexMask, lrTexMask;
  
	// remove shadows
	chr.removeShadows(frame, fg, bg, chrMask);
	phy.removeShadows(frame, fg, bg, phyMask);
	geo.removeShadows(frame, fg, bg, geoMask);
	srTex.removeShadows(frame, fg, bg, srTexMask);
	lrTex.removeShadows(frame, fg, bg, lrTexMask);
  
	// show results
	cv::imshow("frame", frame);
	cv::imshow("bg", bg);
	cv::imshow("fg", fg);
	cv::imshow("chr", chrMask);
	cv::imshow("phy", phyMask);
	cv::imshow("geo", geoMask);
	cv::imshow("srTex", srTexMask);
	cv::imshow("lrTex", lrTexMask);
  
	cv::waitKey();
  
	return 0;
  }
