---
title: Proyecto de modelado | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 58262c6d4edda1dd0be7d147ae21645b3305bfaa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573829"
---
# <a name="project-modeling"></a>Modelado de proyectos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [proyecto de modelado](https://docs.microsoft.com/visualstudio/extensibility/internals/project-modeling).  
  
El siguiente paso en la provisión de automatización para el proyecto consiste en implementar los objetos de proyecto estándar: la <xref:EnvDTE.Projects> y `ProjectItems` colecciones; el `Project` y <xref:EnvDTE.ProjectItem> objetos; y los demás objetos únicos de su implementación. Estos objetos estándares se definen en el archivo Dteinternal.h. En el ejemplo BscPrj se proporciona una implementación de los objetos estándar. Puede utilizar estas clases como modelos para crear sus propios objetos de proyecto estándar independiente en paralelo con objetos de proyectos de otros tipos de proyecto.  
  
 Se da por supuesto un consumidor de automatización para poder llamar a <xref:EnvDTE.Solution>("`<UniqueProjName>")` y <xref:EnvDTE.ProjectItems> (`n`) donde n es un número de índice para la obtención de un proyecto específico de la solución. Realizar esta llamada Automatización hace que el entorno llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> en la jerarquía del proyecto adecuado, pasando VSITEMID_ROOT como el parámetro ItemID y VSHPROPID_ExtObject como parámetro VSHPROPID. `IVsHierarchy::GetProperty` Devuelve un `IDispatch` puntero al objeto de automatización que proporciona el núcleo `Project` interfaz, que se ha implementado.  
  
 El siguiente es la sintaxis de `IVsHierarchy::GetProperty`.  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 Proyectos de acomodar el anidamiento y utilizar colecciones para crear grupos de elementos de proyecto. La jerarquía tiene este aspecto.  
  
```  
Projects  
  |– Project  
      |– ProjectItems (a collection of ProjectItem)  
          |– ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 El anidamiento significa que un <xref:EnvDTE.ProjectItem> objeto puede ser <xref:EnvDTE.ProjectItems> colección al mismo tiempo porque un `ProjectItems` colección puede contener los objetos anidados. El proyecto básico de ejemplo no muestra este anidamiento. Implementando el `Project` de objeto, participa en la estructura de árbol que caracteriza el diseño del modelo de automatización general.  
  
 La automatización de proyectos de sigue la ruta de acceso en el diagrama siguiente.  
  
 ![Objetos de proyecto de Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
Automatización de proyectos  
  
 Si implementa un `Project` objeto, el entorno seguirá devolviendo un tipo genérico `Project` objeto que contiene únicamente el nombre del proyecto.  
  
## <a name="see-also"></a>Vea también  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>

