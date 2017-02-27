---
title: "C&#243;mo: Crear y quitar dependencias del proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ProjectDependenciesDlg"
helpviewer_keywords: 
  - "compilaciones [Visual Studio], configurar"
  - "dependencias, proyecto"
  - "configuraciones de compilación del proyecto, dependencias"
  - "dependencias del proyecto"
  - "proyectos [Visual Studio], dependencias"
  - "vs.build.projectdependencies"
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# C&#243;mo: Crear y quitar dependencias del proyecto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando se compila una solución que contiene varios proyectos, a veces es necesario compilar primero algunos proyectos, para generar el código que utilizan otros proyectos.  Cuando un proyecto utiliza código ejecutable generado por otro proyecto, se hace referencia al proyecto que genera el código como una dependencia de proyecto del proyecto que utiliza el código.  Tales relaciones de dependencia pueden definirse en el cuadro de diálogo de **Dependencias del proyecto** .  
  
### Para asignar dependencias a proyectos  
  
1.  En el Explorador de soluciones, seleccione un proyecto.  
  
2.  En el menú **Proyecto**, elija **Dependencias del proyecto**.  
  
     Se abrirá el cuadro de diálogo **Dependencias del proyecto**.  
  
    > [!NOTE]
    >  La opción **Dependencias del proyecto** sólo está disponible en las soluciones con más de un proyecto.  
  
3.  En la ficha **Dependencias**, seleccione un proyecto en el menú desplegable **Proyecto**.  
  
4.  En el campo **Depende de**, active la casilla de todos los proyectos que deben compilarse antes que el actual.  
  
 Para poder crear dependencias de proyecto, la solución debe estar compuesta por más de un proyecto.  
  
### Para quitar dependencias de proyectos  
  
1.  En el Explorador de soluciones, seleccione un proyecto.  
  
2.  En el menú **Proyecto**, elija **Dependencias del proyecto**.  
  
     Se abrirá el cuadro de diálogo **Dependencias del proyecto**.  
  
    > [!NOTE]
    >  La opción **Dependencias del proyecto** sólo está disponible en las soluciones con más de un proyecto.  
  
3.  En la ficha **Dependencias**, seleccione un proyecto del menú desplegable **Proyecto**.  
  
4.  En el campo **Depende de**, desactive las casillas de todos los proyectos que ya no mantienen relaciones de dependencia con el proyecto actual.  
  
## Vea también  
 [Compilar y limpiar proyectos y soluciones en Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Compilar aplicaciones en Visual Studio](../ide/compiling-and-building-in-visual-studio.md)   
 [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md)   
 [Cómo: Modificar las propiedades y los valores de configuración del proyecto](http://msdn.microsoft.com/es-es/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)