---
title: "M&#233;todos de captura de diagn&#243;stico de gr&#225;ficos | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea21995d-0241-412e-8f62-600c3794247f
caps.latest.revision: 2
caps.handback.revision: 2
ms.author: "mithom"
manager: "douge"
---
# M&#233;todos de captura de diagn&#243;stico de gr&#225;ficos
Inserte aquí la introducción.  
  
## Métodos de captura  
 En [!INCLUDE[win81](../debugger/includes/win81_md.md)], el tiempo de ejecución de DirectX 11.2 puede capturar información de gráficos internamente en nombre de herramientas de depuración, como diagnóstico de gráficos. Es lo que se conoce como *captura robusta*.  Antes de añadir esta compatibilidad al tiempo de ejecución de DirectX, la información de gráficos se capturaba interceptando determinadas llamadas de función para registrar argumentos y otra información antes de reenviar las llamadas a DirectX para completarlas. Es lo que se llama *captura heredada*.  
  
 Como el tiempo de ejecución de DirectX tiene la responsabilidad exclusiva de capturar información de gráficos en [!INCLUDE[win81](../debugger/includes/win81_md.md)], no es necesario actualizar la captura heredada para que sea compatible con DirectX 11.2 y, por lo tanto, la captura heredada está en desuso.  Sin embargo, como el tiempo de ejecución de DirectX 11.2 no es compatible con versiones de Windows anteriores a [!INCLUDE[win81](../debugger/includes/win81_md.md)], [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] todavía admite la captura heredada para aplicaciones que tienen como destino [!INCLUDE[win8](../debugger/includes/win8_md.md)] y [!INCLUDE[win7](../debugger/includes/win7_md.md)].  
  
 Ambos métodos registran información parecida y no cambian cómo se captura la información de gráficos o se utilizan las herramientas de Diagnóstico de gráficos.  
  
### Captura robusta  
 La captura robusta es compatible con el diagnóstico de gráficos de [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] en [!INCLUDE[win81](../debugger/includes/win81_md.md)], [!INCLUDE[winblue_winrt_2](../debugger/includes/winblue_winrt_2_md.md)] y Windows Phone 8.1.  Es compatible con DirectX 10.0 mediante DirectX 11.2 y puede capturar información de gráficos sobre las nuevas características de Direct3D 11.2, por ejemplo, recursos en mosaico.  No obstante, no es totalmente compatible con todas las características de Direct3D 11.2, por ejemplo, no puede depurar un sombreador HLSL que se creó utilizando la característica de vinculación del sombreador HLSL.  La captura robusta utiliza una nueva API de captura para ser compatible con sus escenarios de captura mediante programación.  
  
### Captura heredada  
 La captura heredada es compatible con el diagnóstico de gráficos de [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] y [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] en [!INCLUDE[win8](../debugger/includes/win8_md.md)], Windows RT 8 y [!INCLUDE[win7](../debugger/includes/win7_md.md)].  Es compatible con DirectX 10.0 mediante DirectX 11.1.  La captura heredada no es compatible con ninguna característica de Direct3D 11.2 y está en desuso, excepto para los escenarios en los que la captura robusta no está disponible.  La captura heredada utiliza la API de captura definida en el archivo de encabezado `vsgcapture.h` para ser compatible con sus escenarios de captura mediante programación.  Este tipo de captura mediante programación también está en desuso, excepto para los escenarios en los que no está disponible la captura robusta.  
  
## Vea también  
 [Capturar información de gráficos](../debugger/capturing-graphics-information.md)   
 [Tutorial: Capturar información de gráficos](../debugger/walkthrough-capturing-graphics-information.md)