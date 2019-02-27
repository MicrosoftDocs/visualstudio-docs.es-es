---
title: Procedimiento Modificar archivos web.config para instrumentar y generar perfiles de aplicaciones web ASP.NET compiladas dinámicamente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 925112de25a127d4664bb66d602ca137ad624f70
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616695"
---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>Procedimiento Modificar archivos web.config para instrumentar y generar perfiles de aplicaciones web ASP.NET compiladas dinámicamente
Puede usar el método de instrumentación de las herramientas de generación de perfiles [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para recopilar datos detallados de tiempo, los datos de asignación de memoria de .NET y datos de duración de objetos .NET de aplicaciones web compiladas de forma dinámica [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

 En este tema se describe cómo modificar el archivo de configuración *web.config* para habilitar la instrumentación y la generación de perfiles de aplicaciones web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

> [!NOTE]
>  No es necesario modificar el archivo *web.config* cuando se usa el método de generación de perfiles de muestreo o cuando se quiere instrumentar un módulo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilado previamente.

 La raíz de un archivo *web.config* es el elemento **configuration**. Para instrumentar y generar perfiles de una aplicación web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilada dinámicamente, debe agregar o modificar los siguientes elementos:

- Un elemento **configuration/runtime/assemblyBinding/dependentAssembly** que identifica el ensamblado Microsoft.VisualStudio.Enterprise.ASPNetHelper que controla la generación de perfiles. El elemento **dependentAssembly** contiene dos elementos secundarios: **assemblyIdentity** y **codeBase**.

- Un elemento **configuration/system.web/compilation** que identifica el paso de compilación posterior al proceso del generador de perfiles para el ensamblado de destino.

- Dos elementos **add** que identifican la ubicación de las herramientas de generación de perfiles se agregan a la sección **configuration/appSettings**.

  Le recomendamos que cree una copia del archivo *web.config* original que pueda usar para restaurar la configuración de la aplicación.

### <a name="to-add-the-aspnethelper-assembly-as-a-configurationruntimeassemblybindingdependentassembly-element"></a>Para agregar el ensamblado ASPNetHelper como un elemento configuration/runtime/assemblyBinding/dependentAssembly

1. Si es necesario, agregue el elemento **runtime** como un elemento secundario del elemento **configuration**; en caso contrario, vaya al siguiente paso.

    El elemento **runtime** no tiene atributos. El elemento **configuration** solo puede tener un elemento secundario **runtime**.

2. Si es necesario, agregue el elemento **assemblyBinding** como un elemento secundario del elemento **runtime**; en caso contrario, vaya al siguiente paso.

    El elemento **runtime** solo puede tener un elemento **assemblyBinding**.

3. Agregue el siguiente nombre y valor de atributo para el elemento **assemblyBinding**:


   | Nombre de atributo | Valor del atributo |
   |----------------|--------------------------------------|
   | **Xmlns** | **urn:schemas-microsoft-com:asm.v1** |


4. Agregue un elemento **dependentAssembly** como un elemento secundario del elemento **assemblyBinding**.

    El elemento **dependentAssembly** no tiene atributos.

5. Agregue un elemento **assemblyIdentity** como elemento secundario del elemento **dependentAssembly**.

6. Agregue el siguiente nombre y valor de atributo para el elemento **assemblyIdentity**:


   | Nombre de atributo | Valor del atributo |
   |--------------------| - |
   | **name** | **Microsoft.VisualStudio.Enterprise.ASPNetHelper** |
   | **PublicKeyToken** | **b03f5f7f11d50a3a** |
   | **culture** | **Neutral** |


7. Agregue un elemento **codeBase** como elemento secundario del elemento **dependentAssembly**.

8. Agregue el siguiente nombre y valor de atributo para el elemento **codeBase**:

   |Nombre de atributo|Valor del atributo|
   |--------------------|---------------------|
   |**version**|**10.0.0.0**|
   |**href**|`PathToASPNetHelperDll`|

    `PathToASPNetHelperDll` es la dirección URL del archivo Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll. Si [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] está instalado en la ubicación predeterminada, el valor **href** debería ser: `C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL`

```xml
    <configuration>
        <runtime>
            <assemblyBinding
                xmlns="urn:schemas-microsoft-com:asm.v1"
            >
                <dependentAssembly>
                    <assemblyIdentity name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"
                        publicKeyToken="b03f5f7f11d50a3a"
                        culture="neutral"
                    />
                    <codeBase
                        version="10.0.0.0"
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"
                    />
                </dependentAssembly>
            </assemblyBinding>
        </runtime>
```

### <a name="to-add-the-profiler-post-process-step-to-the-configurationsystemwebcompilation-element"></a>Para agregar el paso posterior al proceso del generador de perfiles al elemento configuration/system.web/compilation

1.  Si es necesario, agregue el elemento **system.web** como un elemento secundario del elemento **configuration**; en caso contrario, vaya al siguiente paso.

     El elemento **system.web** no tiene atributos. El elemento **configuration** solo puede tener un elemento secundario **system.web**.

2.  Si es necesario, agregue el elemento **compilation** como un elemento secundario del elemento **system.web**, en caso contrario, vaya al siguiente paso.

     El elemento **system.web** solo puede tener un elemento secundario **compilation**.

3.  Quite cualquier atributo existente del elemento **compilation** y agregue el siguiente nombre y valor de atributo:

    |Nombre de atributo|Valor del atributo|
    |--------------------|---------------------|
    |**assemblyPostProcessorType**|**Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter, Microsoft.VisualStudio.Enterprise.ASPNetHelper, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a**|

```xml
    <configuration>
        <runtime>
        . . .
        </runtime>
        <system.web>
            <compilation
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,
                    Version=10.0.0.0,
                    Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            />
        </system.web>
    <configuration>
```

### <a name="to-add-profiler-location-settings-to-the-configurationappsettings-element"></a>Para agregar valores de ubicación del generador de perfiles al elemento configuration/appSettings

1. Si es necesario, agregue el elemento **system.appSettings** como un elemento secundario del elemento **configuration**; en caso contrario, vaya al siguiente paso.

    El elemento **system.appSettings** no tiene atributos. El elemento **configuration** solo puede tener un elemento secundario **appSettings**.

2. Agregue un elemento **add** como elemento secundario del elemento **appSettings**.

3. Agregue el siguiente nombre y valor de atributo para el elemento **add**:


   | Nombre de atributo | Valor del atributo |
   |----------------| - |
   | **key** | **Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation** |
   | **value** | `PerformanceToolsFolder` **\VSInstr.Exe** |


4. Agregue otro elemento **add** como elemento secundario del elemento **appSettings**.

5. Agregue el siguiente nombre y valor de atributo para este elemento **add**:

   |Nombre de atributo|Valor del atributo|
   |--------------------|---------------------|
   |**key**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools**|
   |**value**|`PerformanceToolsFolder`|

    `PerformanceToolsFolder` es la ruta de acceso de los archivos ejecutables del generador de perfiles. Para obtener la ruta de acceso a las herramientas de generación de perfiles, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).


```xml
    <configuration>
        <runtime>
        . . .
        </runtime>
        . . .
        <system.web>
        </system.web>
        <appSettings>
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\vsinstr.exe"
        />
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\"
            />
        </appSettings>
    </configuration>
```

## <a name="example"></a>Ejemplo
 El siguiente es un archivo *web.config* completo que habilita la instrumentación y la generación de perfiles de aplicaciones web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compiladas dinámicamente. En este ejemplo se supone que no había ninguna otra configuración en el archivo antes de la modificación.

```xml
<?xml version="1.0"?>
    <configuration>
        <runtime>
            <assemblyBinding
                xmlns="urn:schemas-microsoft-com:asm.v1"
            >
                <dependentAssembly>
                    <assemblyIdentity
                        name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"
                        publicKeyToken="b03f5f7f11d50a3a"
                        culture="neutral"
                    />
                    <codeBase
                        version="10.0.0.0"
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"
                    />
                </dependentAssembly>
            </assemblyBinding>
        </runtime>
        <system.web>
            <compilation
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,
                    Version=10.0.0.0,
                    Culture=neutral,
                    PublicKeyToken=b03f5f7f11d50a3a"
            />
        </system.web>
        <appSettings>
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\vsinstr.exe"
            />
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\"
            />
        </appSettings>
    </configuration>

```

## <a name="see-also"></a>Vea también
- [Cómo: Instrumentar una aplicación web ASP.NET compilada dinámicamente y recopilar datos detallados de control de tiempo](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)
- [Cómo: Instrumentar una aplicación ASP.NET compilada dinámicamente y recopilar datos de memoria](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)