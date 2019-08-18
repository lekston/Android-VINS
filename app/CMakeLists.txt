# Sets the minimum version of CMake required to build the native
# library. You should either keep the default value or only pass a
# value of 3.4.0 or lower.

#工程路径
#OpenCV-android-sdk路径
#set(pathToOpenCv /opt/local)
set(pathToProject /opt/01.src/AndroidStudioProjects/Android-VINS)
set(boostForAndroid /opt/02.installs/Boost-for-Android/pre-build/boost_1.69.0_prebuilt_ndk_19c)
set(pathToOpenCV /opt/01.src/Android/OpenCV-android-sdk/)

#CMake版本信息
cmake_minimum_required(VERSION 3.4.1)
#支持-std=gnu++11
set(CMAKE_VERBOSE_MAKEFILE on)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=gnu++11 -lz -static-libstdc++")

#配置加载native依赖
include_directories(${pathToProject}/app/src/main/cpp/include/opencv)

include_directories(${pathToProject}/app/src/main/cpp/include/CL)
include_directories(${pathToProject}/app/src/main/cpp/include/eigen3)
include_directories(${pathToProject}/app/src/main/cpp/include/)
include_directories(${boostForAndroid}/include/)

include_directories(${pathToProject}/app/src/main/cpp/include/ceres-solver/include)
include_directories(${pathToProject}/app/src/main/cpp/include/ceres-solver/internal)
include_directories(${pathToProject}/app/src/main/cpp/include/ceres-solver/internal/ceres/miniglog)
include_directories(${pathToProject}/app/src/main/cpp/include/ceres-solver/config)
include_directories(${pathToProject}/app/src/main/cpp/src/camera_model/include)

#静态方式加载
add_library( lib-std-cpp STATIC IMPORTED )
set_target_properties( lib-std-cpp PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libstdc++.a)
add_library( lib-std-cpp-shared SHARED IMPORTED )
set_target_properties( lib-std-cpp-shared PROPERTIES IMPORTED_LOCATION /opt/android/android-ndk-r19b/toolchains/llvm/prebuilt/linux-x86_64/sysroot/usr/lib/aarch64-linux-android/28/libstdc++.so)

add_library( lib-cpp-static STATIC IMPORTED )
set_target_properties( lib-cpp-static PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libc++_static.a)
add_library( lib-c STATIC IMPORTED )
set_target_properties( lib-c PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libc.a)
add_library( lib-m STATIC IMPORTED )
set_target_properties( lib-m PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libm.a)
add_library( lib-z STATIC IMPORTED )
set_target_properties( lib-z PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libz.a)
add_library( lib-dl STATIC IMPORTED )
set_target_properties( lib-dl PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libdl.a)

# openCV
add_library( lib_opencv_calib3d STATIC IMPORTED )
set_target_properties(lib_opencv_calib3d PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libopencv_calib3d.a)

add_library( lib_opencv_core STATIC IMPORTED )
set_target_properties(lib_opencv_core PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libopencv_core.a)

add_library( lib_opencv_features2d STATIC IMPORTED )
set_target_properties(lib_opencv_features2d PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libopencv_features2d.a)

add_library( lib_opencv_flann STATIC IMPORTED )
set_target_properties(lib_opencv_flann PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libopencv_flann.a)

add_library( lib_opencv_highgui STATIC IMPORTED )
set_target_properties(lib_opencv_highgui PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libopencv_highgui.a)

add_library( lib_opencv_imgcodecs STATIC IMPORTED )
set_target_properties(lib_opencv_imgcodecs PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libopencv_imgcodecs.a)

add_library( lib_opencv_imgproc STATIC IMPORTED )
set_target_properties(lib_opencv_imgproc PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libopencv_imgproc.a)

add_library( lib_opencv_ml STATIC IMPORTED )
set_target_properties(lib_opencv_ml PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libopencv_ml.a)

add_library( lib_opencv_objdetect STATIC IMPORTED )
set_target_properties(lib_opencv_objdetect PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libopencv_objdetect.a)

add_library( lib_opencv_photo STATIC IMPORTED )
set_target_properties(lib_opencv_photo PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libopencv_photo.a)

add_library( lib_opencv_shape STATIC IMPORTED )
set_target_properties(lib_opencv_shape PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libopencv_shape.a)

add_library( lib_opencv_stitching STATIC IMPORTED )
set_target_properties(lib_opencv_stitching PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libopencv_stitching.a)

add_library( lib_opencv_superres STATIC IMPORTED )
set_target_properties(lib_opencv_superres PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libopencv_superres.a)

add_library( lib_opencv_ts STATIC IMPORTED )
set_target_properties(lib_opencv_ts PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libopencv_ts.a)

add_library( lib_opencv_video STATIC IMPORTED )
set_target_properties(lib_opencv_video PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libopencv_video.a)

add_library( lib_opencv_videoio STATIC IMPORTED )
set_target_properties(lib_opencv_videoio PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libopencv_videoio.a)

add_library( lib_opencv_videostab STATIC IMPORTED )
set_target_properties(lib_opencv_videostab PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libopencv_videostab.a)

add_library( lib_tbb STATIC IMPORTED )
set_target_properties(lib_tbb PROPERTIES IMPORTED_LOCATION ${pathToOpenCV}/sdk/native/3rdparty/libs/${ANDROID_ABI}/libtbb.a)

add_library( lib_IlmImf STATIC IMPORTED )
set_target_properties(lib_IlmImf PROPERTIES IMPORTED_LOCATION ${pathToOpenCV}/sdk/native/3rdparty/libs/${ANDROID_ABI}/libIlmImf.a)

add_library( lib_libjasper STATIC IMPORTED )
set_target_properties(lib_libjasper PROPERTIES IMPORTED_LOCATION ${pathToOpenCV}/sdk/native/3rdparty/libs/${ANDROID_ABI}/liblibjasper.a)

#add_library( lib_libjpeg STATIC IMPORTED )
#set_target_properties(lib_libjpeg PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/liblibjpeg.a)

add_library( lib_libpng STATIC IMPORTED )
set_target_properties(lib_libpng PROPERTIES IMPORTED_LOCATION ${pathToOpenCV}/sdk/native/3rdparty/libs/${ANDROID_ABI}/liblibpng.a)

add_library( lib_libtiff STATIC IMPORTED )
set_target_properties(lib_libtiff PROPERTIES IMPORTED_LOCATION ${pathToOpenCV}/sdk/native/3rdparty/libs/${ANDROID_ABI}/liblibtiff.a)

add_library( lib_libwebp STATIC IMPORTED )
set_target_properties(lib_libwebp PROPERTIES IMPORTED_LOCATION ${pathToOpenCV}/sdk/native/3rdparty/libs/${ANDROID_ABI}/liblibwebp.a)

add_library( opencv SHARED IMPORTED )
set_target_properties(opencv PROPERTIES IMPORTED_LOCATION ${pathToProject}/app/src/main/jniLibs/${ANDROID_ABI}/libopencv_java3.so)

#add_library(OpenCL SHARED IMPORTED)
#set_target_properties(OpenCL PROPERTIES IMPORTED_LOCATION ${CMAKE_SOURCE_DIR}/src/main/jniLibs/${ANDROID_ABI}/libOpenCL.so)

add_library(lib-ceres STATIC IMPORTED)
set_target_properties(lib-ceres PROPERTIES IMPORTED_LOCATION ${CMAKE_SOURCE_DIR}/src/main/jniLibs/${ANDROID_ABI}/libceres.a)

add_library(lib-boost-filesystem STATIC IMPORTED)
set_target_properties(lib-boost-filesystem PROPERTIES IMPORTED_LOCATION ${boostForAndroid}/libs/llvm/${ANDROID_ABI}/libboost_filesystem.a)

add_library(lib-boost-system STATIC IMPORTED)
set_target_properties(lib-boost-system PROPERTIES IMPORTED_LOCATION ${boostForAndroid}/libs/llvm/${ANDROID_ABI}/libboost_system.a)

add_library(lib-boost-program-options STATIC IMPORTED)
set_target_properties(lib-boost-program-options PROPERTIES IMPORTED_LOCATION ${boostForAndroid}/libs/llvm/${ANDROID_ABI}/libboost_program_options.a)
#find_package(ceres REQUIRED)

#C++日志
find_library( log-lib log )

#CPP文件夹下带编译的cpp文件
add_library( native-lib SHARED src/main/cpp/native-lib.cpp
    src/main/cpp/src/vins_estimator/src/estimator_node.cpp
    src/main/cpp/src/vins_estimator/src/parameters.cpp
    src/main/cpp/src/vins_estimator/src/estimator.cpp
    src/main/cpp/src/vins_estimator/src/feature_manager.cpp
    src/main/cpp/src/vins_estimator/src/factor/pose_local_parameterization.cpp
    src/main/cpp/src/vins_estimator/src/factor/projection_factor.cpp
    src/main/cpp/src/vins_estimator/src/factor/marginalization_factor.cpp
    src/main/cpp/src/vins_estimator/src/utility/utility.cpp
    src/main/cpp/src/vins_estimator/src/utility/visualization.cpp
    src/main/cpp/src/vins_estimator/src/initial/solve_5pts.cpp
    src/main/cpp/src/vins_estimator/src/initial/initial_aligment.cpp
    src/main/cpp/src/vins_estimator/src/initial/initial_sfm.cpp
    src/main/cpp/src/vins_estimator/src/initial/initial_ex_rotation.cpp
    src/main/cpp/src/vins_estimator/src/loop-closure/ThirdParty/DBoW/BowVector.cpp
    src/main/cpp/src/vins_estimator/src/loop-closure/ThirdParty/DBoW/FBrief.cpp
    src/main/cpp/src/vins_estimator/src/loop-closure/ThirdParty/DBoW/FeatureVector.cpp
    src/main/cpp/src/vins_estimator/src/loop-closure/ThirdParty/DBoW/QueryResults.cpp
    src/main/cpp/src/vins_estimator/src/loop-closure/ThirdParty/DBoW/ScoringObject.cpp
    src/main/cpp/src/vins_estimator/src/loop-closure/ThirdParty/DUtils/Random.cpp
    src/main/cpp/src/vins_estimator/src/loop-closure/ThirdParty/DUtils/Timestamp.cpp
    src/main/cpp/src/vins_estimator/src/loop-closure/ThirdParty/DVision/BRIEF.cpp
    src/main/cpp/src/vins_estimator/src/loop-closure/ThirdParty/VocabularyBinary.cpp
    src/main/cpp/src/vins_estimator/src/loop-closure/loop_closure.cpp
    src/main/cpp/src/vins_estimator/src/loop-closure/keyframe.cpp
    src/main/cpp/src/vins_estimator/src/loop-closure/keyframe_database.cpp
    src/main/cpp/src/vins_estimator/src/feature_tracker/feature_tracker.cpp

    src/main/cpp/src/camera_model/src/chessboard/Chessboard.cc
    src/main/cpp/src/camera_model/src/calib/CameraCalibration.cc
    src/main/cpp/src/camera_model/src/camera_models/Camera.cc
    src/main/cpp/src/camera_model/src/camera_models/CameraFactory.cc
    src/main/cpp/src/camera_model/src/camera_models/CostFunctionFactory.cc
    src/main/cpp/src/camera_model/src/camera_models/PinholeCamera.cc
    src/main/cpp/src/camera_model/src/camera_models/CataCamera.cc
    src/main/cpp/src/camera_model/src/camera_models/EquidistantCamera.cc
    src/main/cpp/src/camera_model/src/camera_models/ScaramuzzaCamera.cc
    src/main/cpp/src/camera_model/src/sparse_graph/Transform.cc
    src/main/cpp/src/camera_model/src/gpl/gpl.cc
    src/main/cpp/src/camera_model/src/gpl/EigenQuaternionParameterization.cc

)
target_link_libraries( native-lib
                        opencv
                        ${log-lib}
                        lib_opencv_calib3d lib_opencv_core lib_opencv_features2d  lib_opencv_flann lib_opencv_highgui lib_opencv_imgcodecs lib_opencv_imgproc lib_opencv_ml lib_opencv_objdetect
                        lib_opencv_photo  lib_opencv_shape lib_opencv_stitching lib_opencv_superres lib_opencv_ts lib_opencv_video lib_opencv_videoio lib_opencv_videostab


                      #  OpenCL
                        lib-ceres
                        lib-boost-filesystem
                        lib-boost-program-options
                        lib-boost-system
                        lib_libjasper lib_libpng lib_libtiff lib_libwebp lib_IlmImf
                     #  lib_libjpeg lib_tbb lib-std-cpp lib-std-cpp-shared lib-c
                        lib-m lib-z lib-dl
                        lib-std-cpp-shared
        )
