---
title: Análisis del uso de memoria en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8971f26881e522c81f2c111098f09a94133072d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948920"
---
# <a name="analyze-memory-usage"></a>Analizar el uso de memoria
Utilice la herramienta de diagnóstico **Uso de memoria** con depurador integrado para buscar usos ineficaces y fugas de memoria. La herramienta Uso de memoria permite tomar una o más *instantáneas* del montón de memoria nativo y administrado. Puede recopilar instantáneas de aplicaciones .NET, ASP.NET, nativas o de modo mixto (.NET y nativas).  
  
-   Puede analizar una sola instantánea para entender el impacto relativo de los tipos de objeto en el uso de la memoria y buscar código en la aplicación que use la memoria de forma ineficaz.  
  
-   También puede comparar (diff) dos instantáneas de una aplicación para buscar las áreas del código que generen un aumento del uso de la memoria con el tiempo.  

Para obtener instrucciones detalladas, vea el tutorial [Análisis del uso de memoria](../profiling/memory-usage.md).  Actualmente, para medir el uso de memoria de una aplicación .NET Core, debe usar la herramienta con el depurador adjunto. Para otras aplicaciones administradas y nativas, puede usar la herramienta ya sea con o sin el depurador adjunto.

Las herramientas de generación de perfiles se pueden usar sin el depurador en Windows 7 y versiones posteriores. Para ejecutar las herramientas de generación de perfiles con el depurador se requiere Windows 8 y versiones posteriores (ventana **Herramientas de diagnóstico**).
  
## <a name="blogs-and-videos"></a>Blogs y vídeos  

| | |
|---------|---------|
| ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo") | [Vea un vídeo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171) sobre cómo utilizar las herramientas de diagnóstico en el que se muestra cómo analizar el uso de CPU y de memoria en Visual Studio 2017. |

 [Analyze CPU and Memory While Debugging](https://blogs.msdn.microsoft.com/visualstudio/2016/02/15/analyze-cpu-memory-while-debugging/) (Análisis de la CPU y la memoria durante la depuración)  
  
 [Visual C++ Blog: Memory Profiling in Visual C++ 2015](https://blogs.msdn.microsoft.com/vcblog/2015/10/21/memory-profiling-in-visual-c-2015/) (Blog de Visual C++: Generación de perfiles de memoria en Visual C++ 2015)  

## <a name="see-also"></a>Vea también
 [Generación de perfiles en Visual Studio](../profiling/index.md)  
 [Primer vistazo a la generación de perfiles](../profiling/profiling-feature-tour.md)