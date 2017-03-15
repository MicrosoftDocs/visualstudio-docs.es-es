---
title: "Versi&#243;n de .NET Framework de destino del proyecto no instalada (Cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.TargetFrameworkNotFound"
ms.assetid: 64ce8743-d5bd-447e-ba10-54b2aafe109e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Versi&#243;n de .NET Framework de destino del proyecto no instalada (Cuadro de di&#225;logo)
Ha abierto un proyecto que tiene como destino un marco que no está instalado en el equipo. Para continuar, debe seleccionar una de las opciones de este cuadro de diálogo.  
  
> [!NOTE]
>  Siempre que descargue e instale un nuevo marco, debe reiniciar Visual Studio.  
  
## Visual Basic y Visual C\#  
 Si abre un proyecto de Visual Basic o Visual C\#, seleccione una de las siguientes opciones.  
  
 **Cambie el destino a .NET Framework 4.5. Puede volver a cambiar a .NET Framework***versión* **más adelante.**  
 Cambia el destino de su proyecto a .NET Framework 4.5. Más adelante puede volver a instalar la versión anterior y cambiar el destino del proyecto.  
  
 **Descargue el paquete de destino para .NET Framework \<versión\>. El proyecto no cambiará.**  
 Abre el sitio web del Centro de descarga de Microsoft, donde puede descargar la versión de .NET Framework que desee. El proyecto se descarga de la solución. Después de descargar e instalar el marco deseado, debe reiniciar Visual Studio y, a continuación, volver a abrir el proyecto.  
  
 **No cargar el proyecto.**  
 No descarga el proyecto de la solución. Más adelante podrá instalar el marco deseado y volver a cargar el proyecto.  
  
## Visual C\+\+  
 Si abre un proyecto de Visual C\#, seleccione una de las siguientes opciones.  
  
 **Descargue el paquete de destino para .NET Framework** *versión* **. El proyecto no cambiará.**  
 Abre el sitio web del Centro de descarga de Microsoft, donde puede descargar la versión de .NET Framework que desee. Una vez finalizada la descarga, el proyecto vuelve a destinarse a esa versión. El proyecto se descarga de la solución. Después de descargar e instalar el marco deseado, debe reiniciar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y, a continuación, volver a abrir el proyecto.  
  
 **No cargar el proyecto.**  
 No descarga el proyecto de la solución. Más adelante podrá instalar el marco deseado y volver a cargar el proyecto.  
  
## Vea también  
 [Cómo: Usar como destino una versión de .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Solucionar problemas de versión de .NET Framework de destino](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [Agregar referencias](/visual-cpp/ide/adding-references-in-visual-cpp-projects)