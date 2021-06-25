---
title: Configuración del proyecto para la salida | Microsoft Docs
description: Obtenga información sobre los procesos de compilación que cada configuración puede admitir y las interfaces y métodos por los que se pueden hacer disponibles los elementos de salida.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8b718e70bac0d9e09936daf743420acc04a1c4ad
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899880"
---
# <a name="project-configuration-for-output"></a>Configuración del proyecto para la salida
Cada configuración puede admitir un conjunto de procesos de compilación que generan elementos de salida, como archivos ejecutables o de recursos. Estos elementos de salida son privados para el usuario y se pueden colocar en grupos que vinculan tipos relacionados de salida, como archivos ejecutables (.exe, .dll, .lib) y archivos de origen (archivos .idl, .h).

 Los elementos de salida se pueden hacer disponibles a través <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> de los métodos y enumerarse con los <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> métodos . Si desea agrupar elementos de salida, el proyecto también debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> interfaz .

 La construcción desarrollada mediante la implementación permite `IVsOutputGroup` a los proyectos agrupar salidas según el uso. Por ejemplo, un archivo DLL podría agruparse con su base de datos de programa (PDB).

> [!NOTE]
> Un archivo PDB contiene información de depuración y se crea cuando se especifica la opción "Generar información de depuración" al compilar el .dll o .exe. Normalmente, el archivo .pdb se genera solo para la configuración del proyecto de depuración.

 El proyecto debe devolver el mismo número de grupos para cada configuración que admita, aunque el número de salidas contenidas en un grupo puede variar de una configuración a otra. Por ejemplo, el archivo DLL de Matt del proyecto podría incluir mattd.dll y mattd.pdb en la configuración de depuración, pero solo incluir matt.dll en la configuración comercial.

 Los grupos también tienen la misma información de identificador, como el nombre canónico, el nombre para mostrar y la información de grupo, desde la configuración a la configuración dentro de un proyecto. Esta coherencia permite que la implementación y el empaquetado sigan funcionando aunque cambien las configuraciones.

 Los grupos también pueden tener una salida clave que permite que los métodos abreviados de empaquetado apunten a algo significativo. Cualquier grupo puede estar vacío en una configuración determinada, por lo que no se debe realizar ninguna suposición sobre el tamaño de un grupo. El tamaño (número de salidas) de cada grupo de cualquier configuración puede ser diferente del tamaño de otro grupo en la misma configuración. También puede ser diferente del tamaño del mismo grupo en otra configuración.

 ![Gráfico grupos de salida](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups") Grupos de salida

 El uso principal de la interfaz es proporcionar acceso a los objetos de administración de compilación, implementación y depuración, y permitir a los proyectos la libertad <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> de agrupar salidas. Para obtener más información sobre el uso de esta interfaz, vea [Project Configuration Object](../../extensibility/internals/project-configuration-object.md).

 En el diagrama anterior, Group Built tiene una salida clave entre configuraciones (ya sea bD.exe o b.exe) para que el usuario pueda crear un acceso directo a Built y saber que el acceso directo funcionará independientemente de la configuración implementada. El origen del grupo no tiene una salida de clave, por lo que el usuario no puede crear un acceso directo a él. Si el grupo de depuración creado tiene una salida de clave, pero el grupo minorista no lo hace, sería una implementación incorrecta. A continuación, se sigue que si alguna configuración tiene un grupo que no contiene salidas y, como resultado, no hay ningún archivo de clave, otras configuraciones con ese grupo que contienen salidas no pueden tener archivos de clave. Los editores del instalador asumen que los nombres canónicos y los nombres para mostrar de los grupos, además de la existencia de un archivo de clave, no cambian en función de las configuraciones.

 Tenga en cuenta que si un proyecto tiene un que no quiere empaquetar o implementar, es suficiente no colocar esa `IVsOutputGroup` salida en un grupo. La salida se puede enumerar con normalidad implementando el método que devuelve todas las salidas de una configuración independientemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> de la agrupación.

 Para obtener más información, vea la implementación de `IVsOutputGroup` en el ejemplo de proyecto personalizado en [MPF for Projects](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="see-also"></a>Consulta también
- [Administración de opciones de configuración](../../extensibility/internals/managing-configuration-options.md)
- [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)
- [Objeto de configuración del proyecto](../../extensibility/internals/project-configuration-object.md)
- [Configuración de la solución](../../extensibility/internals/solution-configuration.md)
