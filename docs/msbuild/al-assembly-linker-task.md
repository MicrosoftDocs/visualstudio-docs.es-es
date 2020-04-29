---
title: AL (Assembly Linker, Tarea) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AL
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- AL task [MSBuild]
- MSBuild, AL task
ms.assetid: 2ddefbf2-5662-4d55-99a6-ac383bf44560
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c7964c6654d1f6996d1acc44542e3a7bf093a52
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167467"
---
# <a name="al-assembly-linker-task"></a>AL (Assembly Linker, Tarea)

La tarea AL contiene *AL.exe*, una herramienta que se distribuye con el kit de desarrollo de software (SDK) de Windows. La herramienta Assembly Linker se utiliza para crear un ensamblado con un manifiesto a partir de uno o varios archivos que pueden ser módulos o archivos de recursos. Los compiladores y los entornos de desarrollo pueden proporcionar estas capacidades, por lo que a menudo no hace falta utilizar esta tarea directamente. Assembly Linker resulta de más utilidad para los programadores que necesitan crear un único ensamblado a partir de varios archivos de componentes, como los que se pueden producir en desarrollos de lenguajes combinados. Esta tarea no combina los módulos en un único archivo de ensamblado; los módulos individuales deben distribuirse y estar disponibles para que el ensamblado resultante se cargue correctamente. Para obtener más información sobre *AL.exe*, vea [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).

## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de la tarea `AL` .

| Parámetro | Descripción |
|---------------------| - |
| `AlgorithmID` | Parámetro `String` opcional.<br /><br /> Especifica un algoritmo que genera un valor hash para todos los archivos en un ensamblado de múltiples archivos, exceptuando el archivo que contiene el manifiesto del ensamblado. Para obtener más información, consulte la documentación sobre la opción `/algid` en [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `BaseAddress` | Parámetro `String` opcional.<br /><br /> Especifica la dirección donde se cargará un archivo DLL en el equipo del usuario en tiempo de ejecución. Las aplicaciones se cargan con mayor rapidez si se especifica la dirección base de los archivos DLL, en lugar de dejar que el sistema operativo cambie la ubicación de los mismos en el espacio de procesos. Este parámetro corresponde a la opción /base[address](/dotnet/framework/tools/al-exe-assembly-linker). |
| `CompanyName` | Parámetro `String` opcional.<br /><br /> Especifica una cadena para el campo `Company` del ensamblado. Para obtener más información, consulte la documentación sobre la opción `/comp[any]` en [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Configuration` | Parámetro `String` opcional.<br /><br /> Especifica una cadena para el campo `Configuration` del ensamblado. Para obtener más información, consulte la documentación sobre la opción `/config[uration]` en [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Copyright` | Parámetro `String` opcional.<br /><br /> Especifica una cadena para el campo `Copyright` del ensamblado. Para obtener más información, consulte la documentación sobre la opción `/copy[right]` en [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Culture` | Parámetro `String` opcional.<br /><br /> Especifica la cadena de referencia cultural que se va a asociar al ensamblado. Para obtener más información, consulte la documentación sobre la opción `/c[ulture]` en [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `DelaySign` | Parámetro `Boolean` opcional.<br /><br /> `true` para colocar solo la clave pública en el ensamblado; `false` para firmar completamente el ensamblado. Para obtener más información, consulte la documentación sobre la opción `/delay[sign]` en [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Description` | Parámetro `String` opcional.<br /><br /> Especifica una cadena para el campo `Description` del ensamblado. Para obtener más información, consulte la documentación sobre la opción `/descr[iption]` en [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EmbedResources` | Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Inserta los recursos especificados en la imagen que contiene el manifiesto del ensamblado. Esta tarea copia el contenido del archivo de recursos en la imagen. Los elementos pasados a este parámetro pueden tener metadatos opcionales adjuntos a los mismos denominados `LogicalName` y `Access`. Los metadatos `LogicalName` se utilizan para especificar el identificador interno del recurso.  Los metadatos `Access` se pueden establecer en `private` para que el recurso no sea visible para otros ensamblados. Para obtener más información, consulte la documentación sobre la opción `/embed[resource]` en [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EvidenceFile` | Parámetro `String` opcional.<br /><br /> Inserta el archivo especificado en el ensamblado con el nombre de recurso `Security.Evidence`.<br /><br /> No se puede usar `Security.Evidence` para los recursos habituales. Este parámetro corresponde a la opción `/e[vidence]` de [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ExitCode` | Parámetro de solo lectura de salida `Int32` opcional.<br /><br /> Especifica el código de salida proporcionado por el comando ejecutado. |
| `FileVersion` | Parámetro `String` opcional.<br /><br /> Especifica una cadena para el campo `File Version` del ensamblado. Para obtener más información, consulte la documentación sobre la opción `/fileversion` en [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Flags` | Parámetro `String` opcional.<br /><br /> Especifica un valor para el campo `Flags` del ensamblado. Para obtener más información, consulte la documentación sobre la opción `/flags` en [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `GenerateFullPaths` | Parámetro `Boolean` opcional.<br /><br /> Hace que la tarea use la ruta de acceso absoluta de los archivos que se enumeran en un mensaje de error. Este parámetro corresponde a la opción `/fullpaths` de [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyContainer` | Parámetro `String` opcional.<br /><br /> Especifica un contenedor que contiene un par de claves. De este modo, el ensamblado se firmará (recibirá un nombre seguro) mediante la inserción de una clave pública en el manifiesto del ensamblado. La tarea firmará después el ensamblado final con la clave privada. Para obtener más información, consulte la documentación sobre la opción `/keyn[ame]` en [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyFile` | Parámetro `String` opcional.<br /><br /> Especifica un archivo que contiene un par de claves o simplemente una clave pública para firmar un ensamblado. El compilador inserta la clave pública en el manifiesto del ensamblado y firma después el ensamblado final con la clave privada. Para obtener más información, consulte la documentación sobre la opción `/keyf[ile]` en [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `LinkResources` | Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Vincula los archivos de recursos especificados a un ensamblado. El recurso pasa a formar parte del ensamblado, pero el archivo no se copia. Los elementos pasados a este parámetro pueden tener metadatos opcionales adjuntos a los mismos denominados `LogicalName`, `Target` y `Access`. Los metadatos `LogicalName` se utilizan para especificar el identificador interno del recurso. Los metadatos `Target` pueden especificar el nombre de archivo y la ruta de acceso donde la tarea copia el archivo, tras lo cual compila este nuevo archivo en el ensamblado. Los metadatos `Access` se pueden establecer en `private` para que el recurso no sea visible para otros ensamblados. Para obtener más información, consulte la documentación sobre la opción `/link[resource]` en [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `MainEntryPoint` | Parámetro `String` opcional.<br /><br /> Especifica el nombre completo (*class.method*) del método que se utilizará como punto de entrada al convertir un módulo en un archivo ejecutable. Este parámetro corresponde a la opción `/main` de [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `OutputAssembly` | Parámetro de salida obligatorio de tipo <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Especifica el nombre del archivo generado por esta tarea. Este parámetro corresponde a la opción `/out` de [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Platform` | Parámetro `String` opcional.<br /><br /> Limita en qué plataforma se puede ejecutar este código; debe ser `x86`, `Itanium`, `x64` o `anycpu`. De manera predeterminada, es `anycpu`. Este parámetro corresponde a la opción `/platform` de [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductName` | Parámetro `String` opcional.<br /><br /> Especifica una cadena para el campo `Product` del ensamblado. Para obtener más información, consulte la documentación sobre la opción `/prod[uct]` en [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductVersion` | Parámetro `String` opcional.<br /><br /> Especifica una cadena para el campo `ProductVersion` del ensamblado. Para obtener más información, consulte la documentación sobre la opción `/productv[ersion]` en [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ResponseFiles` | Parámetro `String[]` opcional.<br /><br /> Especifica los archivos de respuesta que contienen las opciones adicionales que deben pasarse a Assembly Linker. |
| `SdkToolsPath` | Parámetro `String` opcional.<br /><br /> Especifica la ruta de acceso a las herramientas del SDK, tales como resgen.exe. |
| `SourceModules` | Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Uno o varios módulos que se compilarán en un ensamblado. Los módulos aparecerán en una lista en el manifiesto del ensamblado resultante, y tendrán que distribuirse y estar disponibles para poder cargar el ensamblado. Los elementos que se pasan a este parámetro pueden tener metadatos adicionales denominados `Target`, que especifican la ruta y el nombre de archivo en el que la tarea copia el archivo, tras lo cual compilará este nuevo archivo en el ensamblado. Para obtener más información, consulte la documentación de [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). Este parámetro corresponde a la lista de módulos pasados a *Al.exe* sin un modificador concreto. |
| `TargetType` | Parámetro `String` opcional.<br /><br /> Especifica el formato del archivo de salida: `library` (biblioteca de códigos), `exe` (aplicación de consola) o `win` (aplicación basada en Windows). De manera predeterminada, es `library`. Este parámetro corresponde a la opción `/t[arget]` de [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `TemplateFile` | Parámetro `String` opcional.<br /><br /> Especifica el ensamblado del que se heredarán todos los metadatos del ensamblado, salvo el campo correspondiente a la referencia cultural. El ensamblado especificado debe tener un nombre seguro.<br /><br /> El ensamblado creado con el parámetro `TemplateFile` será un ensamblado satélite. Este parámetro corresponde a la opción `/template` de [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Timeout` | Parámetro `Int32` opcional.<br /><br /> Especifica el tiempo en milisegundos después del cual se termina la tarea ejecutable. El valor predeterminado es `Int.MaxValue`, que indica que no hay período de tiempo de espera. |
| `Title` | Parámetro `String` opcional.<br /><br /> Especifica una cadena para el campo `Title` del ensamblado. Para obtener más información, consulte la documentación sobre la opción `/title` en [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ToolPath` | Parámetro `String` opcional.<br /><br /> Especifica la ubicación desde donde la tarea cargará el archivo ejecutable subyacente (Al.exe). Si no se especifica este parámetro, la tarea usa la ruta de instalación del SDK que se corresponde con la versión de la plataforma que está ejecutando MSBuild. |
| `Trademark` | Parámetro `String` opcional.<br /><br /> Especifica una cadena para el campo `Trademark` del ensamblado. Para obtener más información, consulte la documentación sobre la opción `/trade[mark]` en [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Version` | Parámetro `String` opcional.<br /><br /> Especifica la información de versión de este ensamblado. El formato de la cadena es *principal.secundaria.compilación.revisión*. El valor predeterminado es 0. Para obtener más información, consulte la documentación sobre la opción `/v[ersion]` en [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Icon` | Parámetro `String` opcional.<br /><br /> Inserta un archivo *.ico* en el ensamblado. El archivo *.ico* proporciona al archivo de salida la apariencia deseada en el Explorador de archivos. Este parámetro corresponde a la opción `/win32icon` de [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Resource` | Parámetro `String` opcional.<br /><br /> Inserta un recurso de Win32 (archivo *.res*) en el archivo de salida. Para obtener más información, consulte la documentación sobre la opción `/win32res` en [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Ejemplo

 En el ejemplo siguiente se crea un ensamblado con las opciones especificadas.

```xml
<AL
    EmbedResources="@(EmbeddedResource)"
    Culture="%(EmbeddedResource.Culture)"
    TemplateFile="@(IntermediateAssembly)"
    KeyContainer="$(KeyContainerName)"
    KeyFile="$(KeyOriginatorFile)"
    DelaySign="$(DelaySign)"

    OutputAssembly=
       "%(EmbeddedResource.Culture)\$(TargetName).resources.dll">

    <Output TaskParameter="OutputAssembly"
        ItemName="SatelliteAssemblies"/>
</AL>
```

## <a name="see-also"></a>Vea también

* [Referencia de tareas](../msbuild/msbuild-task-reference.md)
* [Tareas](../msbuild/msbuild-tasks.md)
