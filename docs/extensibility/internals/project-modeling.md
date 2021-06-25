---
title: Project Modeling | Microsoft Docs
description: Obtenga información sobre los objetos de proyecto estándar necesarios para crear automatización para el nuevo tipo de proyecto y la ruta de acceso que sigue la automatización del proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b90271fcc43c627f2eb7dbb2f318427ad0d9839e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899685"
---
# <a name="project-modeling"></a>Modelado de proyectos
El siguiente paso para proporcionar automatización para el proyecto es implementar los objetos de proyecto estándar: las colecciones y , los objetos y y los objetos <xref:EnvDTE.Projects> `ProjectItems` restantes únicos de la `Project` <xref:EnvDTE.ProjectItem> implementación. Estos objetos estándar se definen en el archivo Dteinternal.h. En el ejemplo BscPrj se proporciona una implementación de los objetos estándar. Puede usar estas clases como modelos para crear sus propios objetos de proyecto estándar que se en paralelo con objetos de proyecto de otros tipos de proyecto.

 Un consumidor de automatización supone que puede llamar a (" y ( ), donde n es un número de índice para obtener <xref:EnvDTE.Solution> un proyecto específico en la `<UniqueProjName>")` <xref:EnvDTE.ProjectItems> `n` solución. La realización de esta llamada de automatización hace que el entorno llame a en la jerarquía de proyectos adecuada, pasando VSITEMID_ROOT como parámetro ItemID y VSHPROPID_ExtObject <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> como parámetro VSHPROPID. `IVsHierarchy::GetProperty` devuelve un `IDispatch` puntero al objeto de automatización que proporciona la interfaz `Project` principal, que ha implementado.

 A continuación se muestra la sintaxis de `IVsHierarchy::GetProperty` .

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 Los proyectos admiten el anidamiento y usan colecciones para crear grupos de elementos de proyecto. La jerarquía tiene este aspecto.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 Anidar significa que un <xref:EnvDTE.ProjectItem> objeto puede ser una colección al mismo tiempo porque una colección puede contener los objetos <xref:EnvDTE.ProjectItems> `ProjectItems` anidados. El ejemplo de proyecto básico no muestra este anidamiento. Al implementar el objeto , participa en la estructura de árbol que caracteriza el `Project` diseño del modelo de automatización general.

 La automatización del proyecto sigue la ruta de acceso del diagrama siguiente.

 ![Visual Studio project objects](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Automatización de proyectos

 Si no implementa un objeto , el entorno devolverá un objeto genérico que solo `Project` contiene el nombre del `Project` proyecto.

## <a name="see-also"></a>Consulta también
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
