---
title: "Informaci&#243;n general de Visual Studio Library | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio Library, información general"
ms.assetid: 48910975-7202-462f-a656-de67a4f8b14d
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Informaci&#243;n general de Visual Studio Library
La biblioteca de Visual Studio es un conjunto de clases de C\+\+ basadas en plantillas para simplificar la creación de VSPackages en C\+\+ nativo.  La biblioteca de Visual Studio incluye código fuente completo, como un conjunto de archivos de encabezado de C\+\+.  Los archivos de encabezado se instalan en *ruta de instalación de Visual Studio SDK*\\VisualStudioIntegration \\Common\\Source\\CPP\\VSL\\Include \\.  
  
> [!NOTE]
>  La biblioteca de Visual Studio se basa en Active \(ATL\) Template Library para su compatibilidad con objetos COM.  Para obtener más información, vea [Introducción a ATL](/visual-cpp/atl/introduction-to-atl).  
  
 La biblioteca de Visual Studio admite las pruebas unitarias, para el código y para el código.  Algunas pruebas unitarias se incluyen, como sigue:  
  
-   Las pruebas unitarias de la biblioteca de Visual Studio se instalan en *ruta de instalación de Visual Studio SDK*\\VisualStudioIntegration\\Common\\Source\\CPP\\VSL\\UnitTest \\.  
  
-   Las clases base para las pruebas unitarias para código están en *ruta de instalación de Visual Studio SDK*\\VisualStudioIntegration\\Common\\Source\\CPP\\VSL\\Include\\VSLUnitTest .h.  
  
 Las implementaciones falsas de COM de uso general y las interfaces de Visual Studio están en los archivos de encabezado, VSLMockSystemInterfaces.h y VSLMockVisualStudioInterfaces.h, que se instalan en *ruta de instalación de Visual Studio SDK*\\VisualStudioIntegration\\Common\\Source\\CPP\\VSL\\Include \\.  
  
## Vea también  
 [Desarrollo de VSPackages mediante la Visual Studio Library](../misc/developing-vspackages-by-using-the-visual-studio-library.md)