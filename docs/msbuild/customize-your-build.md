---
title: Personalizar una compilación | Microsoft Docs
ms.date: 06/14/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 858d28ac2fdc6cab32e537e86f84771e0fb53f90
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53919565"
---
# <a name="customize-your-build-c-visual-basic"></a>Personalizar una compilación (C#, Visual Basic)

Los proyectos de MSBuild que usan el proceso de compilación estándar (la importación de *Microsoft.Common.props* y *Microsoft.Common.targets*) tienen varios enlaces de extensibilidad que se pueden usar para personalizar el proceso de compilación.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Adición de argumentos a las invocaciones de MSBuild de línea de comandos para el proyecto

Un archivo *Directory.Build.rsp* en el directorio de origen o por encima se aplica a las compilaciones de línea de comandos del proyecto. Para obtener más información, vea [Archivos de respuesta de MSBuild](../msbuild/msbuild-response-files.md#directorybuildrsp).

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory.Build.props y Directory.Build.targets

Antes de la versión 15 de MSBuild, si quería proporcionar una nueva propiedad personalizada a los proyectos de la solución, tenía que agregar manualmente una referencia a esa propiedad en cada archivo de proyecto de la solución. O, tenía que definir la propiedad en un archivo *.props* y, después, importar explícitamente el archivo *.props* en cada proyecto de la solución, entre otras cosas.

Pero ahora se puede agregar una propiedad nueva a cada proyecto en un paso si se define en un único archivo denominado *Directory.Build.props* en la carpeta raíz que contiene el código fuente. Cuando se ejecuta MSBuild, *Microsoft.Common.props* busca su estructura de directorio para el archivo *Directory.Build.props* (y *Microsoft.Common.targets* busca *Directory.Build.targets*). Si encuentra uno, importa la propiedad. *Directory.Build.props* es un archivo definido por el usuario que proporciona personalizaciones a los proyectos de un directorio.

> [!NOTE]
> Los sistemas de archivos basados en Linux distinguen mayúsculas de minúsculas. Asegúrese de que las mayúsculas y minúsculas del nombre del archivo Directory.Build.props coincidan de manera exacta o no se detectará durante el proceso de compilación.
>
> Consulte [este problema de GitHub](https://github.com/dotnet/core/issues/1991#issue-368441031) para más información.

### <a name="directorybuildprops-example"></a>Ejemplo de Directory.Build.props

Por ejemplo, si quisiera permitir que todos sus proyectos tuvieran acceso a la nueva característica **/deterministic** de Roslyn (que se expone en el destino `CoreCompile` de Roslyn mediante la propiedad `$(Deterministic)`), podría realizar lo siguiente.

1. Crear un archivo en la raíz de su repositorio denominado *Directory.Build.props*.
2. Agregar el siguiente XML al archivo.

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```
3. Ejecutar MSBuild. Las importaciones existentes del proyecto de *Microsoft.Common.props* y *Microsoft.Common.targets* encuentran el archivo y lo importan.

### <a name="search-scope"></a>Ámbito de búsqueda

Al buscar el archivo *Directory.Build.props*, MSBuild recorre la estructura del directorio hacia arriba desde la ubicación del proyecto (`$(MSBuildProjectFullPath)`), deteniéndose después de que encuentra un archivo *Directory.Build.props*. Por ejemplo, si su `$(MSBuildProjectFullPath)` fuera *c:\users\username\code\test\case1*, MSBuild empezaría a buscar allí y, después, buscaría en la estructura del directorio hacia arriba hasta que encontrara un archivo *Directory.Build.props*, como en la siguiente estructura de directorio.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

La ubicación del archivo de solución es irrelevante para *Directory.Build.props*.

### <a name="import-order"></a>Orden de importación

*Directory.Build.props* se importa muy pronto en *Microsoft.Common.props*, y las propiedades definidas después no están disponibles en él. Por tanto, evite hacer referencia a propiedades que todavía no están definidas (y que se van a evaluar como vacías).

*Directory.Build.targets* se importa desde *Microsoft.Common.targets* después de importar los archivos *.targets* de paquetes NuGet. Por tanto, puede reemplazar propiedades y destinos definidos en la mayoría de la lógica de compilación, pero a veces puede que necesite personalizar el archivo de proyecto después de la importación final.

### <a name="use-case-multi-level-merging"></a>Caso de uso: combinación de varios niveles

Imagínese que tiene esta estructura de solución estándar:

```
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
```

Puede que convenga tener propiedades comunes para todos los proyectos *(1)*, propiedades comunes para los proyectos *src* *(2-src)* y propiedades comunes para los proyectos *test* *(2-test)*.

Para que MSBuild combine correctamente los archivos "internos" (*2-src* y *2-test*) con el archivo "externo" (*1*), debe tener en cuenta que, cuando MSBuild encuentra un archivo *Directory.Build.props*, detiene el análisis. Para continuar con el análisis y efectuar la combinación con el archivo externo, coloque este código en ambos archivos internos:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

A continuación tiene un resumen del enfoque general de MSBuild:

- Para un proyecto dado, MSBuild busca el primer *Directory.Build.props* hacia arriba en la estructura de la solución, lo combina con valores predeterminados y detiene el análisis.
- Si quiere que se busquen y combinen varios niveles, efectúe una [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) (que se muestra arriba) del archivo "externo" desde el archivo "interno".
- Si el archivo "externo" no importa algo por encima de él, el análisis se detendrá en ese punto.
- Para controlar el proceso de análisis/combinación, use `$(DirectoryBuildPropsPath)` e `$(ImportDirectoryBuildProps)`.

O más sencillo: el primer *Directory.Build.props* que no importa nada es donde se detiene MSBuild.

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

De forma predeterminada, *Microsoft.Common.props* importa `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props` y *Microsoft.Common.targets* importa `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets`. El valor predeterminado de `MSBuildProjectExtensionsPath` es `$(BaseIntermediateOutputPath)`, `obj/`. NuGet usa este mecanismo para hacer referencia a la lógica de compilación que se entrega con paquetes, es decir, en tiempo de restauración, crea archivos `{project}.nuget.g.props` que hacen referencia al contenido del paquete.

Puede deshabilitar este mecanismo de extensibilidad si establece la propiedad `ImportProjectExtensionProps` en `false` en *Directory.Build.props* o antes de importar *Microsoft.Common.props*.

> [!NOTE]
> La deshabilitación de las importaciones de MSBuildProjectExtensionsPath impedirá que la lógica de compilación que se entrega en los paquetes NuGet se aplique al proyecto. Algunos paquetes NuGet requieren lógica de compilación para realizar su función y quedarán inutilizados si se deshabilita esta opción.

## <a name="user-file"></a>El archivo .user

*Microsoft.Common.CurrentVersion.targets* importa `$(MSBuildProjectFullPath).user`, si existe, para que pueda crear un archivo junto al proyecto con esa extensión adicional. Para cambios a largo plazo que se van a insertar en el repositorio de control de código fuente, es preferible cambiar el propio proyecto, para que en el futuro los encargados del mantenimiento no tengan que conocer este mecanismo de extensión.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath y MSBuildUserExtensionsPath

> [!WARNING]
> El uso de estos mecanismos de extensión hace más difícil obtener compilaciones repetibles entre equipos. Pruebe a usar una configuración que se pueda insertar en el repositorio de control de código fuente y compartir entre todos los desarrolladores del código base.

Por convención, muchos archivos de lógica de compilación principales importan

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

antes de su contenido, y

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

después. Esto permite que los SDK instalados aumenten la lógica de compilación de los tipos de proyecto comunes.

Se busca la misma estructura de directorios en `$(MSBuildUserExtensionsPath)`, que es la carpeta *%LOCALAPPDATA%\Microsoft\MSBuild* por usuario. Los archivos ubicados en esa carpeta se importarán para todas las compilaciones del tipo de proyecto correspondiente que se ejecuta con las credenciales del usuario. Puede deshabilitar las extensiones de usuario si establece propiedades con el mismo nombre que el archivo de importación con el patrón `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}`. Por ejemplo, si se establece `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` en `false` se impedirá la importación de `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*`.

## <a name="customize-the-solution-build"></a>Personalización de la compilación de la solución

> [!IMPORTANT]
> La personalización de la compilación de la solución de este modo solo se aplica a las compilaciones de línea de comandos con *MSBuild.exe*. **No** se aplica a las compilaciones dentro de Visual Studio.

Cuando MSBuild compila un archivo de solución, primero lo convierte internamente en un archivo de proyecto y, después, lo compila. El archivo de proyecto generado importa `before.{solutionname}.sln.targets` antes de definir los destinos y `after.{solutionname}.sln.targets` después de importarlos, incluidos los destinos instalados en los directorios `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` y `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter`.

Por ejemplo, se podría definir un destino nuevo para escribir un mensaje de registro personalizado después de compilar *MyCustomizedSolution.sln* mediante la creación de un archivo en el mismo directorio denominado *after.MyCustomizedSolution.sln.targets* que contiene

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

## <a name="see-also"></a>Vea también

[Conceptos de MSBuild](../msbuild/msbuild-concepts.md)

[Referencia de MSBuild](../msbuild/msbuild-reference.md)
