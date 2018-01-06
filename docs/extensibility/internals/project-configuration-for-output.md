---
title: "Configuración para la salida del proyecto | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4f3927ac9aa9e85be026d2b9a2af1c0c4d956c9f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="project-configuration-for-output"></a>Configuración del proyecto para la salida
Cada configuración puede admitir un conjunto de procesos de compilación que generar elementos de salida como archivos de recursos o ejecutables. Estos elementos de salida son privados para el usuario y pueden colocarse en grupos que se vinculan los tipos relacionados de salida, como archivos ejecutables (.exe, .dll, .lib) y archivos de origen (.idl, archivos .h).  
  
 Elementos de salida pueden ponerse a disposición a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> métodos y enumerado con el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> métodos. Si desea agrupar los elementos de salida, también debería implementar el proyecto de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> interfaz.  
  
 La construcción desarrollado mediante la implementación de `IVsOutputGroup` permite a los proyectos a las salidas de grupo según uso. Por ejemplo, un archivo DLL puede estar agrupado con su base de datos de programa (PDB).  
  
> [!NOTE]
>  Un archivo PDB contiene información de depuración y se crea cuando se especifica la opción 'Generar información de depuración' al compilar el archivo .dll o .exe. Normalmente se genera el archivo .pdb para solo la configuración de proyecto de depuración.  
  
 El proyecto debe devolver el mismo número de grupos para cada configuración que admite, aunque el número de salidas dentro de un grupo puede variar para cada configuración. Por ejemplo, Matt del proyecto DLL podría incluir mattd.dll y mattd.pdb en configuración de depuración, pero solo se incluyen matt.dll en configuración comercial.  
  
 Los grupos también tienen la misma información de identificador, como el nombre canónico, el nombre para mostrar y la información del grupo de configuración dentro de un proyecto. Esta coherencia permite empaquetado a continúe funcionando aunque cambien las configuraciones e implementación.  
  
 Los grupos también pueden tener una salida de clave que permite accesos directos de empaquetado para que apunte a algo significativo. Cualquier grupo puede estar vacío en una configuración determinada, por lo que no debe realizarse ninguna suposición sobre el tamaño de un grupo. El tamaño (número de salidas) de cada grupo en ninguna otra configuración puede ser diferente del tamaño de otro grupo en la misma configuración. También puede ser diferente del tamaño del mismo grupo en otra configuración.  
  
 ![Gráfico de grupos de salida](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
Grupos de resultados  
  
 El uso principal de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> interfaz es proporcionar acceso para compilar, implementar y depurar objetos de administración y permitir que los proyectos la libertad de salidas de grupo. Para obtener más información sobre el uso de esta interfaz, vea [objeto de configuración de proyecto](../../extensibility/internals/project-configuration-object.md).  
  
 En el diagrama anterior, creado grupo tiene una clave de salida en las distintas configuraciones (bD.exe o b.exe) por lo que el usuario puede crear un acceso directo a integrada y sabe que el método abreviado funcione, independientemente de la configuración que se implementó. Origen del grupo no tiene una clave de salida, por lo que el usuario no puede crear un acceso directo a ella. Si el grupo depurar compilada tiene una salida de clave, pero el grupo comercial crea no, que sería una implementación incorrecta. Así pues, a continuación, si cualquier configuración tiene un grupo que no contenga ninguna salida, y, como resultado, ningún archivo de claves y otras configuraciones con ese grupo que contengan salidas no pueden tener archivos de clave. Los editores de instalador se supone que nombres canónicos y nombres para mostrar de grupos, además de la existencia de un archivo de clave, no cambian en función de las configuraciones.  
  
 Tenga en cuenta que, si un proyecto tiene un `IVsOutputGroup` que no desea empaquetar o implementar, es suficiente para no incluir que los resultados en un grupo. La salida se puede seguir enumerar normalmente mediante la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> método que devuelve todas las salidas de la configuración, independientemente de la agrupación.  
  
 Para obtener más información, vea la implementación de `IVsOutputGroup` en el ejemplo de un proyecto al [MPF para los proyectos de](http://mpfproj12.codeplex.com).  
  
## <a name="see-also"></a>Vea también  
 [Administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md)   
 [Configuración del proyecto para una compilación](../../extensibility/internals/project-configuration-for-building.md)   
 [Objeto de configuración de proyecto](../../extensibility/internals/project-configuration-object.md)   
 [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)