---
title: Modelado de Proyectos (Project Modeling) Microsoft Docs
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
ms.openlocfilehash: c1ac89baf5bc7582d3430532938a5e5a0c35a4c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706555"
---
# <a name="project-modeling"></a>Modelado de proyectos
El siguiente paso para proporcionar automatización para el proyecto <xref:EnvDTE.Projects> `ProjectItems` es implementar los objetos de proyecto estándar: las colecciones; los `Project` <xref:EnvDTE.ProjectItem> objetos y; y los objetos restantes únicos para su implementación. Estos objetos estándar se definen en el archivo Dteinternal.h. En el ejemplo BscPrj se proporciona una implementación de los objetos estándar. Puede utilizar estas clases como modelos para crear sus propios objetos de proyecto estándar que se encuentran en paralelo con objetos de proyecto de otros tipos de proyecto.

 Un consumidor de automatización presume <xref:EnvDTE.Solution>`<UniqueProjName>")` poder <xref:EnvDTE.ProjectItems> `n`llamar a (" y ( ) donde n es un número de índice para obtener un proyecto específico en la solución. Realizar esta llamada de automatización hace que el entorno llame <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> a la jerarquía de proyecto adecuada, pasando VSITEMID_ROOT como el parámetro ItemID y VSHPROPID_ExtObject como parámetro VSHPROPID. `IVsHierarchy::GetProperty`devuelve `IDispatch` un puntero al objeto `Project` de automatización que proporciona la interfaz principal, que ha implementado.

 A continuación se `IVsHierarchy::GetProperty`muestra la sintaxis de .

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 Los proyectos admiten el anidamiento y usan colecciones para crear grupos de elementos de proyecto. La jerarquía se ve así.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 Anidar significa <xref:EnvDTE.ProjectItem> que un <xref:EnvDTE.ProjectItems> objeto puede ser `ProjectItems` colección al mismo tiempo porque una colección puede contener los objetos anidados. El proyecto básico ejemplo no muestra este anidamiento. Al implementar `Project` el objeto, participa en la estructura de árbol que caracteriza el diseño del modelo de automatización general.

 La automatización del proyecto sigue la ruta de acceso en el diagrama siguiente.

 ![Objetos de proyecto](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") de Visual Studio Automatización de proyectos

 Si no implementa `Project` un objeto, el entorno `Project` seguirá devolviendo un objeto genérico que contenga solo el nombre del proyecto.

## <a name="see-also"></a>Vea también
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
