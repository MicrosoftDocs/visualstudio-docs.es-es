---
title: Configuración para la salida del proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1c23f9210175b848bfdf3ddab56776092e39212c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740885"
---
# <a name="project-configuration-for-output"></a>Configuración del proyecto para la salida
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cada configuración puede admitir un conjunto de procesos de compilación que generan elementos de salida, como archivos ejecutables o un recurso. Estos elementos de salida son privados para el usuario y pueden colocarse en grupos que se vinculan los tipos relacionados de salida, como archivos ejecutables (.exe, .dll o .lib) y archivos de código fuente (.idl, archivos .h).  
  
 Elementos de salida pueden estar disponibles a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> métodos y enumerado con el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> métodos. Cuando desea agrupar elementos de salida, también debe implementar el proyecto de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> interfaz.  
  
 La construcción desarrollado implementando `IVsOutputGroup` permite que los proyectos agrupen resultados según su uso. Por ejemplo, se puede agrupar un archivo DLL con su base de datos de programa (PDB).  
  
> [!NOTE]
>  Un archivo PDB contiene información de depuración y se crea cuando se especifica la opción 'Generar información de depuración' al compilar el archivo .dll o .exe. Normalmente se genera el archivo .pdb para solo la configuración de proyecto de depuración.  
  
 El proyecto debe devolver el mismo número de grupos para cada configuración que admite, aunque el número de salidas contenida dentro de un grupo puede variar para cada configuración. Por ejemplo, Matt del proyecto DLL podría incluir mattd.dll y mattd.pdb en configuración de depuración, pero sólo incluir matt.dll en configuración de venta directa.  
  
 Los grupos también tienen la misma información de identificador, como información de grupo, nombre para mostrar y nombre canónico de configuración dentro de un proyecto. Esta coherencia permite la implementación y empaquetado siga funcionando aunque cambien las configuraciones.  
  
 Grupos también pueden tener una salida de clave que permite a los métodos abreviados de empaquetado para que apunte a algo significativo. Cualquier grupo puede estar vacío en una configuración determinada, por lo que no se debe realizar ninguna suposición sobre el tamaño de un grupo. El tamaño (número de salidas) de cada grupo en ninguna otra configuración puede ser diferente del tamaño de otro grupo en la misma configuración. También puede ser diferente del tamaño del mismo grupo en otra configuración.  
  
 ![Gráfico de grupos de salida](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
Grupos de resultados  
  
 El uso principal de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> interfaz es proporcionar acceso para crear, implementar y depurar objetos de administración y permitir que los proyectos de la libertad de salidas de grupo. Para obtener más información sobre el uso de esta interfaz, vea [objeto de configuración de proyecto](../../extensibility/internals/project-configuration-object.md).  
  
 En el diagrama anterior, creado el grupo tiene una clave de salida en las distintas configuraciones (bD.exe o b.exe) por lo que el usuario puede crear un acceso directo a integrada y sepa que el acceso directo funcionará independientemente de la configuración implementada. Origen del grupo no tiene una clave de salida, por lo que el usuario no puede crear un acceso directo a él. Si la depuración integrada de grupo tiene una salida de la clave, pero el grupo minorista integrado no es así, eso sería una implementación incorrecta. Así pues, a continuación, si cualquier configuración tiene un grupo que no contenga ninguna salida, y, como resultado, ningún archivo de clave y, a continuación, otras configuraciones con ese grupo que contienen las salidas no pueden tener archivos de clave. Los editores del instalador se suponen que no cambie los nombres canónicos y nombres para mostrar de grupos, además de la existencia de un archivo de clave, basándose en las configuraciones.  
  
 Tenga en cuenta que si un proyecto tiene un `IVsOutputGroup` que no desea empaquetar o implementar, es suficiente para no poner esa salida en un grupo. La salida aún puede enumerarse normalmente mediante la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> método que devuelve todos los resultados de la configuración, independientemente de la agrupación.  
  
 Para obtener más información, vea la implementación de `IVsOutputGroup` en el ejemplo del proyecto personalizado al [MPF de proyectos](http://mpfproj12.codeplex.com).  
  
## <a name="see-also"></a>Vea también  
 [Administración de las opciones de configuración](../../extensibility/internals/managing-configuration-options.md)   
 [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)   
 [Objeto de configuración de proyecto](../../extensibility/internals/project-configuration-object.md)   
 [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)

