---
title: "C&#243;mo: Cambiar el directorio de resultados de compilaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "directorio de resultados, cambiar"
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# C&#243;mo: Cambiar el directorio de resultados de compilaci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede especificar la ubicación de salida por configuración \(para debug, release o ambos\) generada por el proyecto.  
  
> [!NOTE]
>  Si tiene un proyecto **Setup**, vea la nota que se proporciona al final de este artículo.  
  
## Cambiar el directorio de salida de la compilación  
  
#### Para cambiar el directorio de salida de compilación  
  
1.  En la barra de menús, elija **Proyecto**, *NombreDeAplicación***Propiedades**. En el **Explorador de soluciones**, también puede hacer clic con el botón secundario en el nodo del proyecto y seleccionar **Propiedades**.  
  
2.  Si tiene un proyecto de Visual Basic, seleccione la pestaña **Compilar**. Si tiene un proyecto de Visual C\#, seleccione la pestaña **Compilar**. Si tiene un proyecto de C\+\+ o JavaScript, seleccione la pestaña **General**.  
  
3.  En la lista desplegable de configuración de la parte superior, elija la configuración cuya ubicación de archivo de resultados desea cambiar \(debug, release o todas\).  
  
     Busque la entrada de la ruta de acceso de los resultados \(**Ruta de acceso de los resultados de la compilación** en Visual Basic, **Directorio de resultados** en Visual C\+\+ y **Ruta de acceso de los resultados** en JavaScript y C\#\). Especifique un nuevo directorio de resultados de la compilación relativo al directorio del proyecto.  
  
> [!NOTE]
>  En un proyecto Setup, el cuadro **Nombre del archivo de salida** cambia solo la ubicación del archivo Setup.exe, no la ubicación de los archivos del proyecto. Para obtener más información, vea **Compilación, Propiedades de configuración, Propiedades del proyecto de implementación \(cuadro de diálogo\)**.  
  
## Vea también  
 [Compilar \(Página, Diseñador de proyectos\) \(C\#\)](../ide/reference/build-page-project-designer-csharp.md)   
 [Página de propiedades General \(Proyecto\)](/visual-cpp/ide/general-property-page-project)   
 [Compilar aplicaciones en Visual Studio](../ide/compiling-and-building-in-visual-studio.md)