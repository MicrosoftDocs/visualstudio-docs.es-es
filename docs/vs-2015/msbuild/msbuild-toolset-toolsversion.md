---
title: Conjunto de herramientas de MSBuild (ToolsVersion) | Microsoft Docs
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
- MSBuild, multitargeting
- targeting a specific .NET framework [MSBuild]
- MSBuild, targeting a specific .NET framework
- multitargeting [MSBuild]
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd516501acfc7690c12a253adc5da6cf163b5592
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851834"
---
# <a name="msbuild-toolset-toolsversion"></a>Conjunto de herramientas de MSBuild (ToolsVersion)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
MSBuild usa un conjunto de herramientas de tareas, destinos y herramientas para compilar una aplicación. Normalmente, un conjunto de herramientas de MSBuild incluye un archivo microsoft.common.tasks, un archivo microsoft.common.targets y compiladores como csc.exe y vbc.exe. La mayoría de los conjuntos de herramientas se pueden usar para compilar aplicaciones correspondientes a más de una versión de .NET Framework y a más de una plataforma de sistema. Sin embargo, el conjunto de herramientas de MSBuild 2.0 solo se puede usar para las aplicaciones de .NET Framework 2.0.  
  
## <a name="toolsversion-attribute"></a>Atributo ToolsVersion  
 El conjunto de herramientas se especifica en el atributo `ToolsVersion` del elemento [Project](../msbuild/project-element-msbuild.md) del archivo de proyecto. En el ejemplo siguiente se especifica que el proyecto debe compilarse usando el conjunto de herramientas de MSBuild 12.0:  
  
```  
<Project ToolsVersion="12.0" ... </Project>  
```  
  
## <a name="how-the-toolsversion-attribute-works"></a>Cómo funciona el atributo ToolsVersion  
 Al crear un nuevo proyecto en Visual Studio, o actualizar uno ya existente, se incluye automáticamente un atributo denominado `ToolsVersion` en el archivo de proyecto y su valor corresponde a la versión de MSBuild incluida en la edición de Visual Studio. Para obtener más información, consulte [Elegir una versión específica de .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
 Cuando se define un valor `ToolsVersion` en un archivo de proyecto, MSBuild usa ese valor para determinar los valores de las propiedades del conjunto de herramientas que están disponibles para el proyecto. Una propiedad del conjunto de herramientas es `$(MSBuildToolsPath)`, que especifica la ruta de acceso de las herramientas de .NET Framework. Solo se requiere esa propiedad (o `$(MSBuildBinPath)`) del conjunto de herramientas.  
  
 A partir de Visual Studio 2013, la versión del conjunto de herramientas MSBuild es la misma que el número de versión de Visual Studio. De forma predeterminada, MSBuild usa este conjunto de herramientas en Visual Studio y en la línea de comandos, independientemente de la versión del conjunto de herramientas especificada en el archivo de proyecto.  Este comportamiento puede invalidarse usando la marca /ToolsVersion. Para obtener más información, vea [Invalidar la configuración de ToolsVersion](../msbuild/overriding-toolsversion-settings.md).  
  
 En el ejemplo siguiente, MSBuild busca el archivo Microsoft.CSharp.targets usando la propiedad reservada `MSBuildToolsPath`:  
  
```  
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
```  
  
 Puede modificar el valor de `MSBuildToolsPath` definiendo un conjunto de herramientas personalizado. Para obtener más información, vea [Configuraciones de conjuntos de herramientas estándar y personalizados](../msbuild/standard-and-custom-toolset-configurations.md).  
  
 Al compilar una solución en la línea de comandos, si se especifica `ToolsVersion` para msbuild.exe, todos los proyectos y las dependencias entre proyectos se compilarán de acuerdo con esa `ToolsVersion`, aunque cada proyecto de la solución especifique su propia `ToolsVersion`. Para definir el valor `ToolsVersion` según el proyecto, vea [Invalidar la configuración de ToolsVersion](../msbuild/overriding-toolsversion-settings.md).  
  
 El atributo `ToolsVersion` también se usa para la migración del proyecto. Por ejemplo, si abre un proyecto de Visual Studio 2008 en Visual Studio 2010, el archivo de proyecto se actualiza para incluir ToolsVersion=”4.0”. Si después intenta abrir ese proyecto en Visual Studio 2008, este no reconocerá el atributo `ToolsVersion` actualizado y compilará el proyecto como si dicho atributo todavía estuviese establecido en 3.5.  
  
 Visual Studio 2010 y Visual Studio 2012 usan ToolsVersion 4.0. Visual Studio 2013 usa ToolsVersion 12.0. En muchos casos, se puede abrir el proyecto en las tres versiones de Visual Studio sin modificaciones. Visual Studio siempre usa el conjunto de herramientas correcto, pero se te notificará si la versión usada no coincide con la versión del archivo de proyecto. En casi todos los casos, esta advertencia es inofensiva porque los conjuntos de herramientas son compatibles en la mayoría de los casos.  
  
 Los subconjuntos de herramientas, que se describen más adelante en este tema, permiten que MSBuild cambie automáticamente a las herramientas que se van a usar en función del contexto en el que se ejecuta la compilación. Por ejemplo, MSBuild usa un conjunto de herramientas más reciente cuando se ejecuta en Visual Studio 2012 que cuando se ejecuta en Visual Studio 2010, sin necesidad de cambiar explícitamente el archivo de proyecto. Para obtener más información, vea [Crear proyectos personalizados con identificación de versión](../misc/making-custom-projects-version-aware.md).  
  
## <a name="toolset-implementation"></a>Implementación del conjunto de herramientas  
 Para implementar un conjunto de herramientas, seleccione las rutas de acceso de las distintas herramientas, destinos y tareas que constituyen dicho conjunto. Las herramientas del conjunto de herramientas que define MSBuild proceden de los orígenes siguientes:  
  
- La carpeta de .NET Framework.  
  
- Herramientas administradas adicionales.  
  
  Entre las herramientas administradas se incluyen ResGen.exe y TlbImp.exe.  
  
  MSBuild proporciona dos maneras de tener acceso al conjunto de herramientas:  
  
- Mediante las propiedades del conjunto de herramientas  
  
- Mediante los métodos de la clase <xref:Microsoft.Build.Utilities.ToolLocationHelper>  
  
  Las propiedades del conjunto de herramientas especifican las rutas de acceso de las herramientas. MSBuild usa el valor del atributo `ToolsVersion` del archivo de proyecto para encontrar la clave del Registro correspondiente, y después utiliza la información de dicha clave para establecer las propiedades del conjunto de herramientas. Por ejemplo, si `ToolsVersion` tiene el valor `12.0`, MSBuild establece las propiedades del conjunto de herramientas en función de esta clave del Registro: HKLM\Software\Microsoft\MSBuild\ToolsVersions\12.0.  
  
  Estas son las propiedades del conjunto de herramientas:  
  
- `MSBuildToolsPath` especifica la ruta de acceso de los archivos binarios de MSBuild.  
  
- `SDK40ToolsPath` especifica la ruta de acceso de las herramientas administradas adicionales para MSBuild 4.x (que podría ser 4.0 o 4.5).  
  
- `SDK35ToolsPath` especifica la ruta de acceso de las herramientas administradas adicionales para MSBuild 3,5.  
  
  Como alternativa, puede determinar el conjunto de herramientas mediante programación llamando a los métodos de la clase <xref:Microsoft.Build.Utilities.ToolLocationHelper>. La clase contiene estos métodos:  
  
- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A> devuelve la ruta de acceso de la carpeta de .NET Framework.  
  
- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A> devuelve la ruta de acceso de un archivo de la carpeta .NET Framework.  
  
- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A> devuelve la ruta de acceso de la carpeta de las herramientas administradas.  
  
- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A> devuelve la ruta de acceso de un archivo, que normalmente se encuentra en la carpeta de las herramientas administradas.  
  
- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToBuildTools%2A> devuelve la ruta de acceso de las herramientas de compilación.  
  
### <a name="sub-toolsets"></a>Subconjuntos de herramientas  
 Como se ha descrito anteriormente en este tema, MSBuild usa una clave del Registro para especificar la ruta de acceso de las herramientas básicas. Si la clave tiene una subclave, MSBuild la usa para especificar la ruta de acceso de un subconjunto de herramientas que contiene herramientas adicionales. En este caso, el conjunto de herramientas se define mediante la combinación de las definiciones de propiedades especificadas en ambas claves.  
  
> [!NOTE]
>  Si hay un conflicto entre los nombres de propiedades del conjunto de herramientas, el valor definido para la ruta de acceso de la subclave reemplaza al valor definido para la ruta de acceso de la clave raíz.  
  
 Los subconjuntos de herramientas se activan si se define la propiedad de compilación `VisualStudioVersion`. Esta propiedad puede tener uno de estos valores:  
  
- “10.0” especifica el subconjunto de herramientas de .NET Framework 4  
  
- “11,0” especifica el subconjunto de herramientas de .NET Framework 4,5  
  
- “12,0” especifica el subconjunto de herramientas de .NET Framework 4.5.1  
  
  Los subconjuntos de herramientas 10.0 y 11.0 deben usarse con ToolsVersion 4.0. En versiones posteriores, la versión del subconjunto de herramientas y ToolsVersion deben coincidir.  
  
  Durante una compilación, MSBuild automáticamente determina y establece un valor predeterminado para la propiedad `VisualStudioVersion` si no se ha definido aún.  
  
  MSBuild proporciona sobrecargas para los métodos de la clase `ToolLocationHelper` que agregan un valor enumerado `VisualStudioVersion` como parámetro.  
  
  Los subconjuntos de herramientas se incluyen por primera vez en .NET Framework 4.5.  
  
## <a name="see-also"></a>Vea también  
 [Configuraciones de conjuntos de herramientas estándar y personalizados](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Compatibilidad con múltiples versiones (multi-targeting)](../msbuild/msbuild-multitargeting-overview.md)



