# Collection-of-LiDAR-Camera-Calibration

A Collection of LiDAR-Camera-Calibration Papers, Toolboxes and Notes. 

Main context of this collection is from [this repo.](https://github.com/Deephome/Awesome-LiDAR-Camera-Calibration). And I added more to it.

I checked the Papers, Toolboxs one by one, to see if they are good for our research(The good and open-sourced ones are explained in Chinese so far, but will be updated in English).

## 1. Target-based methods
|Paper|Target|Feature|Optimization|Toolbox|Note|Achievability|
| --- | --- | --- | --- | --- | --- | --- |
| [Extrinsic Calibration of a Camera and Laser Range Finder (improves camera calibration), 2004](http://lars.mec.ua.pt/public/LAR%20Projects/Modelling/2011_MiguelAlmeida/Documentos%20leitura/Extrinsic%20Calibration%20of%20a%20Camera%20and%20Laser.pdf) | checkerboard |C:Plane (a), L: pts in plane (m)| point-to-plane | [CamLaserCalibraTool](https://github.com/MegviiRobot/CamLaserCalibraTool) | [CN](https://zhuanlan.zhihu.com/p/137501892) | NO: 只开放了2D单线雷达的代码，肯定不行 |
| [Fast Extrinsic Calibration of a Laser Rangefinder to a Camera, 2005](http://www.cs.cmu.edu/~ranjith/lcct.html) | checkerboard| C: Plane (a), L: Plane (m)| plane(n/d) correspondence, point-to-plane | [LCCT](http://www.cs.cmu.edu/~ranjith/lcct.html) | * | NO:比较老，matlab实现的，无ros
|[Extrinsic calibration of a 3D laser scanner and an omnidirectional camera, 2010]()|checkerboard|C: plane (a), L: pts in plane (m)|point-to-plane|[cam_lidar_calib](https://github.com/SubMishMar/cam_lidar_calib)|*| NO：是ros实现的，但是没给执行步骤，且代码整理不好，很多launch文件，需要详细看代码 |
|[LiDAR-Camera Calibration using 3D-3D Point correspondences, 2017](https://arxiv.org/abs/1705.09785)| cardboard + ArUco | C: 3D corners (a), L: 3D corners (m) | ICP | [lidar_camera_calibration](https://github.com/ankitdhall/lidar_camera_calibration) | 实现 | Yes：有详细的代码使用流程，也有视频演示， 流程稍微复杂，但是github超多star，需要实现这个，代码里含有Velodyne的包，不是原生适配Ouster的驱动，含有可能要改动|
|[Reflectance Intensity Assisted Automatic and Accurate Extrinsic Calibration of 3D LiDAR and Panoramic Camera Using a Printed Chessboard, 2017](http://www.mdpi.com/2072-4292/9/8/851/htm)| checkerboard | C: 2D corners (a), L: 3D corners (a) |PnP, angle difference|[ILCC](https://github.com/mfxox/ILCC)|* | Python实现，使用流程较长，需要看懂详细的流程后，可用 |
|[Extrinsic Calibration of Lidar and Camera with Polygon, 2018](https://ram-lab.com/papers/2018/liao_robio2018.pdf) | regular cardboard |C: 2D edge, corners (a), L: 3D edge, pts in plane (a) | point-to-line, point-inside-polygon | [ram-lab/plycal](https://github.com/ram-lab/plycal) | * | 有GUI页面，应该很直观，需要收集 synced image(png,jpg,jpeg) 和 pcd 包，而不是ROS | 
|[Automatic Extrinsic Calibration of a Camera and a 3D LiDAR using Line and Plane Correspondences, 2018](http://www.cs.cmu.edu/~kaess/pub/Zhou18iros.pdf)| checkerboard | C: 3D edge, plane(a), L: 3D edge, pts in plane (a) | direcion/normal, point-to-line, point-to-plane | [Matlab LiDAR Toolbox](https://ww2.mathworks.cn/help/lidar/ug/lidar-and-camera-calibration.html)  |*| Matlab里的官方方法，过程详细 |
|[Improvements to Target-Based 3D LiDAR to Camera Calibration, 2020](https://arxiv.org/pdf/1910.03126v3.pdf)|cardboard with ArUco|C: 2d corners (a), L: 3D corners (a) | PnP, IOU | [github](https://github.com/UMich-BipedLab/extrinsic_lidar_camera_calibration)|*|详细流程，非ros, 需收集pcd文件 
|[ACSC: Automatic Calibration for Non-repetitive Scanning Solid-State LiDAR and Camera Systems, 2020](https://arxiv.org/pdf/2011.08516.pdf)|checkerboard | C: 2D corners (a), L: 3D corners (a) | PnP | [ACSC](https://github.com/HViktorTsoi/ACSC) | * | 有详细流程，ros |
|[Automatic Extrinsic Calibration Method for LiDAR and Camera Sensor Setups, 2021](https://arxiv.org/abs/2101.04431)|cardboard with circle & Aruco| C: 3D points (a), L: 3D points (a) | ICP | [velo2cam_ calibration](https://github.com/beltransen/velo2cam_calibration)|*|有详细流程，ros|
|[Single-Shot is Enough: Panoramic Infrastructure Based Calibration of Multiple Cameras and 3D LiDARs,2021 IROS](https://arxiv.org/pdf/2103.12941.pdf)|panoramic infrastructure|C: CCTag(a), L: corner points and vectors(a)|PnP, ICP|[multiple-cameras-and-3D-LiDARs-extrinsic-calibration](https://github.com/alibaba/multiple-cameras-and-3D-LiDARs-extrinsic-calibration)|*| 标定物很复杂，且使用流程不太详细，算了 |
|[Joint Camera Intrinsic and LiDAR-Camera Extrinsic Calibration, 2023, ICRA](https://arxiv.org/pdf/2202.13708.pdf)|chessboard + circles | C: chessboard corners, circle centers, L: circle centers | PnP, intrinsic constraints (corners, cirlce center)| [OpenCalib/JointCalib](https://github.com/OpenCalib/JointCalib) | [CN](https://mp.weixin.qq.com/s/AcygRdkTlb_X9Rn8jSYXAQ) | github使用流程很不详细，需要详细看论文和代码 |
|[Optimising the selection of samples for robust lidar camera calibration, 2021, ITSC ](https://arxiv.org/abs/2103.12287)| Chessboard |  | | [Camera-LiDAR Calibration](https://github.com/acfr/cam_lidar_calibration) |  | Yes:有详细ros流程，还有youtube视频教学 |
|[ROS official method](http://wiki.ros.org/cam2lidar/Tutorials/How%20to%20calibrate%20Lidar%20and%20Camera)| fiducial mark+types |  | | [ROS official method](http://wiki.ros.org/cam2lidar/Tutorials/How%20to%20calibrate%20Lidar%20and%20Camera) | 实现 | ros官网的一个方法，比较老，需要实现一下，毕竟ros官方 |
| [Another high star repo](https://github.com/heethesh/lidar_camera_calibration) | Chessboard |  | | [Another high star repo](https://github.com/heethesh/lidar_camera_calibration) | 实现 |  |


> C: camera, L: LiDAR, a: automaic, m: manual

## 2. Targetless methods  

### 2.1. Motion-based methods
|Paper|Feature|Optimization|Toolbox|Note| Achievability | 
| --- | --- | --- | --- | --- | --- |
|[LiDAR and Camera Calibration Using Motions Estimated by Sensor Fusion Odometry, 2018](https://arxiv.org/pdf/1804.05178.pdf)|C: motion (ICP),  L: motion (VO) | hand-eye calibration | * | * | 未开源 |

### 2.2. Scene-based methods
#### 2.2.1. Traditional methods
|Paper|Feature|Optimization|Toolbox|Note| Achievability | 
| --- | --- | --- | --- | --- | --- |
|[Automatic Targetless Extrinsic Calibration of a 3D Lidar and Camera by Maximizing Mutual Information, 2012](http://robots.engin.umich.edu/publications/gpandey-2012a.pdf)|C：grayscale, L: reflectivity| mutual information, BB steepest gradient ascent | [Extrinsic Calib](http://robots.engin.umich.edu/SoftwareData/ExtrinsicCalib)|*|  开源网页失效 | 
|[Automatic Calibration of Lidar and Camera Images using Normalized Mutual Information, 2013](http://www-personal.acfr.usyd.edu.au/jnieto/Publications_files/TaylorICRA2013.pdf)|C:grayscale, L: reflectivity, noraml | normalized MI, particle swarm | * | * | 未开源 |
|[Automatic Online Calibration of Cameras and Lasers, 2013](http://www.roboticsproceedings.org/rss09/p29.pdf)|C: Canny edge, L: depth-discontinuous edge| correlation, grid search | * | * | 未开源 |
|[SOIC: Semantic Online Initialization and Calibration for LiDAR and Camera, 2020](https://arxiv.org/pdf/2003.04260)|semantic centroid| PnP|*|*| 未开源 | 
|[A Low-cost and Accurate Lidar-assisted Visual SLAM System, 2021](http://www.zywok.com:20441/index.php/s/xEqCafR6dEp4REZ)|C: edge(grayscale), L: edge (reflectivity, depth projection) | ICP,  coordinate descent algorithms | [CamVox](https://github.com/ISEE-Technology/CamVox) |*| 
|[Pixel-level Extrinsic Self Calibration of High Resolution LiDAR and Camera in Targetless Environments,2021](http://arxiv.org/abs/2103.01627)|C:Canny edge(grayscale), L: depth-continuous edge|point-to-line, Gaussian-Newton|[livox_camera_calib](https://github.com/hku-mars/livox_camera_calib)|*|
|[CRLF: Automatic Calibration and Refinement based on Line Feature for LiDAR and Camera in Road Scenes, 2021](https://arxiv.org/pdf/2103.04558v1.pdf)|C:straight line, L: straight line | perspective3-lines (P3L) | * | [CN](https://cloud.tencent.com/developer/article/1805735) |
|[Fast and Accurate Extrinsic Calibration for Multiple LiDARs and Cameras,2021](https://arxiv.org/pdf/2109.06550.pdf)|C:Canny edge(grayscale), L: depth-continuous edge|point-to-plane, point-to-edge|[mlcc](https://github.com/hku-mars/mlcc)|*|
|[General, Single-shot, Target-less, and Automatic LiDAR-Camera Extrinsic Calibration Toolbox,ICRA 2023](https://arxiv.org/pdf/2302.05094.pdf)|C:keypoints, L: keypoints on intensity images (by SuperGlue)|reprojection error minimization, RANSAC|[direct_visual_lidar_calibration](https://github.com/koide3/direct_visual_lidar_calibration)|*|

#### 2.2.2. Deep-learning methods
|Paper|Toolbox|Note| Achievability |  
| --- | --- | --- | --- |
|[RegNet: Multimodal sensor registration using deep neural networks, 2017,IV](https://arxiv.org/pdf/1707.03167.pdf)|[regnet](https://github.com/aaronlws95/regnet)|*| 还没完全开源，代码运行流程都不全 |
|[CalibNet: Geometrically supervised extrinsic calibration using 3d spatial transformer networks,2018,IROS](https://arxiv.org/pdf/1803.08181.pdf)|[CalibNet](https://github.com/epiception/CalibNet)|*| github不是这个方法的使用流程toolbox，而是怎么去训练这个方法的解释 |
|[LCCNet: Lidar and Camera Self-Calibration using CostVolume Network,2021,CVPRW](https://openaccess.thecvf.com/content/CVPR2021W/WAD/papers/Lv_LCCNet_LiDAR_and_Camera_Self-Calibration_Using_Cost_Volume_Network_CVPRW_2021_paper.pdf)|[LCCNet](https://github.com/IIPCVLAB/LCCNet)|*| github不是这个方法的使用流程toolbox，而是怎么去训练这个方法的解释 |

## 3. Other toolboxes
|Toolbox|Introduction|Note|
| --- | --- | --- |
|[Apollo sensor calibration tools](https://github.com/ApolloAuto/apollo/blob/master/docs/quickstart/apollo_2_0_sensor_calibration_guide.md)|targetless method, no source code | [CN](https://blog.csdn.net/learning_tortosie/article/details/82351553?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_baidulandingword-0&spm=1001.2101.3001.4242)|
|[Autoware camera lidar calibrator](https://github.com/Autoware-AI/utilities/tree/master/autoware_camera_lidar_calibrator)|pick points mannually, PnP|*|
|[Autoware calibration camera lidar](https://github.com/XidianLemon/calibration_camera_lidar)| checkerboard, similar to [LCCT](http://www.cs.cmu.edu/~ranjith/lcct.html) |[CN](https://adamshan.blog.csdn.net/article/details/81670732)|
|[livox_camera_lidar_calibration](https://github.com/Livox-SDK/livox_camera_lidar_calibration)|pick points mannually, PnP| *|
|[OpenCalib](https://github.com/PJLab-ADG/SensorsCalibration)|target-based, target-less, mannual|OpenCalib: A Multi-sensor Calibration Toolbox for Autonomous Driving|
|[tier4/CalibrationTools](https://github.com/tier4/CalibrationTools)|target-based, mannual|*|

