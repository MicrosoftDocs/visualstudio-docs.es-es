---
title: Conjunto de herramientas de MSBuild (ToolsVersion) | Microsoft Docs
ms.date: 01/31/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multitargeting
- targeting a specific .NET framework [MSBuild]
- MSBuild, targeting a specific .NET framework
- multitargeting [MSBuild]
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b77ea7f04377a1c531efeff780e9303f0bd3eb79
ms.sourcegitcommit: a3edc753c951f317b67ce294cd2fc74f0c45390c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2020
ms.locfileid: "89426968"
---
# <a name="msbuild-toolset-toolsversion"></a>Conjunto de herramientas de MSBuild (ToolsVersion)

MSBuild usa un conjunto de herramientas de tareas, destinos y herramientas para compilar una aplicación. Normalmente, un conjunto de herramientas de MSBuild incluye un archivo *microsoft.common.tasks*, un archivo *microsoft.common.targets* y compiladores como *csc.exe* y *vbc.exe*. La mayoría de los conjuntos de herramientas se pueden usar para compilar aplicaciones correspondientes a más de una versión de .NET Framework y a más de una plataforma de sistema. Sin embargo, el conjunto de herramientas de MSBuild 2.0 solo se puede usar para las aplicaciones de .NET Framework 2.0.

## <a name="toolsversion-attribute"></a>Atributo ToolsVersion

::: moniker range=">=vs-2019"
 El conjunto de herramientas se especifica en el atributo `ToolsVersion` del elemento [Project](../msbuild/project-element-msbuild.md) del archivo de proyecto. En el ejemplo siguiente, se especifica que el proyecto debe compilarse usando el conjunto de herramientas de MSBuild "Current".

```xml
<Project ToolsVersion="Current" ... </Project>
```

::: moniker-end

::: moniker range="vs-2017"
 El conjunto de herramientas se especifica en el atributo `ToolsVersion` del elemento [Project](../msbuild/project-element-msbuild.md) del archivo de proyecto. En el ejemplo siguiente, se especifica que el proyecto debe compilarse usando el conjunto de herramientas de MSBuild 15.0.

```xml
<Project ToolsVersion="15.0" ... </Project>
```

::: moniker-end

> [!NOTE]
> En algunos tipos de proyecto se usa el atributo `sdk` en lugar de `ToolsVersion`. Para más información, vea [Adiciones al formato csproj para .NET Core](/dotnet/core/tools/csproj).

## <a name="how-the-toolsversion-attribute-works"></a>Cómo funciona el atributo ToolsVersion

 Al crear un nuevo proyecto en Visual Studio, o actualizar uno ya existente, se incluye automáticamente un atributo denominado `ToolsVersion` en el archivo de proyecto y su valor corresponde a la versión de MSBuild incluida en la edición de Visual Studio. Para obtener más información, vea [Información general sobre destinos de Framework](../ide/visual-studio-multi-targeting-overview.md).

 Cuando se define un valor `ToolsVersion` en un archivo de proyecto, MSBuild usa ese valor para determinar los valores de las propiedades del conjunto de herramientas que están disponibles para el proyecto. Una propiedad del conjunto de herramientas es `$(MSBuildToolsPath)`, que especifica la ruta de acceso de las herramientas de .NET Framework. Solo se requiere esa propiedad (o `$(MSBuildBinPath)`) del conjunto de herramientas.

 A partir de Visual Studio 2013, la versión del conjunto de herramientas MSBuild es la misma que el número de versión de Visual Studio. De forma predeterminada, MSBuild usa este conjunto de herramientas en Visual Studio y en la línea de comandos, independientemente de la versión del conjunto de herramientas especificada en el archivo de proyecto.  Este comportamiento puede invalidarse usando la marca -ToolsVersion. Para más información, consulte [Invalidar la configuración de ToolsVersion](../msbuild/overriding-toolsversion-settings.md).

 En el ejemplo siguiente, MSBuild busca el archivo *Microsoft.CSharp.targets* usando la propiedad reservada `MSBuildToolsPath`.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

 Puede modificar el valor de `MSBuildToolsPath` definiendo un conjunto de herramientas personalizado. Para más información, consulte [Configuraciones de conjuntos de herramientas estándar y personalizados](../msbuild/standard-and-custom-toolset-configurations.md).

 Al crear una solución en la línea de comandos y especifique un `ToolsVersion` para *msbuild.exe*, todos los proyectos y sus dependencias proyecto a proyecto se crean según la que `ToolsVersion`, aunque cada proyecto de la solución Especifique su propia `ToolsVersion`. Para definir el valor `ToolsVersion` según el proyecto, consulte [Invalidar la configuración de ToolsVersion](../msbuild/overriding-toolsversion-settings.md).

 El atributo `ToolsVersion` también se usa para la migración del proyecto. Por ejemplo, si abre un proyecto de Visual Studio 2008 en Visual Studio 2010, el archivo de proyecto se actualiza para incluir ToolsVersion="4.0". Si después intenta abrir ese proyecto en Visual Studio 2008, este no reconocerá el atributo `ToolsVersion` actualizado y compilará el proyecto como si dicho atributo todavía estuviese establecido en 3.5.

 Visual Studio 2010 y Visual Studio 2012 usan ToolsVersion 4.0. Visual Studio 2013 usa ToolsVersion 12.0. Visual Studio 2015 usa ToolsVersion 14.0, y Visual Studio 2017 usa ToolsVersion 15.0. En muchos casos, puede abrir el proyecto en varias versiones de Visual Studio sin modificaciones. Visual Studio siempre usa el conjunto de herramientas correcto, pero se te notificará si la versión usada no coincide con la versión del archivo de proyecto. En casi todos los casos, esta advertencia es inofensiva porque los conjuntos de herramientas son compatibles en la mayoría de los casos.

 Los subconjuntos de herramientas, que se describen más adelante en este tema, permiten que MSBuild cambie automáticamente a las herramientas que se van a usar en función del contexto en el que se ejecuta la compilación. Por ejemplo, MSBuild usa un conjunto de herramientas más reciente cuando se ejecuta en Visual Studio 2012 que cuando se ejecuta en Visual Studio 2010, sin necesidad de cambiar explícitamente el archivo de proyecto.

## <a name="toolset-implementation"></a>Implementación del conjunto de herramientas

 Para implementar un conjunto de herramientas, seleccione las rutas de acceso de las distintas herramientas, destinos y tareas que constituyen dicho conjunto. Las herramientas del conjunto de herramientas que define MSBuild proceden de los orígenes siguientes:

- La carpeta de .NET Framework.

- Herramientas administradas adicionales.

  Entre las herramientas administradas se incluyen *ResGen.exe* y *TlbImp.exe*.

MSBuild proporciona dos maneras de tener acceso al conjunto de herramientas:

- Mediante las propiedades del conjunto de herramientas

- Mediante los métodos de la clase <xref:Microsoft.Build.Utilities.ToolLocationHelper>

Las propiedades del conjunto de herramientas especifican las rutas de acceso de las herramientas. A partir de Visual Studio 2017, MSBuild deja de tener una ubicación fija. Se encuentra de forma predeterminada en la carpeta *MSBuild\15.0\Bin* correspondiente a la ubicación de instalación de Visual Studio. En versiones anteriores, MSBuild usa el valor del atributo `ToolsVersion` del archivo de proyecto para encontrar la clave del Registro correspondiente y, después, usa la información de dicha clave para establecer las propiedades del conjunto de herramientas. Por ejemplo, si `ToolsVersion` tiene el valor `12.0`, MSBuild establece las propiedades del conjunto de herramientas conforme a esta clave del Registro: **HKLM\Software\Microsoft\MSBuild\ToolsVersions\12.0**.

 Estas son las propiedades del conjunto de herramientas:

- `MSBuildToolsPath` especifica la ruta de acceso de los archivos binarios de MSBuild.

- `SDK40ToolsPath` especifica la ruta de acceso de las herramientas administradas adicionales para MSBuild 4.x (que podría ser 4.0 o 4.5).

- `SDK35ToolsPath` especifica la ruta de acceso de las herramientas administradas adicionales para MSBuild 3,5.

Como alternativa, puede determinar el conjunto de herramientas mediante programación llamando a los métodos de la clase <xref:Microsoft.Build.Utilities.ToolLocationHelper>. La clase contiene estos métodos:

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A> devuelve la ruta de acceso de la carpeta de .NET Framework.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A> devuelve la ruta de acceso de un archivo de la carpeta .NET Framework.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A> devuelve la ruta de acceso de la carpeta de las herramientas administradas.

- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A> devuelve la ruta de acceso de un archivo, que normalmente se encuentra en la carpeta de las herramientas administradas.

- [GetPathToBuildTools](/previous-versions/visualstudio/visual-studio-2013/dn251121(v=vs.121)) devuelve la ruta de acceso de las herramientas de compilación.

### <a name="sub-toolsets"></a>Subconjuntos de herramientas

 En las versiones de MSBuild anteriores a 15.0, MSBuild usa una clave del registro para especificar la ruta de acceso de las herramientas básicas. Si la clave tiene una subclave, MSBuild la usa para especificar la ruta de acceso de un subconjunto de herramientas que contiene herramientas adicionales. En este caso, el conjunto de herramientas se define mediante la combinación de las definiciones de propiedades especificadas en ambas claves.

> [!NOTE]
> Si hay un conflicto entre los nombres de propiedades del conjunto de herramientas, el valor definido para la ruta de acceso de la subclave reemplaza al valor definido para la ruta de acceso de la clave raíz.

 Los subconjuntos de herramientas se activan si se define la propiedad de compilación `VisualStudioVersion`. Esta propiedad puede tener uno de estos valores:

- "10.0" especifica el subconjunto de herramientas de .NET Framework 4

- "11.0" especifica el subconjunto de herramientas de .NET Framework 4.5

- "12.0" especifica el subconjunto de herramientas de .NET Framework 4.5.1

Los subconjuntos de herramientas 10.0 y 11.0 deben usarse con ToolsVersion 4.0. En versiones posteriores, la versión del subconjunto de herramientas y ToolsVersion deben coincidir.

Durante una compilación, MSBuild automáticamente determina y establece un valor predeterminado para la propiedad `VisualStudioVersion` si no se ha definido aún.

MSBuild proporciona sobrecargas para los métodos de la clase `ToolLocationHelper` que agregan un valor enumerado `VisualStudioVersion` como parámetro.

Los subconjuntos de herramientas se incluyen por primera vez en .NET Framework 4.5.

## <a name="see-also"></a>Vea también

- [Configuraciones de conjuntos de herramientas estándar y personalizados](../msbuild/standard-and-custom-toolset-configurations.md)
- [Compatibilidad con múltiples versiones (multi-targeting)](../msbuild/msbuild-multitargeting-overview.md)
