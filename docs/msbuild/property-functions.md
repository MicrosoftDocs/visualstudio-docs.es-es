---
title: Funciones de propiedad | Microsoft Docs
ms.date: 02/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0551162a00437b01c7357dfdac16462aad8f2fc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597391"
---
# <a name="property-functions"></a>Funciones de propiedad

En .NET Framework versiones 4 y 4.5, se pueden usar funciones de propiedad para evaluar los scripts de MSBuild. Las funciones de propiedad se pueden usar siempre que aparezcan propiedades. A diferencia de las tareas, las funciones de propiedad se pueden usar fuera de los destinos, y se evalúan antes de que se ejecute ningún destino.

 Se puede leer la hora del sistema, comparar cadenas, buscar coincidencias de expresiones regulares y realizar otras acciones en el script de compilación sin usar tareas de MSBuild. MSBuild intentará convertir la cadena en números y los números en cadena, y realizar otras conversiones que sean necesarias.
 
Los valores de cadena devueltos por las funciones de propiedad tienen [caracteres especiales](msbuild-special-characters.md) con secuencia de escape. Si quiere que el valor se considere como si se hubiese implementado directamente en el archivo del proyecto, use `$([MSBuild]::Unescape())` para quitar las secuencias de escape de los caracteres especiales.

## <a name="property-function-syntax"></a>Sintaxis de las funciones de propiedad

Hay tres tipos de funciones de propiedad, cada una con una sintaxis diferente:

- Funciones de propiedad de cadena (instancia)
- Funciones de propiedad estáticas
- Funciones de propiedad de MSBuild

### <a name="string-property-functions"></a>Funciones de propiedad de cadena

Todos los valores de las funciones compiladas son solo valores de cadena. Puede usar los métodos de cadena (instancia) para operar en cualquier valor de propiedad. Por ejemplo, puede usar este código para extraer el nombre de unidad (los primeros tres caracteres) de una propiedad de compilación que representa una ruta completa:

```fundamental
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>Funciones de propiedad estáticas

En el script de compilación, puede acceder a las propiedades y método estáticos de muchas clases del sistema. Para obtener el valor de una propiedad estática, utilice la sintaxis siguiente, donde \<Class> es el nombre de la clase del sistema y \<Property> es el nombre de la propiedad.

```fundamental
$([Class]::Property)
```

Por ejemplo, puede usar el código siguiente para establecer una propiedad de compilación en la fecha y hora actuales.

```xml
<Today>$([System.DateTime]::Now)</Today>
```

Para llamar a un método estático, utilice la sintaxis siguiente, donde \<Class> es el nombre de la clase del sistema, \<Method> es el nombre del método y (\<Parameters) es la lista de parámetros del método:

```fundamental
$([Class]::Method(Parameters))
```

Por ejemplo, para establecer una propiedad de compilación en un nuevo GUID, puede usar este script:

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

En las funciones de propiedad estáticas, puede usar cualquier método o propiedad estáticos de estas clases del sistema:

- System.Byte
- System.Char
- System.Convert
- System.DateTime
- System.Decimal
- System.Double
- System.Enum
- System.Guid
- System.Int16
- System.Int32
- System.Int64
- System.IO.Path
- System.Math
- System.Runtime.InteropServices.OSPlatform
- System.Runtime.InteropServices.RuntimeInformation
- System.UInt16
- System.UInt32
- System.UInt64
- System.SByte
- System.Single
- System.String
- System.StringComparer
- System.TimeSpan
- System.Text.RegularExpressions.Regex
- System.UriBuilder
- System.Version
- Microsoft.Build.Utilities.ToolLocationHelper

Además, puede usar los siguientes métodos y propiedades estáticos:

- System.Environment::CommandLine
- System.Environment::ExpandEnvironmentVariables
- System.Environment::GetEnvironmentVariable
- System.Environment::GetEnvironmentVariables
- System.Environment::GetFolderPath
- System.Environment::GetLogicalDrives
- System.IO.Directory::GetDirectories
- System.IO.Directory::GetFiles
- System.IO.Directory::GetLastAccessTime
- System.IO.Directory::GetLastWriteTime
- System.IO.Directory::GetParent
- System.IO.File::Exists
- System.IO.File::GetCreationTime
- System.IO.File::GetAttributes
- System.IO.File::GetLastAccessTime
- System.IO.File::GetLastWriteTime
- System.IO.File::ReadAllText

### <a name="calling-instance-methods-on-static-properties"></a>Llamada a métodos de instancia en propiedades estáticas

Si accede a una propiedad estática que devuelve una instancia de objeto, puede invocar los métodos de instancia de ese objeto. Para llamar a un método de instancia, utilice la sintaxis siguiente, donde \<Class> es el nombre de la clase del sistema, \<Property> es el nombre de la propiedad, \<Method> es el nombre del método y (\<Parameters>) es la lista de parámetros del método:

```fundamental
$([Class]::Property.Method(Parameters))
```

El nombre de la clase debe ser completo en el espacio de nombres.

Por ejemplo, puede usar el código siguiente para establecer una propiedad de compilación en la fecha de hoy.

```xml
<Today>$([System.DateTime]::Now.ToString('yyyy.MM.dd'))</Today>
```

### <a name="msbuild-property-functions"></a>Funciones de propiedad de MSBuild

Puede acceder a varios métodos estáticos de su compilación para proporcionar compatibilidad con operadores aritméticos, lógicos bit a bit y caracteres de escape. Para acceder a estos métodos, utilice la sintaxis siguiente, donde \<Method> es el nombre del método y (\<Parameters>) es la lista de parámetros del método.

```fundamental
$([MSBuild]::Method(Parameters))
```

Por ejemplo, para sumar dos propiedades que tienen valores numéricos, use el código siguiente.

```fundamental
$([MSBuild]::Add($(NumberOne), $(NumberTwo)))
```

Esta es una lista de las funciones de propiedad de MSBuild:

|Signatura de función|Descripción|
|------------------------|-----------------|
|double Add(double a, double b)|Suma dos valores double.|
|long Add(long a, long b)|Suma dos valores long.|
|double Subtract(double a, double b)|Resta dos valores double.|
|long Subtract(long a, long b)|Resta dos valores long.|
|double Multiply(double a, double b)|Multiplica dos valores double.|
|long Multiply(long a, long b)|Multiplica dos valores long.|
|double Divide(double a, double b)|Divide dos valores double.|
|long Divide(long a, long b)|Divide dos valores long.|
|double Modulo(double a, double b)|Realiza la operación de módulo en dos valores double.|
|long Modulo(long a, long b)|Realiza la operación de módulo en dos valores long.|
|string Escape(string unescaped)|Aplica un escape a la cadena según las reglas de escape de MSBuild.|
|string Unescape(string escaped)|Elimina el escape de la cadena según las reglas de escape de MSBuild.|
|int BitwiseOr(int first, int second)|Realiza una operación `OR` bit a bit en el primero y el segundo (primero &#124; segundo).|
|int BitwiseAnd(int first, int second)|Realiza una operación `AND` bit a bit en el primero y el segundo (primero & segundo).|
|int BitwiseXor(int first, int second)|Realiza una operación `XOR` bit a bit en el primero y el segundo (primero ^ segundo).|
|int BitwiseNot(int first)|Realiza una operación `NOT` bit a bit (~first).|
|bool IsOsPlatform(string platformString)|Especifica si la plataforma del sistema operativo actual es `platformString`. `platformString` debe ser un miembro de <xref:System.Runtime.InteropServices.OSPlatform>.|
|bool IsOSUnixLike()|True si el sistema operativo actual es un sistema Unix.|
|string NormalizePath(params string[] path)|Obtiene la ruta de acceso completa con formato canónico de la ruta proporcionada y garantiza que contiene los caracteres separadores de directorio correctos para el sistema operativo actual.|
|string NormalizeDirectory(params string[] path)|Obtiene la ruta de acceso completa con formato canónico del directorio proporcionado y garantiza que contiene los caracteres separadores de directorio correctos para el sistema operativo actual mientras garantiza que tiene una barra diagonal final.|
|string EnsureTrailingSlash(string path)|Si la ruta de acceso proporcionada no tiene una barra diagonal final, entonces agrega una. Si la ruta es una cadena vacía, no la modifica.|
|string GetPathOfFileAbove(string file, string startingDirectory)|Busca un archivo basándose en la ubicación del archivo de compilación actual, o basándose en `startingDirectory`, si se ha especificado.|
|GetDirectoryNameOfFileAbove(string startingDirectory, string fileName)|Busca un archivo en el directorio especificado o en una ubicación de la estructura de directorios por encima de ese directorio.|
|string MakeRelative(string basePath, string path)|Hace que `path` sea relativo a `basePath`. `basePath` debe ser un directorio absoluto. Si `path` no puede ser relativo, se devuelve textualmente. Similar a `Uri.MakeRelativeUri`.|
|string ValueOrDefault(string conditionValue, string defaultValue)|Devuelve la cadena en el parámetro "defaultValue" solo si el parámetro "conditionValue" está vacío. De lo contrario, devuelve el valor conditionValue.|

## <a name="nested-property-functions"></a>Funciones de propiedad anidadas

Puede combinar funciones de propiedad para formar funciones más complejas, como muestra el siguiente ejemplo.

```fundamental
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

Este ejemplo devuelve el valor del bit <xref:System.IO.FileAttributes>`Archive` (32 o 0) del archivo indicado por la ruta de acceso `tempFile`. Tenga en cuenta que los valores de datos enumerados no pueden aparecer por nombre dentro de las funciones de propiedad. En su lugar, se debe usar el valor numérico (32).

En las funciones de propiedad anidadas también pueden aparecer metadatos. Para obtener más información, consulte [Procesamiento por lotes](../msbuild/msbuild-batching.md).

## <a name="msbuild-doestaskhostexist"></a>DoesTaskHostExist de MSBuild

La función de propiedad `DoesTaskHostExist` de MSBuild devuelve si actualmente hay instalado un host de tareas para el tiempo de ejecución y los valores de arquitectura especificados.

Esta función de propiedad tiene la sintaxis siguiente:

```fundamental
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>MSBuild EnsureTrailingSlash

La función de propiedad `EnsureTrailingSlash` de MSBuild agrega una barra diagonal final, si todavía no existe.

Esta función de propiedad tiene la sintaxis siguiente:

```fundamental
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>GetDirectoryNameOfFileAbove de MSBuild

La función de propiedad `GetDirectoryNameOfFileAbove` de MSBuild busca un archivo en los directorios situados por encima del directorio actual en la ruta de acceso.

 Esta función de propiedad tiene la sintaxis siguiente:

```fundamental
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 El código siguiente es un ejemplo de esta sintaxis.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>MSBuild GetPathOfFileAbove

La función de propiedad `GetPathOfFileAbove` de MSBuild devuelve la ruta de acceso del archivo inmediatamente anterior a este. Es funcionalmente equivalente a llamar a

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

Esta función de propiedad tiene la sintaxis siguiente:

```fundamental
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>GetRegistryValue de MSBuild

La función de propiedad `GetRegistryValue` de MSBuild devuelve el valor de una clave de registro. Esta función toma dos argumentos, el nombre de clave y el nombre de valor, y devuelve el valor del Registro. Si no especifica un nombre de valor, se devuelve el valor predeterminado.

En los ejemplos siguientes se muestra cómo usar esta función:

```fundamental
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>GetRegistryValueFromView de MSBuild

La función de propiedad `GetRegistryValueFromView` de MSBuild obtiene datos del Registro del sistema dada la clave del Registro, el valor y una o varias vistas del Registro ordenadas. La clave y el valor se buscan en cada vista del Registro por orden hasta que se encuentran.

La sintaxis de esta función de propiedad es:

```fundamental
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

El sistema operativo Windows de 64 bits mantiene una clave del Registro **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node** que presenta una vista del Registro **HKEY_LOCAL_MACHINE\SOFTWARE** para aplicaciones de 32 bits.

De forma predeterminada, una aplicación de 32 bits que se ejecuta en WOW64 accede a la vista del Registro de 32 bits, y una aplicación de 64 bits accede a la vista del Registro de 64 bits.

Están disponibles las siguientes vistas del Registro:

|Vista del Registro|Definición|
|-------------------|----------------|
|RegistryView.Registry32|La vista del Registro para aplicaciones de 32 bits.|
|RegistryView.Registry64|La vista del Registro para aplicaciones de 64 bits.|
|RegistryView.Default|La vista del Registro que coincide con el proceso donde se está ejecutando la aplicación.|

A continuación se muestra un ejemplo.

 ```fundamental
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

obtiene los datos de **SLRuntimeInstallPath** de la clave **ReferenceAssemblies**, y busca primero en la vista del Registro de 64 bits y, después, en la vista del Registro de 32 bits.

## <a name="msbuild-makerelative"></a>MakeRelative de MSBuild

La función de propiedad `MakeRelative` de MSBuild devuelve la ruta de acceso relativa de la segunda ruta de acceso, relativa a la primera ruta de acceso. Cada ruta de acceso puede ser un archivo o una carpeta.

Esta función de propiedad tiene la sintaxis siguiente:

```fundamental
$([MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2)))
```

El código siguiente es un ejemplo de esta sintaxis.

```xml
<PropertyGroup>
    <Path1>c:\users\</Path1>
    <Path2>c:\users\username\</Path2>
</PropertyGroup>

<Target Name = "Go">
    <Message Text ="$([MSBuild]::MakeRelative($(Path1), $(Path2)))" />
    <Message Text ="$([MSBuild]::MakeRelative($(Path2), $(Path1)))" />
</Target>

<!--
Output:
   username\
   ..\
-->
```

## <a name="msbuild-valueordefault"></a>ValueOrDefault de MSBuild

La función de propiedad `ValueOrDefault` de MSBuild devuelve el primer argumento, a menos que sea nulo o vacío. Si el primer argumento es nulo o vacío, la función devuelve el segundo argumento.

En el ejemplo siguiente se muestra cómo usar esta función.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <Value1>$([MSBuild]::ValueOrDefault('$(UndefinedValue)', 'a'))</Value1>
        <Value2>$([MSBuild]::ValueOrDefault('b', '$(Value1)'))</Value2>
    </PropertyGroup>

    <Target Name="MyTarget">
        <Message Text="Value1 = $(Value1)" />
        <Message Text="Value2 = $(Value2)" />
    </Target>
</Project>

<!--
Output:
  Value1 = a
  Value2 = b
-->
```

## <a name="see-also"></a>Vea también

- [Propiedades de MSBuild](../msbuild/msbuild-properties.md)

- [Información general sobre MSBuild](../msbuild/msbuild.md)
