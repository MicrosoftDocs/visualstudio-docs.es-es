---
title: "C&#243;mo: Administrar configuraciones de compilaci&#243;n a las que se han aplicado opciones del desarrollador de Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuraciones de compilación avanzadas"
  - "compilar con opciones del desarrollador de Visual Basic"
  - "compilaciones de depuración"
  - "MSBuild, versión de depuración"
  - "MSBuild, versión de lanzamiento"
  - "versiones de lanzamiento"
  - "Visual Studio, compilar con opciones de Visual Basic"
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Administrar configuraciones de compilaci&#243;n a las que se han aplicado opciones del desarrollador de Visual Basic
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

De manera predeterminada, todas las opciones de configuración de compilación avanzadas se ocultan si se aplica la configuración de desarrollador de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  En este tema se explica cómo habilitar manualmente esta configuración.  
  
## Habilitar configuraciones de compilación avanzadas  
 De forma predeterminada, la configuración de desarrollador de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] oculta la opción para abrir el cuadro de diálogo **Administrador de configuración** y las listas **Configuración** y **Plataforma** del [Diseñador de proyectos](http://msdn.microsoft.com/es-es/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
#### Para habilitar las configuraciones de compilación avanzadas  
  
1.  En el menú **Herramientas**, haga clic en **Opciones**.  
  
2.  Expanda **Proyectos y soluciones** y haga clic en **General**.  
  
    > [!NOTE]
    >  El nodo **General** es visible incluso si está desactivada la opción **Mostrar todas las configuraciones**.  Si desea ver cada opción disponible, haga clic en **Mostrar todas las configuraciones**.  
  
3.  Haga clic en **Mostrar configuraciones de compilación avanzadas**.  
  
4.  Haga clic en **Aceptar**.  
  
     En el menú **Compilar**, ahora está disponible el **Administrador de configuración** y las listas **Configuración** y **Plataforma** están visibles en el Diseñador de proyectos.  
  
## Vea también  
 [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md)   
 [Compilar aplicaciones en Visual Studio](../ide/compiling-and-building-in-visual-studio.md)