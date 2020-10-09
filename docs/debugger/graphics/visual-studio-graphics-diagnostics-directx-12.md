---
title: Compatibilidad de DirectX 12 con Visual Studio | Microsoft Docs
description: Se recomienda a los usuarios de DirectX 12 usar PIX en Windows para obtener una experiencia de depuración gráfica completa.
ms.date: 09/29/2020
ms.topic: conceptual
author: davidcongruili
ms.author: davidli1
manager: mluparu
ms.workload:
- multiple
ms.openlocfilehash: 9dbc52a0233abe467da4d41af0134663bc7cd9df
ms.sourcegitcommit: a1cb4e2025045c2ad79167645c4c0f33b94b1152
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2020
ms.locfileid: "91671421"
---
# <a name="directx-12-support-in-visual-studio"></a>Compatibilidad de DirectX 12 con Visual Studio

## <a name="directx-12-support"></a>Compatibilidad de DirectX 12

El diagnóstico de gráficos de Visual Studio no es compatible con los juegos de DirectX 12. Para la depuración gráfica con compatibilidad completa con DirectX 12, Visual Studio recomienda *PIX en Windows*. 

PIX en Windows es una herramienta de optimización y depuración del rendimiento con capacidades remotas. PIX en Windows ofrece siete características principales que se adaptan a sus necesidades de depuración gráfica. Depure y analice el rendimiento de la representación de gráficos de Direct3D 12 con capturas de GPU. Comprenda el rendimiento y los subprocesos de todo el trabajo de CPU y GPU realizado por el juego con capturas de tiempo. Identifique las ineficiencias en los patrones de E/S de disco del título y el diseño del paquete con capturas de E/S de los archivos.

Continúe el recorrido de depuración gráfica con [**PIX en Windows**](https://aka.ms/PIXonWindows).

[**Descargue PIX en Windows**](https://aka.ms/downloadPIX) o [**vea la documentación**.](https://devblogs.microsoft.com/pix/documentation/)

## <a name="pix-on-windows"></a>PIX en Windows

PIX en Windows incluye siete modos principales de funcionamiento:
1. **Capturas de GPU** para la depuración y análisis del rendimiento de la representación de gráficos de Direct3D 12.
2. **Capturas de tiempo** para comprender el rendimiento y los subprocesos de todo el trabajo de CPU y GPU realizado por el juego y para realizar un seguimiento del uso de memoria de GPU.
3. **Las capturas de resúmenes de funciones** acumulan información sobre cuánto tiempo se ejecuta cada función y con qué frecuencia se llama a cada una de ellas.
4. **Las capturas de gráficos** realizan un seguimiento de la ejecución de una única función.
5. **Las capturas de asignación de memoria** proporcionan una visión general de las asignaciones de memoria realizadas por el juego.
6. **Las capturas de E/S de los archivos** identifican las ineficiencias en los patrones de E/S de disco del título y el diseño del paquete.
7. **El monitor del sistema** muestra datos del contador en tiempo real mientras se ejecuta un juego.

[**Aquí**](https://www.youtube.com/playlist?list=PLeHvwXyqearWuPPxh6T03iwX-McPG5LkB) tiene un vídeo detallado de introducción a PIX en Windows.
