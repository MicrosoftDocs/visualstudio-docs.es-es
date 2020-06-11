---
title: Personalizar una compilación | Microsoft Docs
ms.date: 06/13/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b0cb05948f8010964eefe101cbc77d48a149566
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2020
ms.locfileid: "84180407"
---
# <a name="customize-your-build"></a>Personalizar una compilación

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

Las propiedades que se establecen en *Directory.Build.props* pueden reemplazarse en cualquier parte del archivo de proyecto o en archivos importados, por lo que debe pensar en la configuración de *Directory.Build.props* como la especificación de los valores predeterminados de los proyectos.

*Directory.Build.targets* se importa desde *Microsoft.Common.targets* después de importar los archivos *.targets* de paquetes NuGet. Por lo tanto, puede invalidar las propiedades y los destinos definidos en la mayor parte de la lógica de compilación, o bien, establecer las propiedades de todos los proyectos independientemente de lo que establezcan los proyectos individuales.

Cuando tenga que establecer una propiedad o definir un destino para un proyecto individual que invalide cualquier configuración anterior, coloque esa lógica en el archivo de proyecto después de la importación final. Para hacer esto en un proyecto de estilo SDK, primero debe reemplazar el atributo de estilo SDK por las importaciones equivalentes. [Procedimiento para usar los SDK de proyecto de MSBuild](how-to-use-project-sdk.md).

> [!NOTE]
> El motor de MSBuild lee todos los archivos importados durante la evaluación, antes de iniciar la ejecución de la compilación de cualquier proyecto (incluido cualquier `PreBuildEvent`), por lo que no se espera que estos archivos se modifiquen en `PreBuildEvent` ni en ninguna otra parte del proceso de compilación. Las modificaciones no surtirán efecto hasta la siguiente invocación de *MSBuild.exe* o la siguiente compilación de Visual Studio.

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

Puede que convenga tener propiedades comunes para todos los proyectos *(1)* , propiedades comunes para los proyectos *src* *(2-src)* y propiedades comunes para los proyectos *test* *(2-test)* .

Para que MSBuild combine correctamente los archivos "internos" (*2-src* y *2-test*) con el archivo "externo" (*1*), debe tener en cuenta que, cuando MSBuild encuentra un archivo *Directory.Build.props*, detiene el análisis. Para continuar con el análisis y efectuar la combinación con el archivo externo, coloque este código en ambos archivos internos:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

A continuación tiene un resumen del enfoque general de MSBuild:

- Para un proyecto dado, MSBuild busca el primer *Directory.Build.props* hacia arriba en la estructura de la solución, lo combina con valores predeterminados y detiene el análisis.
- Si quiere que se busquen y combinen varios niveles, efectúe una [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) (que se muestra arriba) del archivo "externo" desde el archivo "interno".
- Si el archivo "externo" no importa algo por encima de él, el análisis se detendrá en ese punto.
- Para controlar el proceso de análisis/combinación, use `$(DirectoryBuildPropsPath)` e `$(ImportDirectoryBuildProps)`.

O más sencillo: el primer *Directory.Build.props* que no importa nada es donde se detiene MSBuild.

### <a name="choose-between-adding-properties-to-a-props-or-targets-file"></a>Elección entre la adición de propiedades a un archivo .props o .targets

MSBuild depende del orden de importación y la última definición de una propiedad (o una `UsingTask` o destino) es la definición usada.

Al usar importaciones explícitas, puede importar desde un archivo *.props* o *.targets* en cualquier momento. Esta es la convención que se usa ampliamente:

- Los archivos *.props* se importan de forma temprana en el orden de importación.

- Los archivos *.targets*  se importan de forma tardía en el orden de compilación.

Las importaciones `<Project Sdk="SdkName">` aplican esta convención (es decir, primero se muestra la importación de *Sdk.props*, antes que todo el contenido del archivo, para después hacerlo la de *Sdk.targets*, después de todo este contenido).

Para decidir dónde colocar las propiedades, use las siguientes instrucciones generales:

- En el caso de que sean muchas las propiedades, no importa dónde se definan, ya que no se sobrescriben y serán de solo lectura en tiempo de ejecución.

- Para un comportamiento que podría personalizarse en un proyecto individual, establezca valores predeterminados en los archivos *.props*.

- Evite el establecimiento de propiedades dependientes en los archivos *.props* leyendo el valor de una propiedad posiblemente personalizada, ya que la personalización no tendrá lugar hasta que MSBuild lea el proyecto del usuario.

- Establezca propiedades dependientes en los archivos *.targets*, ya que recogerán personalizaciones de proyectos individuales.

- Si tiene que reemplazar propiedades, hágalo en un archivo *.targets*, después de que todas las personalizaciones de proyecto de usuario hayan tenido la oportunidad de surtir efecto. Tenga cuidado al usar propiedades derivadas, ya que también puede ser necesario reemplazarlas.

- Incluya elementos en los archivos *.props* (condicionados por una propiedad). Se tienen en cuenta todas las propiedades antes que cualquier artículo, por lo que se recogen personalizaciones de propiedades de proyecto de usuario, lo que proporciona al proyecto del usuario la oportunidad de `Remove` o `Update` cualquier elemento incorporado por la importación.

- Defina los destinos en los archivos *.targets*. Sin embargo, si un SDK importa el archivo *.targets*, recuerde que este escenario aumenta la dificultad del reemplazo del destino, ya que el proyecto del usuario carece de un lugar para reemplazarlo de forma predeterminada.

- Si es posible, opte por la personalización de propiedades en tiempo de evaluación en lugar del cambio de las mismas dentro de un destino. Esta instrucción hace que resulte más fácil cargar un proyecto y saber lo que hace.

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

después. Esta convención permite que los SDK instalados aumenten la lógica de compilación de los tipos de proyecto comunes.

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

La compilación de la solución es independiente de las compilaciones del proyecto, por lo que la configuración aquí no afecta a las compilaciones del proyecto.

## <a name="customize-all-net-builds"></a>Personalización de todas las compilaciones de .NET

Al mantener un servidor de compilación, puede que tenga que configurar las opciones de MSBuild globalmente para todas las compilaciones en el servidor.  En principio, puede modificar los archivos globales *Microsoft.Common.Targets* o *Microsoft.Common.Props*, aunque hay una manera mejor de hacerlo. Puede incidir en todas las compilaciones de un determinado tipo de proyecto (por ejemplo, todos los proyectos de C#) usando ciertas propiedades de MSBuild y agregando determinados archivos `.targets` y `.props` personalizados.

Para incidir en todas las compilaciones de C# o Visual Basic regidas por una instalación de MSBuild o Visual Studio, cree un archivo *Custom.Before.Microsoft.Common.Targets* o *Custom.After.Microsoft.Common.Targets* con destinos que se ejecutarán antes o después de *Microsoft.Common.targets*, o un archivo *Custom.Before.Microsoft.Common.Props* o *Custom.After.Microsoft.Common.Props* con propiedades que se procesarán antes o después de *Microsoft.Common.props*.

Puede especificar las ubicaciones de estos archivos mediante las siguientes propiedades de MSBuild:

- CustomBeforeMicrosoftCommonProps
- CustomBeforeMicrosoftCommonTargets
- CustomAfterMicrosoftCommonProps
- CustomAfterMicrosoftCommonTargets
- CustomBeforeMicrosoftCSharpProps
- CustomBeforeMicrosoftVisualBasicProps
- CustomAfterMicrosoftCSharpProps
- CustomAfterMicrosoftVisualBasicProps
- CustomBeforeMicrosoftCSharpTargets
- CustomBeforeMicrosoftVisualBasicTargets
- CustomAfterMicrosoftCSharpTargets
- CustomAfterMicrosoftVisualBasicTargets

Las versiones *comunes* de estas propiedades afectan a los proyectos de C# y Visual Basic. Puede establecer estas propiedades en la línea de comandos de MSBuild.

```cmd
msbuild /p:CustomBeforeMicrosoftCommonTargets="C:\build\config\Custom.Before.Microsoft.Common.Targets" MyProject.csproj
```

El método más oportuno depende de su escenario. Con la extensibilidad de Visual Studio, puede personalizar el sistema de compilación y proporcionar un mecanismo para instalar y administrar las personalizaciones.

Si tiene un servidor de compilación dedicado y desea asegurarse de que determinados destinos se ejecuten siempre en todas las compilaciones del tipo de proyecto adecuado que se ejecutan en ese servidor, resulta adecuado usar un archivo `.targets` o `.props` personalizado global.  Si desea que los destinos personalizados solo se ejecuten cuando se aplican ciertas condiciones, use otra ubicación de archivo y establezca la ruta de acceso a ese archivo estableciendo la propiedad de MSBuild adecuada en la línea de comandos de MSBuild solo cuando sea necesario.

> [!WARNING]
> Visual Studio usa los archivos `.targets` o `.props` personalizados si los encuentra en la carpeta MSBuild cada vez que compila cualquier proyecto del tipo coincidente. Esto puede tener consecuencias no deseadas y, si se realiza incorrectamente, puede deshabilitar la capacidad de Visual Studio para compilar en el equipo.

## <a name="customize-c-builds"></a>Personalización de compilaciones de C++

En el caso de los proyectos de C++, los archivos *.targets* y *.props* personalizados que se han mencionado anteriormente no se pueden usar de la misma manera para invalidar la configuración predeterminada. *Directory.Build.props* se importa mediante *Microsoft.Common.props*, que se importa en `Microsoft.Cpp.Default.props` mientras que la mayoría de los valores predeterminados se definen en *Microsoft.Cpp.props* y, para una serie de propiedades, no se puede usar una condición "si aún no se ha definido", ya que la propiedad ya está definida, pero el valor predeterminado debe ser diferente para determinadas propiedades de proyecto definidas en `PropertyGroup` con `Label="Configuration"` (consulte [Estructura de los archivos .vcxproj y .props](/cpp/build/reference/vcxproj-file-structure)).

Sin embargo, puede utilizar las siguientes propiedades para especificar que los archivos *.props* se importen automáticamente antes o después de los archivos *Microsoft.cpp.\** :

- ForceImportAfterCppDefaultProps
- ForceImportBeforeCppProps
- ForceImportAfterCppProps
- ForceImportBeforeCppTargets
- ForceImportAfterCppTargets

Para personalizar los valores predeterminados de las propiedades de todas las compilaciones de C++, cree otro archivo *.props* (por ejemplo, *MyProps.props*) y defina la propiedad `ForceImportAfterCppProps` en `Directory.Build.props` apuntando a él:

<PropertyGroup> <ForceImportAfterCppProps>$(MsbuildThisFileDirectory)\MyProps.props<ForceImportAfterCppProps>
</PropertyGroup>

*MyProps.props* se importará automáticamente al final de *Microsoft.Cpp.props*.

## <a name="customize-all-c-builds"></a>Personalización de todas las compilaciones de C++

No se recomienda personalizar la instalación de Visual Studio, ya que no es fácil realizar un seguimiento de estas personalizaciones, pero si está ampliando Visual Studio para personalizar las compilaciones de C++ para una plataforma determinada, puede crear archivos de `.targets` para cada plataforma y colocarlos en las carpetas de importación correspondientes a esas plataformas como parte de una extensión de Visual Studio.

El archivo `.targets` para la plataforma Win32, *Microsoft.Cpp.Win32.targets*, contiene el siguiente elemento `Import`:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportBefore\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportBefore')"
/>
```

Hay un elemento similar cerca del final del mismo archivo:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportAfter\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportAfter')"
/>
```

Existen elementos de importación similares para otras plataformas de destino en *%ProgramFiles32%\MSBuild\Microsoft.Cpp\v{version}\Platforms\*.

Una vez que coloque el archivo `.targets` en la carpeta `ImportAfter` correspondiente según la plataforma, MSBuild importará el archivo en cada compilación de C++ de esa plataforma. Puede colocar ahí varios archivos de `.targets`, si es necesario. 

Con Extensibilidad de Visual Studio, pueden realizarse más personalizaciones, como la definición de una nueva plataforma. Para obtener más información, consulte [Extensibilidad de proyectos de C++](../extensibility/visual-cpp-project-extensibility.md).

### <a name="specify-a-custom-import-on-the-command-line"></a>Especificación de una importación personalizada en la línea de comandos

En el caso de los `.targets` personalizados que desee incluir para una compilación específica de un proyecto de C++, establezca una o las dos propiedades `ForceImportBeforeCppTargets` y `ForceImportAfterCppTargets` en la línea de comandos.

```cmd
msbuild /p:ForceImportBeforeCppTargets="C:\build\config\Custom.Before.Microsoft.Cpp.Targets" MyCppProject.vcxproj
```

En el caso de una configuración global (para incidir, por ejemplo, en todas las compilaciones de C++ de una plataforma en un servidor de compilación), hay dos métodos. En primer lugar, puede establecer estas propiedades mediante una variable de entorno del sistema que siempre se establece. Esto funciona porque MSBuild siempre lee el entorno y crea (o invalida) propiedades para todas las variables de entorno.

## <a name="see-also"></a>Vea también

- [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)

- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
