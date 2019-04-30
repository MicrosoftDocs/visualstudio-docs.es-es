---
title: Proyecto de modelado | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a2ae395d94d76fd2b11de33cc6d5053d8b92432
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62859674"
---
# <a name="project-modeling"></a>Modelado de proyectos
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
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 El anidamiento significa que un <xref:EnvDTE.ProjectItem> objeto puede ser <xref:EnvDTE.ProjectItems> colección al mismo tiempo porque un `ProjectItems` colección puede contener los objetos anidados. El proyecto básico de ejemplo no muestra este anidamiento. Implementando el `Project` de objeto, participa en la estructura de árbol que caracteriza el diseño del modelo de automatización general.

 La automatización de proyectos de sigue la ruta de acceso en el diagrama siguiente.

 ![Objetos de proyectos de Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") automatización de proyectos

 Si implementa un `Project` objeto, el entorno seguirá devolviendo un tipo genérico `Project` objeto que contiene únicamente el nombre del proyecto.

## <a name="see-also"></a>Vea también
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>