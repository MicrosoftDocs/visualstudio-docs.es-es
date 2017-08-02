---
title: "Modelo de proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "automatización [Visual Studio SDK], implementar objetos de proyecto"
  - "modelos de proyecto de automatización"
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Modelo de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El siguiente paso para proporcionar la automatización para el proyecto es implementar objetos estándar del proyecto: las colecciones de <xref:EnvDTE.Projects> y de `ProjectItems` ; los objetos de `Project` y de <xref:EnvDTE.ProjectItem> ; y los objetos restantes únicos para la implementación.  Estos objetos estándar se definen en el archivo de Dteinternal.h.  Una implementación de los objetos estándar se proporciona en el ejemplo de BscPrj.  Puede utilizar estas clases mientras los modelos para crear dispone los objetos estándar de proyecto que se colocan en paralelo con los objetos del proyecto de otros tipos de proyecto.  
  
 Un consumidor de automatización supone pueda llamar a <xref:EnvDTE.Solution>\(“`<UniqueProjName>")`y <xref:EnvDTE.ProjectItems> \(`n`\) donde es un número de índice n para obtener un proyecto concreto de la solución.  Crear esta llamada de automatización hace el entorno para llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> en la jerarquía de proyecto adecuada, pasando VSITEMID\_ROOT como parámetro de ItemID y VSHPROPID\_ExtObject como parámetro de VSHPROPID.  `IVsHierarchy::GetProperty` devuelve un puntero de `IDispatch` al objeto de automatización que proporciona la interfaz básica de `Project` , implementada.  
  
 A continuación se muestra la sintaxis de `IVsHierarchy::GetProperty`.  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 Los proyectos alojan el anidamiento y utilizan colecciones para crear grupos de elementos de proyecto.  La jerarquía esta apariencia.  
  
```  
Projects  
  |– Project  
      |– ProjectItems (a collection of ProjectItem)  
          |– ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 El anidamiento significa que un objeto de <xref:EnvDTE.ProjectItem> puede ser colección de <xref:EnvDTE.ProjectItems> al mismo tiempo porque una colección de `ProjectItems` puede contener objetos anidados.  El ejemplo básico del proyecto no muestra este anidamiento.  Implementa el objeto de `Project` , combina en similar la estructura que caracteriza el diseño del modelo de automatización general.  
  
 La automatización de proyectos sigue la ruta en el diagrama siguiente.  
  
 ![Objetos de proyectos de Visual Studio](~/docs/extensibility/internals/media/projectobjects.gif "ProjectObjects")  
Automatización de proyectos  
  
 Si no implementa un objeto de `Project` , el entorno seguirá devolviendo un objeto genérico de `Project` que sólo contiene el nombre del proyecto.  
  
## Vea también  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>