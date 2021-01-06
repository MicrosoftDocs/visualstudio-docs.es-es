---
title: Modelado de proyectos | Microsoft Docs
description: Obtenga información sobre los objetos de proyecto estándar necesarios para crear la automatización para el nuevo tipo de proyecto y la ruta de acceso que sigue la automatización del proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a481e731f01230139ec4342231479606c49bd11
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877421"
---
# <a name="project-modeling"></a>Modelado de proyectos
El siguiente paso para proporcionar automatización para el proyecto es implementar los objetos de proyecto estándar: las <xref:EnvDTE.Projects> `ProjectItems` colecciones y, los `Project` <xref:EnvDTE.ProjectItem> objetos y, y los objetos restantes exclusivos de la implementación. Estos objetos estándar se definen en el archivo Dteinternal. h. En el ejemplo BscPrj se proporciona una implementación de los objetos estándar. Puede usar estas clases como modelos para crear sus propios objetos de proyecto estándar que se encuentran en paralelo con objetos de proyecto de otros tipos de proyectos.

 Un consumidor de automatización presupone que puede llamar a <xref:EnvDTE.Solution> (" `<UniqueProjName>")` y <xref:EnvDTE.ProjectItems> (), `n` donde n es un número de índice para obtener un proyecto específico en la solución. Al hacer esta llamada de automatización, el entorno llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> en la jerarquía de proyecto adecuada, pasando VSITEMID_ROOT como parámetro Itemid y VSHPROPID_ExtObject como parámetro VSHPROPID. `IVsHierarchy::GetProperty` Devuelve un `IDispatch` puntero al objeto de automatización que proporciona la `Project` interfaz principal, que ha implementado.

 A continuación se encuentra la sintaxis de `IVsHierarchy::GetProperty` .

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

 La anidación significa que un <xref:EnvDTE.ProjectItem> objeto puede ser <xref:EnvDTE.ProjectItems> colección al mismo tiempo porque una `ProjectItems` colección puede contener los objetos anidados. En el ejemplo de proyecto básico no se muestra este anidamiento. Al implementar el `Project` objeto, participa en la estructura de tipo árbol que caracteriza el diseño del modelo de automatización general.

 La automatización del proyecto sigue la ruta de acceso en el diagrama siguiente.

 ![Objetos de proyecto de Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Automatización de proyectos

 Si no implementa un `Project` objeto, el entorno de seguirá devolviendo un objeto genérico `Project` que contenga solo el nombre del proyecto.

## <a name="see-also"></a>Consulte también
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
