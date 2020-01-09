---
title: ResolveComReference (Tarea) | Microsoft Docs
ms.date: 07/25/2019
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveCOMReference task
- ResolveCOMReference task [MSBuild]
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fdc6c6ccd58bcc83cc37ff3a9f7888af837ed6e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595207"
---
# <a name="resolvecomreference-task"></a>Tarea ResolveComReference

Toma una lista de uno o varios nombres de biblioteca de tipos o archivos *.tlb* y resuelve esas bibliotecas de tipos en ubicaciones de disco.

## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de la tarea `ResolveCOMReference` .

|Parámetro|Descripción|
|---------------|-----------------|
|`DelaySign`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, coloca la clave pública en el ensamblado. Si `false`, firma completamente el ensamblado.|
|`EnvironmentVariables`|Parámetro `String[]` opcional.<br /><br /> Matriz de pares de variables de entorno, separados por signos igual. Estas variables se pasan a spawned *tlbimp.exe* y *aximp.exe* y, además, pasan el bloque de entorno normal o lo invalidan de manera selectiva.|
|`ExecuteAsTool`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, se ejecutan *tlbimp.exe* y *aximp.exe* desde la plataforma de destino adecuada fuera de proceso para generar los ensamblados de contenedor necesarios. Este parámetro permite compatibilidad con múltiples versiones.|
|`IncludeVersionInInteropName`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, la versión typelib se incluirá en el nombre del contenedor. De manera predeterminada, es `false`.|
|`KeyContainer`|Parámetro `String` opcional.<br /><br /> Especifica un contenedor que contiene un par de claves pública-privada.|
|`KeyFile`|Parámetro `String` opcional.<br /><br /> Especifica un elemento que contiene un par de claves pública-privada.|
|`NoClassMembers`|Parámetro `Boolean` opcional.|
|`ResolvedAssemblyReferences`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica las referencias de ensamblado resueltas.|
|`ResolvedFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los archivos completos en disco que corresponden a las ubicaciones físicas de las bibliotecas de tipos que se proporcionaron como entrada para esta tarea.|
|`ResolvedModules`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.|
|`SdkToolsPath`|Parámetro <xref:System.String?displayProperty=fullName> opcional.<br /><br /> Si `ExecuteAsTool` es `true`, este parámetro debe establecerse en la ruta de acceso de las herramientas de SDK para la versión del marco que se tiene como destino.|
|`StateFile`|Parámetro `String` opcional.<br /><br /> Especifica el archivo de caché para las marcas de tiempo del componente COM. Si no está presente, cada ejecución volverá a generar todos los contenedores.|
|`TargetFrameworkVersion`|Parámetro `String` opcional.<br /><br /> Especifica la versión de la plataforma de destino del proyecto.<br /><br /> De manera predeterminada, es `String.Empty`. Significa que no existe filtrado para una referencia basándose en la plataforma de destino.|
|`TargetProcessorArchitecture`|Parámetro `String` opcional.<br /><br /> Especifica la arquitectura del procesador de destino preferida. Se ha pasado a la marca de equipo *tlbimp.exe* después de la traducción.<br /><br /> El valor del parámetro debe ser un miembro de <xref:Microsoft.Build.Utilities.ProcessorArchitecture>.|
|`TypeLibFiles`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica la ruta de acceso del archivo de biblioteca de tipos a las referencias COM. Los elementos incluidos en este parámetro pueden contener metadatos de elementos. Para más información, consulte la sección [Metadatos de elementos TypeLibFiles](#typelibfiles-item-metadata) a continuación.|
|`TypeLibNames`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los nombres de las bibliotecas de tipos que se resolverán. Los elementos incluidos en este parámetro deben contener algunos metadatos de elementos. Para más información, consulte la sección [Metadatos de elementos TypeLibNames](#typelibnames-item-metadata) a continuación.|
|`WrapperOutputDirectory`|Parámetro `String` opcional.<br /><br /> Ubicación en el disco donde se coloca el ensamblado de interoperabilidad generado. Si estos metadatos de elementos no se especifican, la tarea usa la ruta de acceso absoluta del directorio donde se encuentra el archivo del proyecto.|

## <a name="typelibnames-item-metadata"></a>Metadatos de elementos TypeLibNames

 En la tabla siguiente se describen los metadatos de elementos disponibles para los elementos que se han pasado al parámetro `TypeLibNames`.

|Metadatos|Descripción|
|--------------|-----------------|
|`GUID`|Metadatos de elementos necesarios.<br /><br /> GUID de la biblioteca de tipos. Si estos metadatos de elementos no se especifican, se produce un error en la tarea.|
|`VersionMajor`|Metadatos de elementos necesarios.<br /><br /> La versión principal de la biblioteca de tipos. Si estos metadatos de elementos no se especifican, se produce un error en la tarea.|
|`VersionMinor`|Metadatos de elementos necesarios.<br /><br /> La versión secundaria de la biblioteca de tipos. Si estos metadatos de elementos no se especifican, se produce un error en la tarea.|
|`EmbedInteropTypes`|Metadatos `Boolean` opcionales.<br /><br />  Si `true`, inserte los tipos de interoperabilidad de esta referencia directamente en el ensamblado en lugar de generar un archivo DLL de interoperabilidad.|
|`LocaleIdentifier`|Metadatos de elementos opcionales.<br /><br /> El identificador de configuración regional (o LCID) de la biblioteca de tipos. Esto se especifica como un valor de 32 bits que identifica el lenguaje humano preferido por un usuario, una región o una aplicación. Si estos metadatos de elementos no se especifican, la tarea usa un identificador de configuración regional predeterminado de "0".|
|`WrapperTool`|Metadatos de elementos opcionales.<br /><br /> Especifica la herramienta contenedor que se usa para generar el contenedor de ensamblado para esta biblioteca de tipos. Si estos metadatos de elementos no se especifican, la tarea usa una herramienta contenedor predeterminada de "tlbimp". Las opciones que no distinguen mayúsculas de minúsculas disponibles de typelibs son:<br /><br /> -   `Primary`: Use esta herramienta contenedor cuando quiera usar un ensamblado de interoperabilidad primario que ya se ha generado para el componente COM. Cuando use esta herramienta contenedor, no especifique un directorio de salida del contenedor porque provocará un error en la tarea.<br />-   `TLBImp`: Use esta herramienta contenedor cuando quiera generar un ensamblado de interoperabilidad para el componente COM.<br />-   `AXImp`: use esta herramienta contenedor cuando quiera generar un ensamblado de interoperabilidad para un control ActiveX.|

## <a name="typelibfiles-item-metadata"></a>Metadatos de elementos TypeLibFiles

 En la tabla siguiente se describen los metadatos de elementos disponibles para los elementos que se han pasado al parámetro `TypeLibFiles`.

|Metadatos|Descripción|
|--------------|-----------------|
|`EmbedInteropTypes`|Parámetro `Boolean` opcional.<br /><br />  Si `true`, inserte los tipos de interoperabilidad de esta referencia directamente en el ensamblado en lugar de generar un archivo DLL de interoperabilidad.|
|`WrapperTool`|Metadatos de elementos opcionales.<br /><br /> Especifica la herramienta contenedor que se usa para generar el contenedor de ensamblado para esta biblioteca de tipos. Si estos metadatos de elementos no se especifican, la tarea usa una herramienta contenedor predeterminada de "tlbimp". Las opciones que no distinguen mayúsculas de minúsculas disponibles de typelibs son:<br /><br /> -   `Primary`: Use esta herramienta contenedor cuando quiera usar un ensamblado de interoperabilidad primario que ya se ha generado para el componente COM. Cuando use esta herramienta contenedor, no especifique un directorio de salida del contenedor porque provocará un error en la tarea.<br />-   `TLBImp`: Use esta herramienta contenedor cuando quiera generar un ensamblado de interoperabilidad para el componente COM.<br />-   `AXImp`: Use esta herramienta contenedor cuando quiera generar un ensamblado de interoperabilidad para un control ActiveX.|

> [!NOTE]
> Cuanta más información proporcione para identificar de manera exclusiva una biblioteca de tipos, mayor será la posibilidad de que la tarea resuelva el archivo correcto en el disco.

## <a name="remarks"></a>Comentarios

Además de los parámetros enumerados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [Task Base (Clase)](../msbuild/task-base-class.md).

No es necesario registrar un archivo DLL COM en la máquina para que esta tarea funcione.

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
