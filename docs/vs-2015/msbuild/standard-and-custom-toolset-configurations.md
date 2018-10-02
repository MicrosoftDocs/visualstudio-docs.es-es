---
title: Configuraciones de conjuntos de herramientas estándar y personalizados | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cbba44792fe004eb06de20d86bf5607af561107e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581670"
---
# <a name="standard-and-custom-toolset-configurations"></a>Configuraciones de conjuntos de herramientas estándar y personalizados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [configuraciones estándar y personalizados Toolset](https://docs.microsoft.com/visualstudio/msbuild/standard-and-custom-toolset-configurations).  
  
  
Un conjunto de herramientas de MSBuild contiene referencias a tareas, destinos y herramientas que puede usar para compilar un proyecto de aplicación. MSBuild incluye un conjunto de herramientas estándar, pero también puede crear conjuntos de herramientas personalizados. Para obtener información sobre cómo especificar un conjunto de herramientas, consulte [Conjunto de herramientas (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)  
  
## <a name="standard-toolset-configurations"></a>Configuraciones del conjunto de herramientas estándar  
 MSBuild 12.0 incluye los siguientes conjuntos de herramientas estándar:  
  
|ToolsVersion|Ruta de acceso del conjunto de herramientas (como se especifica en la propiedad de compilación MSBuildToolsPath o MSBuildBinPath)|  
|------------------|--------------------------------------------------------------------------------------------|  
|2.0|*Ruta de instalación de Windows*\Microsoft.Net\Framework\v2.0.50727\|  
|3.5|*Ruta de instalación de Windows*\Microsoft.Net\Framework\v3.5\|  
|4.0|*Ruta de instalación de Windows*\Microsoft.Net\Framework\v4.0.30319\|  
|12.0|*%ProgramFiles%* \MSBuild\12.0\bin|  
  
 El valor de `ToolsVersion` determina qué conjunto de herramientas usará un proyecto generado por Visual Studio. En [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] el valor predeterminado es "12.0" (con independencia de la versión especificada en el archivo del proyecto), pero es posible reemplazar ese atributo mediante el modificador **/toolsversion** en un símbolo del sistema. Para obtener información sobre este atributo y otras maneras de especificar el valor de `ToolsVersion`, consulte [Reemplazar la configuración de ToolsVersion](../msbuild/overriding-toolsversion-settings.md).  
  
 Si el valor de `ToolsVersion` no se especifica, la clave del Registro **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\\<Version Number\>\DefaultToolsVersion** define `ToolsVersion`, que siempre es 2.0.  
  
 Las claves del Registro siguiente especifican la ruta de instalación de MSBuild.exe.  
  
|Clave del Registro|Nombre de clave|Cadena (valor de clave)|  
|------------------|--------------|----------------------|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\2.0\|MSBuildToolsPath|Ruta de instalación de .NET Framework 2.0|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\|MSBuildToolsPath|Ruta de instalación de .NET Framework 3.5|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\|MSBuildToolsPath|Ruta de instalación de .NET Framework 4|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\12.0\|MSBuildToolsPath|Ruta de instalación de MSBuild|  
  
### <a name="sub-toolsets"></a>Subconjuntos de herramientas  
 Si la clave del Registro de la tabla anterior tiene una subclave, MSBuild la usa para determinar si la ruta de acceso de un subconjunto de herramientas puede reemplazar la ruta del conjunto de herramientas primario. La subclave siguiente muestra un ejemplo:  
  
 \HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0  
  
 Si se define alguna propiedad en el conjunto de herramientas base y el subconjunto de herramientas seleccionado, se usan las definiciones de propiedades del subconjunto de herramientas. Por ejemplo, el conjunto de herramientas de MSBuild 4,0 define `SDK40ToolsPath` para que apunte al SDK de 7.0A, pero el conjunto de herramientas de MSBuild 4.0\11.0 define la misma propiedad para que apunte al SDK de 8.0A. Si `VisualStudioVersion` no se establece, `SDK40ToolsPath` señalaría a 7.0A, pero si `VisualStudioVersion` se establece en 11.0, la propiedad señalaría en su lugar a 8.0A.  
  
 La propiedad de compilación `VisualStudioVersion` indica si un subconjunto de herramientas se activa. Por ejemplo, un valor de `VisualStudioVersion` de "12.0" especifica el subconjunto de herramientas de MSBuild 12.0. Para obtener más información, vea la sección de subconjuntos de herramientas de [Conjunto de herramientas (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).  
  
> [!NOTE]
>  Se recomienda no cambiar esta configuración. No obstante, puede agregar sus propios valores y especificar las definiciones del conjunto de herramientas personalizado para todos los equipos, como se describe en la sección siguiente.  
  
## <a name="custom-toolset-definitions"></a>Definiciones de conjuntos de herramientas personalizados  
 Cuando un conjunto de herramientas estándar no cumple sus requisitos de compilación, puede crear un conjunto de herramientas personalizado. Por ejemplo, puede tener un escenario de laboratorio de compilación en el que necesite un sistema independiente para compilar proyectos de [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]. Mediante un conjunto de herramientas personalizado, puede asignar valores personalizados al atributo `ToolsVersion` al crear proyectos o ejecutar MSBuild.exe. De este modo, también podrá usar la propiedad `$(MSBuildToolsPath)` para importar los archivos .targets de ese directorio, así como para definir sus propias propiedades de conjunto de herramientas personalizadas que puede usar en cualquier proyecto que utilice ese conjunto de herramientas.  
  
 Especifique un conjunto de herramientas personalizado en el archivo de configuración de MSBuild.exe (o de la herramienta personalizada que hospeda el motor de MSBuild si eso es lo que está usando). Por ejemplo, el archivo de configuración de MSBuild.exe podría incluir la siguiente definición de conjunto de herramientas si se deseaba invalidar el comportamiento predeterminado de ToolsVersion 12.0.  
  
```  
<msbuildToolsets default="12.0">  
   <toolset toolsVersion="12.0">  
      <property name="MSBuildToolsPath"   
        value="C:\SpecialPath" />  
   </toolset>  
</msbuildToolsets>  
```  
  
 `<msbuildToolsets>` también se debe definir en el archivo de configuración, de la siguiente manera.  
  
```  
<configSections>  
   <section name="msbuildToolsets"         
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,   
       Microsoft.Build.Engine, Version=12.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a"  
   </section>  
</configSections>  
```  
  
> [!NOTE]
>  Para que se lea correctamente, `<configSections>` debe ser la primera subsección de la sección `<configuration>`.  
  
 `ToolsetConfigurationSection` es una sección de configuración personalizada que puede usar cualquier host de MSBuild para la configuración personalizada. Si utiliza un conjunto de herramientas personalizado, un host no tiene que hacer nada para inicializar el motor de compilación excepto proporcionar las entradas del archivo de configuración. Definiendo las entradas del Registro, puede especificar conjuntos de herramientas para todos los equipos que se aplican a MSBuild.exe, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y todos los hosts de MSBuild.  
  
> [!NOTE]
>  Si un archivo de configuración define los valores de un elemento `ToolsVersion` ya definido en el Registro, las dos definiciones no se combinan. La definición del archivo de configuración tiene prioridad y los valores del Registro para ese elemento `ToolsVersion` se omiten.  
  
 Las propiedades siguientes son específicas del valor de `ToolsVersion` que se usa en los proyectos:  
  
-   **$(MSBuildBinPath)** se establece en el valor de `ToolsPath` especificado en el Registro o en el archivo de configuración donde se define `ToolsVersion`. El valor de `$(MSBuildToolsPath)` en el Registro o en el archivo de configuración especifica la ubicación de las tareas y los destinos básicos. En el archivo de proyecto, se asigna a la propiedad $(MSBuildBinPath) y también a la propiedad $(MSBuildToolsPath).  
  
-   `$(MSBuildToolsPath)` es una propiedad reservada que proporciona la propiedad MSBuildToolsPath especificada en el archivo de configuración. (Esta propiedad reemplaza a `$(MSBuildBinPath)`. Sin embargo, `$(MSBuildBinPath)` se mantiene por motivos de compatibilidad). Un conjunto de herramientas personalizado debe definir `$(MSBuildToolsPath)` o `$(MSBuildBinPath)` pero no ambos, a no ser que ambos tengan el mismo valor.  
  
 También puede agregar propiedades personalizadas específicas de ToolsVersion al archivo de configuración con la misma sintaxis utilizada para agregar la propiedad MSBuildToolsPath. Para que estas propiedades personalizadas están disponibles para el archivo de proyecto, use el mismo nombre que el del valor especificado en el archivo de configuración. En el archivo de configuración se pueden definir conjuntos de herramientas, pero no subconjuntos de herramientas.  
  
## <a name="see-also"></a>Vea también  
 [Conjunto de herramientas (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)



