---
title: Elementos comunes de proyectos de MSBuild | Microsoft Docs
description: Conozca los elementos comunes de proyectos de MSBuild. Los elementos son referencias con nombre a uno o varios archivos y tienen metadatos como nombres de archivo, rutas de acceso y números de versión.
ms.custom: SEO-VS-2020
ms.date: 10/29/2020
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, common project items
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cd43be13351309e0f4715ee889fb910f4f7e49a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963203"
---
# <a name="common-msbuild-project-items"></a>Elementos comunes de proyectos de MSBuild

En MSBuild, un elemento es una referencia con nombre a uno o varios archivos. Los elementos contienen metadatos como nombres de archivo, rutas de acceso y números de versión. Todos los tipos de proyecto de Visual Studio tienen varios elementos en común. Estos elementos se definen en el archivo *Microsoft.Build.CommonTypes.xsd*.

## <a name="common-items"></a>Elementos comunes

A continuación, se muestra una lista de todos los elementos de proyecto comunes.

### <a name="reference"></a>Referencia

Representa una referencia de ensamblado (administrada) del proyecto.

|Nombre de metadatos de elementos|Descripción|
|---------------|-----------------|
|HintPath|Cadena opcional. Ruta de acceso absoluta o relativa del ensamblado.|
|NOMBRE|Cadena opcional. Nombre para mostrar del ensamblado, por ejemplo, "System.Windows.Forms".|
|FusionName|Cadena opcional. Especifica el nombre de fusión sencillo o seguro del elemento.<br /><br /> Cuando este atributo está presente se ahorra tiempo, ya que no es necesario abrir el archivo de ensamblado para obtener el nombre de fusión.|
|SpecificVersion|Booleano opcional. Especifica si solo se debe hacer referencia a la versión del nombre de fusión.|
|Alias|Cadena opcional. Cualquier alias de la referencia.|
|Private|Booleano opcional. Especifica si la referencia debe copiarse en la carpeta de salida. Este atributo coincide con la propiedad **Copia local** de la referencia que está en el IDE de Visual Studio.|

### <a name="comreference"></a>COMReference

Representa una referencia a un componente COM (no administrado) del proyecto. Este elemento solo se aplica a los proyectos de .NET.

|Nombre de metadatos de elementos|Descripción|
|---------------|-----------------|
|NOMBRE|Cadena opcional. El nombre para mostrar del componente.|
|GUID|Cadena necesaria. GUID del componente, con el formato {12345678-1234-1234-1234-1234567891234}.|
|VersionMajor|Cadena necesaria. Parte principal del número de versión del componente. Por ejemplo, "5" si el número de versión completo es "5.46".|
|VersionMinor|Cadena necesaria. Parte secundaria del número de versión del componente. Por ejemplo, "46" si el número de versión completo es "5.46".|
|LCID|Cadena opcional. LocaleID del componente.|
|WrapperTool|Cadena opcional. Nombre de la herramienta contenedor que se usa en el componente, por ejemplo, "tlbimp".|
|Isolated|Booleano opcional. Especifica si se trata de un componente sin registro.|

### <a name="comfilereference"></a>COMFileReference

Representa una lista de las bibliotecas de tipos que se pasan al parámetro `TypeLibFiles` del destino [ResolveComReference](resolvecomreference-task.md). Este elemento solo se aplica a los proyectos de .NET.

|Nombre de metadatos de elementos|Descripción|
|---------------|-----------------|
|WrapperTool|Cadena opcional. Nombre de la herramienta contenedor que se usa en el componente, por ejemplo, "tlbimp".|

### <a name="nativereference"></a>NativeReference

Representa un archivo de manifiesto nativo o una referencia a este archivo.

|Nombre de metadatos de elementos|Descripción|
|---------------|-----------------|
|NOMBRE|Cadena necesaria. Nombre base del archivo de manifiesto.|
|HintPath|Cadena necesaria. Ruta de acceso relativa del archivo de manifiesto.|

### <a name="projectreference"></a>ProjectReference

Representa una referencia a otro proyecto. Los elementos `ProjectReference` se transforman en elementos de [referencia](#reference) mediante el destino `ResolveProjectReferences`, por lo que es posible que los metadatos válidos en una referencia sean válidos en `ProjectReference`, si el proceso de transformación no los sobrescribe.

|Nombre de metadatos de elementos|Descripción|
|---------------|-----------------|
|NOMBRE|Cadena opcional. Nombre para mostrar de la referencia.|
|GlobalPropertiesToRemove|Objeto `string[]` opcional. Nombres de las propiedades que se van a quitar al compilar el proyecto al que se hace referencia, por ejemplo, `RuntimeIdentifier;PackOnBuild`. El valor predeterminado es vacío.|
|Proyecto|Cadena opcional. GUID de la referencia, con el formato {12345678-1234-1234-1234-1234567891234}.|
|OutputItemType|Cadena opcional. Tipo de elemento al que se van a emitir salidas de destino. El valor predeterminado es en blanco. Si los metadatos de referencia se establecen en "true" (valor predeterminado), las salidas de destino se convierten en referencias del compilador.|
|ReferenceOutputAssembly|Booleano opcional. Si se establece en `false`, no incluye la salida del proyecto al que se hace referencia como una [Referencia](#reference) de este proyecto, pero garantiza que el otro proyecto realice compilaciones antes que este. Tiene como valor predeterminado `true`.|
|SetConfiguration|Cadena opcional. Establece la propiedad global `Configuration` del proyecto al que se hace referencia, por ejemplo, `Configuration=Release`.|
|SetPlatform|Cadena opcional. Establece la propiedad global `Platform` del proyecto al que se hace referencia, por ejemplo, `Platform=AnyCPU`.|
|SetTargetFramework|Cadena opcional. Establece la propiedad global `TargetFramework` del proyecto al que se hace referencia, por ejemplo, `TargetFramework=netstandard2.0`.|
|SkipGetTargetFrameworkProperties|Booleano opcional. Si es `true`, compila el proyecto al que se hace referencia sin negociar el valor `TargetFramework` más compatible. Tiene como valor predeterminado `false`.|
|Destinos|Objeto `string[]` opcional. Lista separada por puntos y coma de destinos de los proyectos a los que se hace referencia que deben compilarse. El valor predeterminado de `$(ProjectReferenceBuildTargets)` es en blanco, que indica los destinos predeterminados.|

### <a name="compile"></a>Compile

Representa los archivos de código fuente para el compilador.

| Nombre de metadatos de elementos | Descripción |
|-----------------------| - |
| DependentUpon | Cadena opcional. Especifica el archivo del que depende este archivo para compilarse correctamente. |
| AutoGen | Booleano opcional. Indica si el entorno de desarrollo integrado (IDE) de Visual Studio ha generado el archivo para el proyecto. |
| Link | Cadena opcional. Ruta de acceso notacional que se va a mostrar cuando el archivo se encuentre físicamente fuera de la influencia del archivo de proyecto. |
| Visible | Booleano opcional. Indica si se va a mostrar el archivo en el **Explorador de soluciones** de Visual Studio. |
| CopyToOutputDirectory | Cadena opcional. Determina si el archivo se va a copiar en el directorio de resultados. Los valores son:<br /><br /> 1.  Nunca<br />2.  Siempre<br />3.  PreserveNewest |

### <a name="embeddedresource"></a>EmbeddedResource

Representa los recursos que se van a incrustar en el ensamblado generado.

| Nombre de metadatos de elementos | Descripción |
|-----------------------| - |
| DependentUpon | Cadena opcional. Especifica el archivo del que depende este archivo para compilarse correctamente. |
| Generator | Cadena necesaria. Nombre de cualquier generador de archivos que se ejecute en este elemento. |
| LastGenOutput | Cadena necesaria. Nombre del archivo creado por cualquier generador de archivos que se ejecutó en este elemento. |
| CustomToolNamespace | Cadena necesaria. Espacio de nombres en el que cualquier generador de archivos que se ejecute en este elemento debe crear código. |
| Link | Cadena opcional. La ruta de acceso notacional se muestra si el archivo se encuentra físicamente fuera de la influencia del proyecto. |
| Visible | Booleano opcional. Indica si se va a mostrar el archivo en el **Explorador de soluciones** de Visual Studio. |
| CopyToOutputDirectory | Cadena opcional. Determina si el archivo se va a copiar en el directorio de resultados. Los valores son:<br /><br /> 1.  Nunca<br />2.  Siempre<br />3.  PreserveNewest |
| LogicalName | Cadena necesaria. Nombre lógico del recurso incrustado. |

### <a name="content"></a>Contenido

Representa archivos que no están compilados en el proyecto pero que podrían incrustarse o publicarse junto con él.

| Nombre de metadatos de elementos | Descripción |
|-----------------------| - |
| DependentUpon | Cadena opcional. Especifica el archivo del que depende este archivo para compilarse correctamente. |
| Generator | Cadena necesaria. Nombre de cualquier generador de archivos que se ejecute en este elemento. |
| LastGenOutput | Cadena necesaria. Nombre del archivo creado por cualquier generador de archivos que se ejecutó en este elemento. |
| CustomToolNamespace | Cadena necesaria. Espacio de nombres en el que cualquier generador de archivos que se ejecute en este elemento debe crear código. |
| Link | Cadena opcional. Ruta de acceso notacional que se mostrará si el archivo se encuentra físicamente fuera de la influencia del proyecto. |
| PublishState | Cadena necesaria. El estado de publicación del contenido:<br /><br /> - Predeterminado<br />- Incluido<br />- Excluido<br />- Archivo de datos<br />- Requisito previo |
| IsAssembly | Booleano opcional. Especifica si el archivo es un ensamblado. |
| Visible | Booleano opcional. Indica si se va a mostrar el archivo en el **Explorador de soluciones** de Visual Studio. |
| CopyToOutputDirectory | Cadena opcional. Determina si el archivo se va a copiar en el directorio de resultados. Los valores son:<br /><br /> 1.  Nunca<br />2.  Siempre<br />3.  PreserveNewest |

### <a name="none"></a>None

Representa archivos que no deberían tener ningún rol en el proceso de compilación.

| Nombre de metadatos de elementos | Descripción |
|-----------------------| - |
| DependentUpon | Cadena opcional. Especifica el archivo del que depende este archivo para compilarse correctamente. |
| Generator | Cadena necesaria. Nombre de cualquier generador de archivos que se ejecute en este elemento. |
| LastGenOutput | Cadena necesaria. Nombre del archivo creado por cualquier generador de archivos que se ejecutó en este elemento. |
| CustomToolNamespace | Cadena necesaria. Espacio de nombres en el que cualquier generador de archivos que se ejecute en este elemento debe crear código. |
| Link | Cadena opcional. Ruta de acceso notacional que se mostrará si el archivo se encuentra físicamente fuera de la influencia del proyecto. |
| Visible | Booleano opcional. Indica si se va a mostrar el archivo en el **Explorador de soluciones** de Visual Studio. |
| CopyToOutputDirectory | Cadena opcional. Determina si el archivo se va a copiar en el directorio de resultados. Los valores son:<br /><br /> 1.  Nunca<br />2.  Siempre<br />3.  PreserveNewest |

### <a name="assemblymetadata"></a>AssemblyMetadata

Representa los atributos de ensamblado que se van a generar como `[AssemblyMetadata(key, value)]`.

| Nombre de metadatos de elementos | Descripción |
|-----------------------| - |
| Incluir | Se convierte en el primer parámetro (la clave) del constructor de atributo `AssemblyMetadataAttribute`. |
| Valor | Cadena necesaria. Se convierte en el segundo parámetro (el valor) del constructor de atributo `AssemblyMetadataAttribute`. |

> [!NOTE]
> Este elemento se aplica a los proyectos que usan el SDK para .NET 5 (y .NET Core) y versiones posteriores.

### <a name="internalsvisibleto"></a>InternalsVisibleTo

Especifica los ensamblados que se van a emitir como atributos de ensamblado `[InternalsVisibleTo(..)]`.

| Nombre de metadatos de elementos | Descripción |
|-----------------------| - |
| Incluir | Nombre del ensamblado. |
| Clave | Cadena opcional. La clave pública del ensamblado. |

> [!NOTE]
> Este elemento se aplica a los proyectos que usan el SDK para .NET 5 (y .NET Core) y versiones posteriores.

### <a name="baseapplicationmanifest"></a>BaseApplicationManifest

Representa el manifiesto de aplicación base de la compilación y contiene información de seguridad de implementación de ClickOnce.

### <a name="codeanalysisimport"></a>CodeAnalysisImport

Representa el proyecto FxCop que se importará.

### <a name="import"></a>Importar

Representa los ensamblados cuyos espacios de nombres debe importar el compilador de Visual Basic.

## <a name="see-also"></a>Vea también

- [Propiedades comunes de proyectos de MSBuild](../msbuild/common-msbuild-project-properties.md)
- [Metadatos de elementos MSBuild comunes](common-msbuild-item-metadata.md)