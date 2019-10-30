---
title: Actualización de una aplicación existente a MSBuild 15 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a891f6d18657bad65a1cf087da975849642b7aec
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72912034"
---
# <a name="update-an-existing-application-for-msbuild-15"></a>Actualización de una aplicación existente a MSBuild 15

En las versiones de MSBuild anteriores a 15.0, MSBuild se cargaba desde la caché global de ensamblados (GAC) y las extensiones de MSBuild se instalaban en el Registro. Así se garantizaba que todas las aplicaciones usaran la misma versión de MSBuild y tuvieran acceso a los mismos conjuntos de herramientas, pero se evitaban instalaciones en paralelo de distintas versiones de Visual Studio.

Para permitir una instalación más rápida, reducida y en paralelo, Visual Studio 2017 y las versiones posteriores ya no colocan MSBuild en la GAC ni modifican el Registro. Lamentablemente, esto significa que las aplicaciones que quieren usar la API de MSBuild para evaluar o compilar proyectos, no pueden confiar de forma implícita en la instalación de Visual Studio.

## <a name="use-msbuild-from-visual-studio"></a>Uso de MSBuild desde Visual Studio

Para garantizar que las compilaciones mediante programación de la aplicación coincidan con las realizadas en Visual Studio o *MSBuild.exe*, cargue los ensamblados de MSBuild desde Visual Studio y use los SDK disponibles en Visual Studio. El paquete NuGet Microsoft.Build.Locator simplifica este proceso.

## <a name="use-microsoftbuildlocator"></a>Uso de Microsoft.Build.Locator

Si redistribuye *Microsoft.Build.Locator.dll* con la aplicación, no tendrá que distribuir otros ensamblados de MSBuild.

La actualización de un proyecto para usar MSBuild 15 y la API de localizador requieren algunos cambios en el proyecto, que se describen a continuación. Para ver un ejemplo de los cambios necesarios para actualizar un proyecto, vea [las confirmaciones realizadas en un proyecto de ejemplo en el repositorio de MSBuildLocator](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15).

### <a name="change-msbuild-references"></a>Cambiar referencias de MSBuild

Para garantizar que MSBuild se cargue desde una ubicación central, no debe distribuir sus ensamblados con la aplicación.

El mecanismo para cambiar el proyecto para evitar la carga de MSBuild desde una ubicación central depende de cómo se haga referencia a MSBuild.

#### <a name="use-nuget-packages-preferred"></a>Uso de paquetes NuGet (preferido)

En estas instrucciones se da por hecho que usa las [referencias NuGet de estilo PackageReference](/nuget/consume-packages/package-references-in-project-files).

Cambie los archivos de proyecto para hacer referencia a ensamblados de MSBuild desde sus paquetes NuGet. Especifique `ExcludeAssets=runtime` para indicar a NuGet que los ensamblados son necesarios solo en tiempo de compilación y no deben copiarse en el directorio de salida.

La versión principal y secundaria de los paquetes de MSBuild debe ser menor o igual que la versión mínima de Visual Studio que quiere permitir. Por ejemplo, si quiere admitir Visual Studio 2017 y versiones posteriores, haga referencia a la versión `15.1.548` del paquete.

Por ejemplo, puede usar este XML:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities.Core" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="use-extension-assemblies"></a>Uso de ensamblados de extensión

Si no puede usar paquetes NuGet, puede hacer referencia a ensamblados de MSBuild distribuidos con Visual Studio. Si hace referencia a MSBuild directamente, para asegurarse de que no se copie en el directorio de salida, establezca `Copy Local` en `False`. En el archivo del proyecto, esta configuración tendrá el aspecto siguiente:

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>Redirecciones de enlaces

Haga referencia al paquete de Microsoft.Build.Locator para asegurarse de que la aplicación use automáticamente las redirecciones de enlaces necesarias a la versión 15.1.0.0. Las redirecciones de enlace a esta versión admiten MSBuild 15 y MSBuild 16.

### <a name="ensure-output-is-clean"></a>Asegurarse de que la salida sea limpia

Compile el proyecto e inspeccione el directorio de salida para asegurarse de que no contiene ningún ensamblado *Microsoft.Build.\*.dll* que no sea *Microsoft.Build.Locator.dll*, agregado en el paso siguiente.

### <a name="add-package-reference-for-microsoftbuildlocator"></a>Adición de una referencia de paquete a Microsoft.Build.Locator

Agregue una referencia de paquete NuGet a [Microsoft.Build.Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/).

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.1.2</Version>
    </PackageReference>
```

No especifique `ExcludeAssets=runtime` para el paquete de Microsoft.Build.Locator.

### <a name="register-instance-before-calling-msbuild"></a>Registrar instancia antes de llamar a MSBuild

Agregue una llamada a la API de localizador antes de llamar a cualquier método que use MSBuild.

La manera más sencilla de agregar la llamada a la API de localizador es agregar una llamada a

```csharp
MSBuildLocator.RegisterDefaults();
```

en el código de inicio de la aplicación.

Si quiere un control más preciso sobre la carga de MSBuild, puede seleccionar un resultado de `MSBuildLocator.QueryVisualStudioInstances()` para pasarlo a `MSBuildLocator.RegisterInstance()` manualmente, pero esto normalmente no es necesario.
