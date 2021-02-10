---
title: Funciones de propiedad | Microsoft Docs
description: Obtenga información sobre las funciones de propiedad, que son llamadas a métodos de .NET Framework que aparecen en las definiciones de propiedad de MSBuild.
ms.custom: SEO-VS-2020
ms.date: 02/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5b4dce707d51d7a2840aeef78f4d70392c884275
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932024"
---
# <a name="property-functions"></a>Funciones de propiedad

Las funciones de propiedad son llamadas a métodos de .NET Framework que aparecen en las definiciones de propiedad de MSBuild. A diferencia de las tareas, las funciones de propiedad se pueden usar fuera de los destinos, y se evalúan antes de que se ejecute ningún destino.

Se puede leer la hora del sistema, comparar cadenas, buscar coincidencias de expresiones regulares y realizar otras acciones en el script de compilación sin usar tareas de MSBuild. MSBuild intentará convertir la cadena en números y los números en cadena, y realizar otras conversiones que sean necesarias.

Los valores de cadena devueltos por las funciones de propiedad tienen [caracteres especiales](msbuild-special-characters.md) con secuencia de escape. Si quiere que el valor se considere como si se hubiese implementado directamente en el archivo del proyecto, use `$([MSBuild]::Unescape())` para quitar las secuencias de escape de los caracteres especiales.

Las funciones de propiedad están disponibles con .NET Framework 4 y versiones posteriores.

## <a name="property-function-syntax"></a>Sintaxis de las funciones de propiedad

Hay tres tipos de funciones de propiedad, cada una con una sintaxis diferente:

- Funciones de propiedad de cadena (instancia)
- Funciones de propiedad estáticas
- Funciones de propiedad de MSBuild

### <a name="string-property-functions"></a>Funciones de propiedad de cadena

Todos los valores de las funciones compiladas son solo valores de cadena. Puede usar los métodos de cadena (instancia) para operar en cualquier valor de propiedad. Por ejemplo, puede usar este código para extraer el nombre de unidad (los primeros tres caracteres) de una propiedad de compilación que representa una ruta completa:

```
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>Funciones de propiedad estáticas

En el script de compilación, puede acceder a las propiedades y método estáticos de muchas clases del sistema. Para obtener el valor de una propiedad estática, utilice la sintaxis siguiente, donde \<Class> es el nombre de la clase del sistema y \<Property> es el nombre de la propiedad.

```
$([Class]::Property)
```

Por ejemplo, puede usar el código siguiente para establecer una propiedad de compilación en la fecha y hora actuales.

```xml
<Today>$([System.DateTime]::Now)</Today>
```

Para llamar a un método estático, utilice la sintaxis siguiente, donde \<Class> es el nombre de la clase del sistema, \<Method> es el nombre del método y (\<Parameters>) es la lista de parámetros del método:

```
$([Class]::Method(Parameters))
```

Por ejemplo, para establecer una propiedad de compilación en un nuevo GUID, puede usar este script:

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

En las funciones de propiedad estáticas, puede usar cualquier método o propiedad estáticos de estas clases del sistema:

- <xref:System.Byte?displayProperty=nameWithType>
- <xref:System.Char?displayProperty=nameWithType>
- <xref:System.Convert?displayProperty=nameWithType>
- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Enum?displayProperty=nameWithType>
- <xref:System.Guid?displayProperty=nameWithType>
- <xref:System.Int16?displayProperty=nameWithType>
- <xref:System.Int32?displayProperty=nameWithType>
- <xref:System.Int64?displayProperty=nameWithType>
- <xref:System.IO.Path?displayProperty=nameWithType>
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.OSPlatform?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation?displayProperty=nameWithType>
- <xref:System.UInt16?displayProperty=nameWithType>
- <xref:System.UInt32?displayProperty=nameWithType>
- <xref:System.UInt64?displayProperty=nameWithType>
- <xref:System.SByte?displayProperty=nameWithType>
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.StringComparer?displayProperty=nameWithType>
- <xref:System.TimeSpan?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- <xref:System.UriBuilder?displayProperty=nameWithType>
- <xref:System.Version?displayProperty=nameWithType>
- <xref:Microsoft.Build.Utilities.ToolLocationHelper?displayProperty=nameWithType>

Además, puede usar los siguientes métodos y propiedades estáticos:

- [System.Environment::CommandLine](xref:System.Environment.CommandLine*)
- [System.Environment::ExpandEnvironmentVariables](xref:System.Environment.ExpandEnvironmentVariables*)
- [System.Environment::GetEnvironmentVariable](xref:System.Environment.GetEnvironmentVariable*)
- [System.Environment::GetEnvironmentVariables](xref:System.Environment.GetEnvironmentVariables*)
- [System.Environment::GetFolderPath](xref:System.Environment.GetFolderPath*)
- [System.Environment::GetLogicalDrives](xref:System.Environment.GetLogicalDrives*)
- [System.IO.Directory::GetDirectories](xref:System.IO.Directory.GetDirectories*)
- [System.IO.Directory::GetFiles](xref:System.IO.Directory.GetFiles*)
- [System.IO.Directory::GetLastAccessTime](xref:System.IO.Directory.GetLastAccessTime*)
- [System.IO.Directory::GetLastWriteTime](xref:System.IO.Directory.GetLastWriteTime*)
- [System.IO.Directory::GetParent](xref:System.IO.Directory.GetParent*)
- [System.IO.File::Exists](xref:System.IO.File.Exists*)
- [System.IO.File::GetCreationTime](xref:System.IO.File.GetCreationTime*)
- [System.IO.File::GetAttributes](xref:System.IO.File.GetAttributes*)
- [System.IO.File::GetLastAccessTime](xref:System.IO.File.GetLastAccessTime*)
- [System.IO.File::GetLastWriteTime](xref:System.IO.File.GetLastWriteTime*)
- [System.IO.File::ReadAllText](xref:System.IO.File.ReadAllText*)

### <a name="calling-instance-methods-on-static-properties"></a>Llamada a métodos de instancia en propiedades estáticas

Si accede a una propiedad estática que devuelve una instancia de objeto, puede invocar los métodos de instancia de ese objeto. Para llamar a un método de instancia, utilice la sintaxis siguiente, donde \<Class> es el nombre de la clase del sistema, \<Property> es el nombre de la propiedad, \<Method> es el nombre del método y (\<Parameters>) es la lista de parámetros del método:

```
$([Class]::Property.Method(Parameters))
```

El nombre de la clase debe ser completo en el espacio de nombres.

Por ejemplo, puede usar el código siguiente para establecer una propiedad de compilación en la fecha de hoy.

```xml
<Today>$([System.DateTime]::Now.ToString('yyyy.MM.dd'))</Today>
```

### <a name="msbuild-property-functions"></a>Funciones de propiedad de MSBuild

Puede acceder a varios métodos estáticos de su compilación para proporcionar compatibilidad con operadores aritméticos, lógicos bit a bit y caracteres de escape. Para acceder a estos métodos, utilice la sintaxis siguiente, donde \<Method> es el nombre del método y (\<Parameters>) es la lista de parámetros del método.

```
$([MSBuild]::Method(Parameters))
```

Por ejemplo, para sumar dos propiedades que tienen valores numéricos, use el código siguiente.

```
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
|string GetPathOfFileAbove(string file, string startingDirectory)|Busca y devuelve la ruta de acceso completa a un archivo en la estructura de directorios que está encima de la ubicación del archivo de compilación actual, o en función de `startingDirectory`, si se especifica.|
|GetDirectoryNameOfFileAbove(string startingDirectory, string fileName)|Busca y devuelve el directorio de un archivo en el directorio especificado o en una ubicación de la estructura de directorios por encima de ese directorio.|
|string MakeRelative(string basePath, string path)|Hace que `path` sea relativo a `basePath`. `basePath` debe ser un directorio absoluto. Si `path` no puede ser relativo, se devuelve textualmente. Similar a `Uri.MakeRelativeUri`.|
|string ValueOrDefault(string conditionValue, string defaultValue)|Devuelve la cadena en el parámetro "defaultValue" solo si el parámetro "conditionValue" está vacío. De lo contrario, devuelve el valor conditionValue.|

## <a name="nested-property-functions"></a>Funciones de propiedad anidadas

Puede combinar funciones de propiedad para formar funciones más complejas, como muestra el siguiente ejemplo.

```
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

Este ejemplo devuelve el valor del bit <xref:System.IO.FileAttributes>`Archive` (32 o 0) del archivo indicado por la ruta de acceso `tempFile`. Tenga en cuenta que los valores de datos enumerados no pueden aparecer por nombre dentro de las funciones de propiedad. En su lugar, se debe usar el valor numérico (32).

En las funciones de propiedad anidadas también pueden aparecer metadatos. Para obtener más información, consulte [Procesamiento por lotes](../msbuild/msbuild-batching.md).

## <a name="msbuild-doestaskhostexist"></a>DoesTaskHostExist de MSBuild

La función de propiedad `DoesTaskHostExist` de MSBuild devuelve si actualmente hay instalado un host de tareas para el tiempo de ejecución y los valores de arquitectura especificados.

Esta función de propiedad tiene la sintaxis siguiente:

```
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>MSBuild EnsureTrailingSlash

La función de propiedad `EnsureTrailingSlash` de MSBuild agrega una barra diagonal final, si todavía no existe.

Esta función de propiedad tiene la sintaxis siguiente:

```
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>GetDirectoryNameOfFileAbove de MSBuild

La función de propiedad `GetDirectoryNameOfFileAbove` de MSBuild busca un archivo en los directorios situados por encima del directorio actual en la ruta de acceso.

 Esta función de propiedad tiene la sintaxis siguiente:

```
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 El código siguiente es un ejemplo de esta sintaxis.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>MSBuild GetPathOfFileAbove

La función de propiedad `GetPathOfFileAbove` de MSBuild devuelve la ruta de acceso del archivo especificado, si se encuentra en la estructura de directorios por encima del directorio actual. Es funcionalmente equivalente a llamar a

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

Esta función de propiedad tiene la sintaxis siguiente:

```
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>GetRegistryValue de MSBuild

La función de propiedad `GetRegistryValue` de MSBuild devuelve el valor de una clave de registro. Esta función toma dos argumentos, el nombre de clave y el nombre de valor, y devuelve el valor del Registro. Si no especifica un nombre de valor, se devuelve el valor predeterminado.

En los ejemplos siguientes se muestra cómo usar esta función:

```
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>GetRegistryValueFromView de MSBuild

La función de propiedad `GetRegistryValueFromView` de MSBuild obtiene datos del Registro del sistema dada la clave del Registro, el valor y una o varias vistas del Registro ordenadas. La clave y el valor se buscan en cada vista del Registro por orden hasta que se encuentran.

La sintaxis de esta función de propiedad es:

```
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

 ```
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

obtiene los datos de **SLRuntimeInstallPath** de la clave **ReferenceAssemblies**, y busca primero en la vista del Registro de 64 bits y, después, en la vista del Registro de 32 bits.

## <a name="msbuild-makerelative"></a>MakeRelative de MSBuild

La función de propiedad `MakeRelative` de MSBuild devuelve la ruta de acceso relativa de la segunda ruta de acceso, relativa a la primera ruta de acceso. Cada ruta de acceso puede ser un archivo o una carpeta.

Esta función de propiedad tiene la sintaxis siguiente:

```
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

## <a name="msbuild-targetframework-and-targetplatform-functions"></a>Funciones TargetFramework y TargetPlatform de MSBuild

MSBuild define varias funciones para controlar las [propiedades TargetFramework y TargetPlatform](msbuild-target-framework-and-target-platform.md).

|Signatura de función|Descripción|
|------------------------|-----------------|
|GetTargetFrameworkIdentifier(string targetFramework)|Analice TargetFrameworkIdentifier desde TargetFramework.|
|GetTargetFrameworkVersion(string targetFramework)|Analice TargetFrameworkVersion desde TargetFramework.|
|GetTargetPlatformIdentifier(string targetFramework)|Analice TargetPlatformIdentifier desde TargetFramework.|
|GetTargetPlatformVersion(string targetFramework)|Analice TargetPlatformVersion desde TargetFramework.|
|IsTargetFrameworkCompatible(string targetFrameworkTarget, string targetFrameworkCandidate)|Devuelve "true" si la plataforma de destino candidata es compatible con esta plataforma de destino y "false" en caso contrario.|

En el ejemplo siguiente se muestra cómo se usan estas funciones. 

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <Value1>$([MSBuild]::GetTargetFrameworkIdentifier('net5.0-windows7.0'))</Value1>
        <Value2>$([MSBuild]::GetTargetFrameworkVersion('net5.0-windows7.0'))</Value2>
        <Value3>$([MSBuild]::GetTargetPlatformIdentifier('net5.0-windows7.0'))</Value3>
        <Value4>$([MSBuild]::GetTargetPlatformVersion('net5.0-windows7.0'))</Value4>
        <Value5>$([MSBuild]::IsTargetFrameworkCompatible('net5.0-windows', 'net5.0'))</Value5>
    </PropertyGroup>

    <Target Name="MyTarget">
        <Message Text="Value1 = $(Value1)" />
        <Message Text="Value2 = $(Value2)" />
        <Message Text="Value3 = $(Value3)" />
        <Message Text="Value4 = $(Value4)" />
        <Message Text="Value5 = $(Value5)" />
    </Target>
</Project>
```

```output
Value1 = .NETCoreApp
Value2 = 5.0
Value3 = windows
Value4 = 7.0
Value5 = True
```

## <a name="msbuild-condition-functions"></a>Funciones de condiciones de MSBuild

Las funciones `Exists` y `HasTrailingSlash` no son funciones de propiedad. Están disponibles para su uso con el atributo `Condition`. Consulte [Condiciones de MSBuild](msbuild-conditions.md).

## <a name="see-also"></a>Vea también

- [Propiedades de MSBuild](../msbuild/msbuild-properties.md)

- [Información general sobre MSBuild](../msbuild/msbuild.md)
