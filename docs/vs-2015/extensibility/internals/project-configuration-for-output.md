---
title: Configuración del proyecto para la salida | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: addd7e8630ce35c6bdbbbb4c063197f75a74c97d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300673"
---
# <a name="project-configuration-for-output"></a>Configuración del proyecto para la salida
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cada configuración puede admitir un conjunto de procesos de compilación que producen elementos de salida, como archivos ejecutables o de recursos. Estos elementos de salida son privados para el usuario y se pueden colocar en grupos que vinculan tipos de salida relacionados, como archivos ejecutables (. exe,. dll,. lib) y archivos de código fuente (archivos. idl,. h).  
  
 Los elementos de salida se pueden poner a disposición a través de los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> y enumerados con los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>. Si desea agrupar los elementos de salida, el proyecto también debe implementar la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>.  
  
 La construcción desarrollada al implementar `IVsOutputGroup` permite a los proyectos agrupar las salidas según el uso. Por ejemplo, un archivo DLL se puede agrupar con su base de datos de programa (PDB).  
  
> [!NOTE]
> Un archivo PDB contiene información de depuración y se crea cuando se especifica la opción "generar información de depuración" al compilar el archivo. dll o. exe. El archivo. pdb se genera normalmente solo para la configuración del proyecto de depuración.  
  
 El proyecto debe devolver el mismo número de grupos para cada configuración que admita, aunque el número de salidas contenidas dentro de un grupo puede variar de una configuración a una configuración. Por ejemplo, la DLL del proyecto Matt puede incluir mattd. dll y matted. pdb en la configuración de depuración, pero solo incluye Matt. dll en configuración de venta directa.  
  
 Los grupos también tienen la misma información de identificador, como el nombre canónico, el nombre para mostrar y la información de grupo, de la configuración de en un proyecto. Esta coherencia permite que la implementación y el empaquetado sigan funcionando incluso si cambian las configuraciones.  
  
 Los grupos también pueden tener una salida de clave que permita que los accesos directos de empaquetado señalen a algo significativo. Cualquier grupo podría estar vacío en una configuración determinada, por lo que no se debe realizar ninguna suposición sobre el tamaño de un grupo. El tamaño (número de salidas) de cada grupo en cualquier configuración puede ser diferente del tamaño de otro grupo en la misma configuración. También puede ser diferente del tamaño del mismo grupo en otra configuración.  
  
 ![Gráfico de grupos de resultados](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
Grupos de resultados  
  
 El uso principal de la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> es proporcionar acceso a los objetos de administración de compilación, implementación y depuración, y permite a los proyectos la libertad de agrupar las salidas. Para obtener más información sobre el uso de esta interfaz, consulte [objeto de configuración del proyecto](../../extensibility/internals/project-configuration-object.md).  
  
 En el diagrama anterior, el grupo compilado tiene una salida de clave en las configuraciones (ya sea bD. exe o b. exe) para que el usuario pueda crear un acceso directo a compilado y sepa que el acceso directo funcionará independientemente de la configuración implementada. El origen del grupo no tiene una salida de clave, por lo que el usuario no puede crear un acceso directo a él. Si el grupo de depuración compilado tiene una salida de clave, pero el grupo comercial compilado no es una implementación incorrecta. Después, que si alguna configuración tiene un grupo que no contiene salidas y, como resultado, ningún archivo de clave, otras configuraciones con ese grupo que contengan salidas no podrán tener archivos de clave. Los editores del instalador suponen que los nombres canónicos y los nombres para mostrar de los grupos, además de la existencia de un archivo de clave, no cambian en función de las configuraciones.  
  
 Tenga en cuenta que si un proyecto tiene una `IVsOutputGroup` que no desea empaquetar o implementar, es suficiente no incluir esa salida en un grupo. La salida todavía se puede enumerar normalmente implementando el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> que devuelve todas las salidas de configuración independientemente de la agrupación.  
  
 Para obtener más información, vea la implementación de `IVsOutputGroup` en el ejemplo de proyecto personalizado en [MPF para proyectos de](https://archive.codeplex.com/?p=mpfproj12).  
  
## <a name="see-also"></a>Vea también  
 [Administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md)   
 [Configuración del proyecto para Compilar](../../extensibility/internals/project-configuration-for-building.md)   
 [Objeto de configuración de proyecto](../../extensibility/internals/project-configuration-object.md)   
 [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)
