---
title: "C&#243;mo: Compilar varias configuraciones simult&#225;neamente | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Compilar varias configuraciones simult&#225;neamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede compilar la mayoría de los tipos de proyectos con varias o incluso todas sus configuraciones de compilación al mismo tiempo usando el cuadro de diálogo **Compilación por lotes**.   Sin embargo, no puede compilar los siguientes tipos de proyectos en varias configuraciones de compilación al mismo tiempo:  
  
1.  Aplicaciones de [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] compiladas para Windows mediante JavaScript.  
  
2.  Todos los proyectos de Visual Basic.  
  
 Para obtener más información acerca de las configuraciones de compilación, vea [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).  
  
### Para compilar un proyecto en varias configuraciones de compilación  
  
1.  En la barra de menús, elija **Compilar**, **Compilación por lotes**.  
  
2.  En la columna **Compilar**, seleccione las casillas de las configuraciones en el que desea compilar un proyecto.  
  
    > [!TIP]
    >  Para editar o crear una configuración de compilación para una solución, en la barra de menú elija **Compilar**, **Administrador de configuración** para abrir el cuadro de diálogo **Administrador de configuración**.  Después de editar una configuración de compilación para una solución, en el cuadro de diálogo **Compilación por lotes**, elija el botón **Recompilar** para actualizar todas las configuraciones para los proyectos de la solución.  
  
3.  Elija los botones **Compilar** o **Recompilar** para compilar el proyecto con las configuraciones que especificó.  
  
## Vea también  
 [Cómo: Crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md)   
 [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md)   
 [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)