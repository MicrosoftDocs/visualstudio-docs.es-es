---
title: Configuración del proyecto para la salida | Microsoft Docs
description: Obtenga información sobre los procesos de compilación que cada configuración puede admitir y las interfaces y los métodos por los que los elementos de salida pueden estar disponibles.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 13e37999ad9f3bada375c1897207e1e4c15546e8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082015"
---
# <a name="project-configuration-for-output"></a>Configuración del proyecto para la salida
Cada configuración puede admitir un conjunto de procesos de compilación que producen elementos de salida, como archivos ejecutables o de recursos. Estos elementos de salida son privados para el usuario y se pueden colocar en grupos que vinculan tipos de salida relacionados, como archivos ejecutables (. exe,. dll,. lib) y archivos de código fuente (archivos. idl,. h).

 Los elementos de salida se pueden poner a disposición a través de los <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> métodos y enumerados con los <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> métodos. Si desea agrupar los elementos de salida, el proyecto también debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> interfaz.

 La construcción desarrollada mediante la implementación `IVsOutputGroup` permite a los proyectos agrupar las salidas según el uso. Por ejemplo, un archivo DLL se puede agrupar con su base de datos de programa (PDB).

> [!NOTE]
> Un archivo PDB contiene información de depuración y se crea cuando se especifica la opción "generar información de depuración" al compilar el archivo. dll o. exe. El archivo. pdb se genera normalmente solo para la configuración del proyecto de depuración.

 El proyecto debe devolver el mismo número de grupos para cada configuración que admita, aunque el número de salidas contenidas dentro de un grupo puede variar de una configuración a una configuración. Por ejemplo, la DLL del proyecto Matt podría incluir mattd.dll y mated. pdb en la configuración de depuración, pero incluir solo matt.dll en la configuración de venta directa.

 Los grupos también tienen la misma información de identificador, como el nombre canónico, el nombre para mostrar y la información de grupo, de la configuración de en un proyecto. Esta coherencia permite que la implementación y el empaquetado sigan funcionando incluso si cambian las configuraciones.

 Los grupos también pueden tener una salida de clave que permita que los accesos directos de empaquetado señalen a algo significativo. Cualquier grupo podría estar vacío en una configuración determinada, por lo que no se debe realizar ninguna suposición sobre el tamaño de un grupo. El tamaño (número de salidas) de cada grupo en cualquier configuración puede ser diferente del tamaño de otro grupo en la misma configuración. También puede ser diferente del tamaño del mismo grupo en otra configuración.

 ![Gráfico de grupos de resultados](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups") Grupos de resultados

 El uso principal de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> interfaz es proporcionar acceso a los objetos de administración de compilación, implementación y depuración, y permite a los proyectos la libertad de agrupar las salidas. Para obtener más información sobre el uso de esta interfaz, consulte [objeto de configuración del proyecto](../../extensibility/internals/project-configuration-object.md).

 En el diagrama anterior, el grupo compilado tiene una salida de clave en las configuraciones (ya sea bD.exe o b.exe) para que el usuario pueda crear un acceso directo a compilar y sepa que el acceso directo funcionará independientemente de la configuración implementada. El origen del grupo no tiene una salida de clave, por lo que el usuario no puede crear un acceso directo a él. Si el grupo de depuración compilado tiene una salida de clave, pero el grupo comercial compilado no es una implementación incorrecta. Después, que si alguna configuración tiene un grupo que no contiene salidas y, como resultado, ningún archivo de clave, otras configuraciones con ese grupo que contengan salidas no podrán tener archivos de clave. Los editores del instalador suponen que los nombres canónicos y los nombres para mostrar de los grupos, además de la existencia de un archivo de clave, no cambian en función de las configuraciones.

 Tenga en cuenta que si un proyecto tiene un `IVsOutputGroup` que no quiere empaquetar o implementar, es suficiente que no incluya el resultado en un grupo. La salida todavía se puede enumerar normalmente implementando el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> método que devuelve todas las salidas de configuración independientemente de la agrupación.

 Para obtener más información, vea la implementación de `IVsOutputGroup` en el ejemplo de proyecto personalizado en [MPF para proyectos](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="see-also"></a>Consulte también
- [Administración de opciones de configuración](../../extensibility/internals/managing-configuration-options.md)
- [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)
- [Objeto de configuración del proyecto](../../extensibility/internals/project-configuration-object.md)
- [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)
