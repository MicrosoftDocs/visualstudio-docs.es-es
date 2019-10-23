---
title: Modelado de proyectos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42e810a36478e49a578c6713d20f1bfc6be98309
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725557"
---
# <a name="project-modeling"></a>Modelado de proyectos
El siguiente paso para proporcionar automatización para el proyecto es implementar los objetos de proyecto estándar: las colecciones <xref:EnvDTE.Projects> y `ProjectItems`; los objetos `Project` y <xref:EnvDTE.ProjectItem>; y los objetos restantes exclusivos de la implementación. Estos objetos estándar se definen en el archivo Dteinternal. h. En el ejemplo BscPrj se proporciona una implementación de los objetos estándar. Puede usar estas clases como modelos para crear sus propios objetos de proyecto estándar que se encuentran en paralelo con objetos de proyecto de otros tipos de proyectos.

 Un consumidor de automatización presupone que podrá llamar a <xref:EnvDTE.Solution> ("`<UniqueProjName>")` y <xref:EnvDTE.ProjectItems> (`n`), donde n es un número de índice para obtener un proyecto específico en la solución. Al hacer esta llamada de automatización, el entorno llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> en la jerarquía de proyecto adecuada, pasando VSITEMID_ROOT como parámetro ItemID y VSHPROPID_ExtObject como parámetro VSHPROPID. `IVsHierarchy::GetProperty` devuelve un puntero de `IDispatch` al objeto de automatización que proporciona la interfaz de `Project` básica, que se ha implementado.

 A continuación se encuentra la sintaxis de `IVsHierarchy::GetProperty`.

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 Los proyectos de admiten el anidamiento y el uso de colecciones para crear grupos de elementos de proyecto. La jerarquía tiene el siguiente aspecto.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 La anidación significa que un objeto de <xref:EnvDTE.ProjectItem> se puede <xref:EnvDTE.ProjectItems> colección al mismo tiempo porque una colección de `ProjectItems` puede contener los objetos anidados. En el ejemplo de proyecto básico no se muestra este anidamiento. Al implementar el objeto de `Project`, participa en la estructura de árbol similar a la que caracteriza el diseño del modelo de automatización general.

 La automatización del proyecto sigue la ruta de acceso en el diagrama siguiente.

 ![Objetos de proyecto de Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Automatización de proyectos

 Si no implementa un objeto de `Project`, el entorno de seguirá devolviendo un objeto de `Project` genérico que contenga solo el nombre del proyecto.

## <a name="see-also"></a>Vea también
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>