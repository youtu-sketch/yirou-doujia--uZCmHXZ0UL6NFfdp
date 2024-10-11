
#### 项目介绍

YoloDotNet v2\.1 是一个基于 C\# 和 .NET 8 的实时物体检测框架，专为图像和视频中的物体检测而设计。它集成了 Yolov8 \~ Yolov11 模型，通过 ML.NET 和 ONNX 运行时实现高效的物体检测，并支持 GPU 加速（使用 CUDA）。YoloDotNet 不仅支持传统的物体检测，还涵盖了分类、OBB 检测、分割和姿态估计等多种功能，适用于各种复杂的视觉任务。

[![image](https://img2023.cnblogs.com/blog/510/202410/510-20241010214936425-577776944.png "image")](https://github.com)

#### 项目技术分析

YoloDotNet 2\.1 现已推出，比以往任何时候都更强大！此版本建立在之前的“Speed Demon”v2\.0 更新的基础上，并添加了一些令人兴奋的新功能，同时保持一切顺利。与旧版本的兼容性已得到保证，并且进行了一些调整以获得更好的对象检测性能。查看新增功能：

* **Yolov11 支持：**最新、最出色的对象检测模型的支持，为用户提供了更先进的物体检测能力。
* **Yolov9 的向后兼容性：**现在您可以在 Yolov8\-v11 版本之间切换。
* **小优化：**为了更快地检测对象，这里和那里有一些调整，速度越快越好！
* **OnnxRuntime 更新：**现在支持 CUDA 12\.x 和 cuDNN 9\.x。GPU 肯定会对这个感到满意！

YoloDotNet v2\.1 – 更快、更智能，并包含更多 Yolo 优点;

**项目及技术应用场景**

YoloDotNet v2\.1 的应用场景非常广泛，包括但不限于：

* **智能监控**：实时检测监控视频中的异常行为或物体。
* **自动驾驶**：实时识别道路上的行人、车辆和其他障碍物。
* **工业检测**：自动化检测生产线上的产品缺陷或异常。
* **医疗影像分析**：辅助医生快速识别医学影像中的病变区域。
* **体育分析**：实时分析运动员的动作和姿态，用于训练和比赛分析。

#### 项目特点

YoloDotNet v2\.1 具有以下显著特点：

* **高性能**：通过多项优化措施，YoloDotNet v2\.1 在速度和效率上达到了新的高度，尤其在 GPU 加速下表现出色。
* **多功能**：支持分类、物体检测、OBB 检测、分割和姿态估计等多种视觉任务，满足不同应用需求。
* **易用性**：提供了简洁的 API 和丰富的示例代码，方便开发者快速上手。
* **跨平台**：基于 .NET 8，支持 Windows、Linux 和 macOS 等多种操作系统。
* **开源免费**：完全开源，用户可以自由使用、修改和分发。

#### 结语

YoloDotNet v2\.1 不仅在技术上实现了重大突破，还为用户提供了强大的工具来应对各种复杂的视觉任务。无论你是开发者、研究人员还是企业用户，YoloDotNet v2\.1 都能为你提供高效、可靠的解决方案。立即体验 YoloDotNet v2\.1，开启你的智能视觉之旅！



---

**项目地址**：YoloDotNet GitHub:[https://github.com/NickSwardh/YoloDotNet](https://github.com/NickSwardh/YoloDotNet "https://github.com/NickSwardh/YoloDotNet"):[悠兔机场](https://xinnongbo.com)

**安装指南**：


```
dotnet add package YoloDotNet

```
**注意**：使用 GPU 加速需要安装 CUDA 和 cuDNN，请确保 ONNX 运行时与这些组件的兼容性。

项目的包含一个示例项目，启动文件位于 `ConsoleDemo/Program.cs`。该文件包含了项目的入口点，用于启动和运行 YoloDotNet 的控制台应用程序。

##### Program.cs 文件内容概述


```
using System;
using YoloDotNet;

namespace ConsoleDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 初始化 Yolo 对象
            var yolo = new Yolo(@"path\to\model.onnx");

            // 加载图像
            var image = Image.Load(@"path\to\image.jpg");

            // 运行对象检测
            var results = yolo.RunObjectDetection(image, confidence: 0.25, iou: 0.7);

            // 处理结果
            image.Draw(results);
            image.Save(@"path\to\save\image.jpg");
        }
    }
}

```
##### 启动文件功能

* **初始化 Yolo 对象**: 加载 ONNX 模型。
* **加载图像**: 使用 SixLabors.ImageSharp 加载图像。
* **运行对象检测**: 调用 Yolo 对象的 `RunObjectDetection` 方法进行对象检测。
* **处理结果**: 在图像上绘制检测结果并保存。

#### 3\. 项目配置文件介绍

YoloDotNet 项目没有传统的配置文件（如 `.config` 或 `.yaml` 文件），但可以通过代码中的配置选项来调整项目的行为。

##### 配置选项示例


```
var yolo = new Yolo(new YoloOptions
{
    OnnxModel = @"path\to\model.onnx",
    ModelType = ModelType.ObjectDetection,
    Cuda = true,
    GpuId = 0,
    PrimeGpu = false
});

```
##### 配置选项说明

* **OnnxModel**: 指定 ONNX 模型的路径。
* **ModelType**: 指定模型类型，如 `ObjectDetection`。
* **Cuda**: 是否启用 CUDA 加速。
* **GpuId**: 指定使用的 GPU ID。
* **PrimeGpu**: 是否预分配 GPU 内存。

通过这些配置选项，可以在代码中灵活地调整 YoloDotNet 的行为，以适应不同的应用场景。


