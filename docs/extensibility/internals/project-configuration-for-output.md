---
title: Configuración del proyecto para la salida ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78b95457af4c5d806fdfcc20f49ac4e82df36488
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706664"
---
# <a name="project-configuration-for-output"></a>Configuración del proyecto para la salida
Cada configuración puede admitir un conjunto de procesos de compilación que producen elementos de salida, como archivos ejecutables o de recursos. Estos elementos de salida son privados para el usuario y se pueden colocar en grupos que vinculan tipos de salida relacionados, como archivos ejecutables (.exe, .dll, .lib) y archivos de origen (archivos .idl, .h).

 Los elementos de salida <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> pueden estar disponibles a través de los métodos y enumerarlos con los <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> métodos. Cuando desee agrupar elementos de salida, <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> el proyecto también debe implementar la interfaz.

 La construcción desarrollada `IVsOutputGroup` por la implementación permite a los proyectos agrupar las salidas según el uso. Por ejemplo, un archivo DLL podría agruparse con su base de datos de programas (PDB).

> [!NOTE]
> Un archivo PDB contiene información de depuración y se crea cuando se especifica la opción 'Generar información de depuración' al compilar el archivo .dll o .exe. El archivo .pdb se genera normalmente solo para la configuración del proyecto de depuración.

 El proyecto debe devolver el mismo número de grupos para cada configuración que admite, aunque el número de salidas contenidas en un grupo puede variar de una configuración a otra. Por ejemplo, el archivo DLL del proyecto Matt puede incluir mattd.dll y mattd.pdb en la configuración de depuración, pero solo incluye matt.dll en la configuración de Retail.

 Los grupos también tienen la misma información de identificador, como el nombre canónico, el nombre para mostrar y la información de grupo, desde la configuración hasta la configuración dentro de un proyecto. Esta coherencia permite que la implementación y el empaquetado sigan funcionando incluso si cambian las configuraciones.

 Los grupos también pueden tener una salida clave que permite que los accesos directos de empaquetado apunten a algo significativo. Cualquier grupo puede estar vacío en una configuración determinada, por lo que no se debe hacer ninguna suposición sobre el tamaño de un grupo. El tamaño (número de salidas) de cada grupo en cualquier configuración puede ser diferente del tamaño de otro grupo en la misma configuración. También puede ser diferente del tamaño del mismo grupo en otra configuración.

 ![Gráfico de grupos de salida](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups") Grupos de salida

 El uso principal <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> de la interfaz es proporcionar acceso para compilar, implementar y depurar objetos de administración y permitir a los proyectos la libertad de agrupar salidas. Para obtener más información sobre el uso de esta interfaz, vea Objeto de configuración de [proyecto](../../extensibility/internals/project-configuration-object.md).

 En el diagrama anterior, Group Built tiene una salida clave entre configuraciones (bD.exe o b.exe) para que el usuario pueda crear un acceso directo a Built y saber que el acceso directo funcionará independientemente de la configuración implementada. Origen de grupo no tiene una salida de clave, por lo que el usuario no puede crear un acceso directo a él. Si el grupo de depuración compilado tiene una salida clave, pero el grupo comercial compilado no, sería una implementación incorrecta. Se deduce, entonces, que si cualquier configuración tiene un grupo que no contiene salidas y, como resultado, ningún archivo de clave, otras configuraciones con ese grupo que contienen salidas no pueden tener archivos de clave. Los editores del instalador asumen que los nombres canónicos y los nombres para mostrar de los grupos, además de la existencia de un archivo de clave, no cambian en función de las configuraciones.

 Tenga en cuenta que `IVsOutputGroup` si un proyecto tiene un que no desea empaquetar o implementar, es suficiente no colocar esa salida en un grupo. La salida todavía se puede enumerar <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> normalmente mediante la implementación del método que devuelve todas las salidas de una configuración independientemente de la agrupación.

 Para obtener más información, `IVsOutputGroup` vea la implementación en el ejemplo De proyecto personalizado en [MPF para proyectos](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="see-also"></a>Vea también
- [Administración de opciones de configuración](../../extensibility/internals/managing-configuration-options.md)
- [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)
- [Objeto de configuración del proyecto](../../extensibility/internals/project-configuration-object.md)
- [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)
