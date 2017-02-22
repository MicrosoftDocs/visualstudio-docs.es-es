---
title: "Configuraci&#243;n del proyecto para la salida | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "las configuraciones de proyecto, la salida"
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Configuraci&#243;n del proyecto para la salida
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cada configuración puede admitir un conjunto de procesos de compilación que generar salida elementos como archivos ejecutables o recurso. Estos elementos de salida son privados para el usuario y pueden colocarse en grupos que se vinculan los tipos relacionados de salida, como archivos ejecutables \(.exe, .dll, .lib\) y archivos de origen \(.idl, archivos .h\).  
  
 Elementos de salida pueden estar disponibles a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> métodos y enumerado con el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> métodos. Si desea agrupar los elementos de salida, también debe implementar el proyecto de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> interfaz.  
  
 La construcción desarrollado mediante la implementación de `IVsOutputGroup` permite a los proyectos a las salidas del grupo según el uso. Por ejemplo, podría agrupar un archivo DLL con su base de datos de programa \(PDB\).  
  
> [!NOTE]
>  Un archivo PDB contiene información de depuración y se crea cuando se especifica la opción 'Generar información de depuración' al generar el archivo .dll o .exe. Normalmente se genera el archivo .pdb para sólo la configuración de proyecto de depuración.  
  
 El proyecto debe devolver el mismo número de grupos para cada configuración que es compatible, incluso aunque el número de salidas dentro de un grupo puede variar para cada configuración. Por ejemplo, Matt del proyecto DLL podría incluir mattd.dll y mattd.pdb en la configuración de depuración, pero sólo incluir matt.dll en configuración comercial.  
  
 Los grupos también tienen la misma información de identificador, como el nombre canónico, el nombre para mostrar y la información de grupo de configuración dentro de un proyecto. Esta coherencia permite continuar funcionando aunque cambien configuraciones el empaquetado e implementación.  
  
 Grupos también pueden tener una salida de clave que permite accesos directos de empaquetado para que apunte a algo significativo. Cualquier grupo puede estar vacío en una configuración determinada, por lo que debe hacer ninguna suposición sobre el tamaño de un grupo. El tamaño \(número de salidas\) de cada grupo en ninguna otra configuración puede ser diferente del tamaño de otro grupo en la misma configuración. También puede ser diferente del tamaño del mismo grupo en otra configuración.  
  
 ![Gráfico de grupos de resultados](../../extensibility/internals/media/vsoutputgroups.png "vsOutputGroups")  
Grupos de resultados  
  
 El uso principal de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> interfaz es proporcionar acceso para compilar, implementar y depurar objetos de administración y permitir la libertad de salidas del grupo de proyectos. Para obtener más información sobre el uso de esta interfaz, vea [Objeto de configuración de proyecto](../../extensibility/internals/project-configuration-object.md).  
  
 En el diagrama anterior, crea el grupo tiene una clave de salida en las distintas configuraciones \(bD.exe o b.exe\), por lo que el usuario puede crear un acceso directo a integrada y sepa que el método abreviado funcionará independientemente de la configuración implementada. Origen de grupo no tiene una clave de salida, por lo que el usuario no puede crear un acceso directo a él. Si depurar compilada de grupo tiene una salida de clave, pero el grupo comercial crea no, que sería una implementación incorrecta. Así pues, a continuación, si cualquier configuración tiene un grupo que no contenga ninguna salida, y, como resultado, ningún archivo de clave y, a continuación, otras configuraciones con ese grupo que contienen resultados no pueden tener archivos de clave. Los editores del instalador se suponen que nombres canónicos y nombres para mostrar de grupos, además de la existencia de un archivo de clave no cambian basándose en las configuraciones.  
  
 Tenga en cuenta que, si un proyecto tiene un `IVsOutputGroup` que desea empaquetar o implementar, es suficiente para no poner esa salida en un grupo. El resultado aún puede enumerarse normalmente implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> método que devuelve todos los resultados de la configuración, independientemente de la agrupación.  
  
 Para obtener más información, vea la implementación de `IVsOutputGroup` en el ejemplo de proyecto personalizada al [MPF de proyectos](http://mpfproj12.codeplex.com).  
  
## Vea también  
 [Administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md)   
 [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)   
 [Objeto de configuración de proyecto](../../extensibility/internals/project-configuration-object.md)   
 [Configuración de soluciones](../../extensibility/internals/solution-configuration.md)