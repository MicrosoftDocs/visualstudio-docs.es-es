---
title: Proyecto de modelado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d654669ad35ce77d840f4852ceb7a6605a8221be
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="project-modeling"></a>Modelado de proyecto
El siguiente paso en la provisión de automatización para el proyecto consiste en implementar los objetos de proyecto estándar: la <xref:EnvDTE.Projects> y `ProjectItems` colecciones; el `Project` y <xref:EnvDTE.ProjectItem> objetos; y los demás objetos únicos de su implementación. Estos objetos estándares se definen en el archivo Dteinternal.h. En el ejemplo BscPrj se proporciona una implementación de los objetos estándares. Puede usar estas clases como modelos para crear sus propios objetos de proyecto estándar stand en paralelo con objetos de proyectos de otros tipos de proyecto.  
  
 Un consumidor de automatización se da por supuesto que puedan llamar a <xref:EnvDTE.Solution>("`<UniqueProjName>")` y <xref:EnvDTE.ProjectItems> (`n`) donde n es un número de índice para obtener un proyecto específico de la solución. Esta llamada de automatización hace que el entorno llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> en la jerarquía del proyecto adecuado, pasando VSITEMID_ROOT como el parámetro de ItemID y VSHPROPID_ExtObject como parámetro VSHPROPID. `IVsHierarchy::GetProperty`Devuelve un `IDispatch` puntero al objeto de automatización que proporciona el núcleo `Project` interfaz que ha implementado.  
  
 La siguiente es la sintaxis de `IVsHierarchy::GetProperty`.  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 Proyectos de dar cabida a anidamiento y utilizar colecciones para crear grupos de elementos de proyecto. La jerarquía tiene el siguiente aspecto.  
  
```  
Projects  
  |- Project  
      |- ProjectItems (a collection of ProjectItem)  
          |- ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 La anidación significa que un <xref:EnvDTE.ProjectItem> objeto puede ser <xref:EnvDTE.ProjectItems> colección al mismo tiempo porque un `ProjectItems` colección puede contener los objetos anidados. El ejemplo básico del proyecto no muestra este anidamiento. Implementando la `Project` objeto, participar en la estructura de árbol que caracteriza el diseño de todo el modelo de automatización.  
  
 La automatización de proyecto sigue la ruta de acceso en el diagrama siguiente.  
  
 ![Objetos de proyecto de Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
Automatización de proyecto  
  
 Si no implementa un `Project` de objeto, el entorno también devolverá un tipo genérico `Project` objeto que contiene solo el nombre del proyecto.  
  
## <a name="see-also"></a>Vea también  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>