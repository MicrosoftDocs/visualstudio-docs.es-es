---
title: Directiva Include T4
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a1ee58c29be3c4dfb5e2148c54464a7a511d1839
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591858"
---
# <a name="t4-include-directive"></a>Directiva Include T4

En una plantilla de texto de Visual Studio, puede incluir texto de otro archivo mediante una directiva de `<#@include#>`. Puede colocar directivas `include` en cualquier parte de una plantilla de texto antes del primer bloque de características de clase `<#+ ... #>`. Los archivos incluidos también pueden contener directivas `include`, así como otras directivas. Esto le permite compartir código de plantilla y texto reutilizable entre plantillas.

## <a name="using-include-directives"></a>Usar directivas include

```
<#@ include file="filePath" [once="true"] #>
```

- `filePath` puede ser absoluta o relativa al archivo de plantilla actual.

   Además, las extensiones de Visual Studio específicas pueden especificar sus propios directorios para buscar archivos de inclusión. Por ejemplo, si ha instalado el SDK de visualización y modelado (herramientas de DSL), se agrega la siguiente carpeta a la lista de inclusión: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates`.

   Estas carpetas de inclusión adicionales podrían depender de la extensión de archivo del archivo para incluir. Por ejemplo, la carpeta de inclusión de las Herramientas ADSL solo es accesible para la inclusión de archivos que tienen la extensión de archivo `.tt`

- `filePath` pueden incluir variables de entorno delimitadas con "%." Por ejemplo:

  ```
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>
  ```

- El nombre de un archivo incluido no tiene que utilizar la extensión `".tt"`.

   Puede que desee utilizar otra extensión, como `".t4"`, para los archivos incluidos. Esto se debe a que, cuando se agrega un archivo de `.tt` a un proyecto, Visual Studio establece automáticamente la propiedad de la **herramienta personalizada** en `TextTemplatingFileGenerator`. Normalmente no desea que los archivos incluidos se transformen individualmente.

   Por otra parte, debe tener en cuenta que en algunos casos, la extensión de archivo afecta a las carpetas adicionales que se buscarán para archivos de inclusión. Esto podría ser importante al tener un archivo incluido que incluye otros archivos.

- El contenido incluido se procesa casi como si formase parte de la plantilla de texto que lo incluye. Sin embargo, puede incluir un archivo que contenga un bloque de características de clase `<#+...#>` aunque la directiva `include` vaya seguida de texto normal y bloques de control estándar.

- Use `once="true"` para asegurarse de que una plantilla se incluye una sola vez, aunque se invoque desde más de un archivo de inclusión.

   Esta característica facilita la creación de una biblioteca de fragmentos de código T4 reutilizables que se pueden incluir en, sin preocuparse de que algún otro fragmento de código ya los haya incluido.  Por ejemplo, supongamos que tiene una biblioteca de fragmentos de código muy específicos que se ocupan de la C# generación y el procesamiento de plantillas.  A su vez, se usan en algunas otras utilidades específicas de la tarea, como la generación de excepciones, que puede usar a partir de cualquier plantilla más específica de la aplicación. Si dibuja el gráfico de dependencias, verá que algunos fragmentos de código se incluyeron varias veces. Sin embargo, el parámetro `once` evita las inclusiones siguientes.

  **MyTextTemplate.tt:**

```
<#@ output extension=".txt" #>
Output message 1 (from top template).
<#@ include file="TextFile1.t4"#>
Output message 5 (from top template).
<#
   GenerateMessage(6); // defined in TextFile1.t4
   AnotherGenerateMessage(7); // defined in TextFile2.t4
#>
```

 **TextFile1.t4:**

```
   Output Message 2 (from included file).
<#@ include file="TextFile2.t4" #>
   Output Message 4 (from included file).
<#+ // Start of class feature control block.
void GenerateMessage(int n)
{
#>
   Output Message <#= n #> (from GenerateMessage method).
<#+
}
#>
```

 **TextFile2.t4:**

```
        Output Message 3 (from included file 2).
<#+ // Start of class feature control block.
void AnotherGenerateMessage(int n)
{
#>
       Output Message <#= n #> (from AnotherGenerateMessage method).
<#+
}
#>
```

 **El archivo generado resultante, MyTextTemplate. txt:**

```
Output message 1 (from top template).
   Output Message 2 (from included file).
        Output Message 3 (from included file 2).

   Output Message 4 (from included file).

Output message 5 (from top template).
   Output Message 6 (from GenerateMessage method).
       Output Message 7 (from AnotherGenerateMessage method).
```

## <a name="msbuild"></a>Usar las propiedades del proyecto en MSBuild y Visual Studio
 Aunque puede usar macros de Visual Studio como $ (SolutionDir) en una directiva Include, no funcionan en MSBuild. Si desea transformar plantillas del equipo de compilación, tiene que utilizar las propiedades del proyecto.

 Modifique el archivo .csproj o .vbproj para definir una propiedad de proyecto. En este ejemplo se define una propiedad denominada `myIncludeFolder`:

```xml
<!-- Define a project property, myIncludeFolder: -->
<PropertyGroup>
    <myIncludeFolder>$(MSBuildProjectDirectory)\..\libs</myIncludeFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myIncludeFolder">
      <Value>$(myIncludeFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

 Ahora puede utilizar la propiedad del proyecto en plantillas de texto, que se transformarán correctamente en Visual Studio y MSBuild:

```
<#@ include file="$(myIncludeFolder)\defs.tt" #>
```
