---
title: MT (Tarea) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- vc.task.mt
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBUILD (C++), MT task
- MT task (MSBuild (C++))
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f90a1349771ab67f342a3490874cd422051cac2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595035"
---
# <a name="mt-task"></a>MT (tarea)
Incluye la herramienta Manifiesto de Microsoft *mt.exe*. Para más información, consulte [Mt.exe](/windows/desktop/SbsCs/mt-exe).

## <a name="parameters"></a>Parámetros
 En la siguiente tabla se describen los parámetros de la tarea **MT**. La mayoría de los parámetros de tarea, así como algunos conjuntos de parámetros, corresponden a una opción de línea de comandos.

> [!NOTE]
> La documentación de *mt.exe* usa un guion ( **-** ) como prefijo para las opciones de línea de comandos, pero en este tema se usa una barra diagonal ( **/** ). Se aceptan ambos prefijos.

|Parámetro|Descripción|
|---------------|-----------------|
|**AdditionalManifestFiles**|Parámetro **String[]** opcional.<br /><br /> Especifica el nombre de uno o varios archivos de manifiesto.<br /><br /> Para más información, consulte la opción **/manifest** de [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**AdditionalOptions**|Parámetro **String** opcional.<br /><br /> Una lista de opciones de la línea de comandos. Por ejemplo, /\<option1> /\<option2> /\<option#>. Use este parámetro para especificar opciones de la línea de comandos que no están representadas por ningún otro parámetro de tarea **MT**.<br /><br /> Para más información, consulte [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**AssemblyIdentity**|Parámetro **String** opcional.<br /><br /> Especifica los valores de atributo del elemento **assemblyIdentity** del manifiesto. Especifique una lista delimitada por comas, donde el primer componente sea el valor del atributo `name`, seguido de uno o varios pares de nombre/valor que tengan el formato *\<nombre de atributo>=<valor_atributo>* .<br /><br /> Para más información, consulte la opción **/identity** de [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ComponentFileName**|Parámetro **String** opcional.<br /><br /> Especifica el nombre de la biblioteca de vínculos dinámicos que pretende compilar desde los archivos *.rgs* o *.tlb*. Este parámetro es obligatorio si especifica los parámetros de la tarea MT **RegistrarScriptFile** o **TypeLibraryFile**.<br /><br /> Para más información, consulte la opción **/dll** de [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**DependencyInformationFile**|Parámetro **String** opcional.<br /><br /> Especifica el archivo de información de dependencia que usa Visual Studio para realizar un seguimiento de la información de dependencia de compilación para la herramienta de manifiesto.|
|**EmbedManifest**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, incrusta el archivo de manifiesto en el ensamblado. Si es `false`, se crea como un archivo de manifiesto independiente.|
|**EnableDPIAwareness**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, agrega información al manifiesto que marca la aplicación para que reconozca valores de ppp. Si escribe una aplicación compatible con los valores de ppp, la interfaz de usuario tendrá una apariencia similar en una amplia variedad de opciones de visualización de valores altos de ppp.<br /><br /> Para más información, consulte [High DPI](/windows/desktop/win7devguide/high-dpi) (Alto DPI).|
|**GenerateCatalogFiles**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, genera archivos de definición de catálogo ( *.cdf*).<br /><br /> Para más información, consulte la opción **/makecdfs** de [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**GenerateCategoryTags**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, hace que se generen etiquetas de categoría. Si este parámetro es `true`, también se debe especificar el parámetro de tarea **ManifestFromManagedAssemblyMT**.<br /><br /> Para más información, consulte la opción **/category** de [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**InputResourceManifests**|Parámetro **String** opcional.<br /><br /> Proporcione el manifiesto de un recurso de tipo RT_MANIFEST que tenga el identificador especificado. Especifique un recurso con el formato, \<file>[;[#]\<resource_id>], donde el parámetro opcional \<resource_id> es un número de 16 bits no negativo.<br /><br /> Si no se especifica ningún `resource_id`, se usará el valor predeterminado CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Para más información, consulte la opción **/inputresource** de [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ManifestFromManagedAssembly**|Parámetro **String** opcional.<br /><br /> Genera un manifiesto del ensamblado administrado especificado.<br /><br /> Para más información, consulte la opción **/managedassemblyname** de [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ManifestToIgnore**|Parámetro **String** opcional.<br /><br /> (No usado).|
|**OutputManifestFile**|Parámetro **String** opcional.<br /><br /> Especifica el nombre del manifiesto de salida. Si se omite este parámetro y solo se opera un manifiesto en él, ese manifiesto se modificará.<br /><br /> Para más información, consulte la opción **/out:** de [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**OutputResourceManifests**|Parámetro **String** opcional.<br /><br /> Genere el manifiesto a un recurso de tipo RT_MANIFEST que tenga el identificador especificado. El recurso tiene el formato, \<file>[;[#]\<resource_id>], donde el parámetro opcional \<resource_id> es un número de 16 bits no negativo.<br /><br /> Si no se especifica ningún `resource_id`, se usará el valor predeterminado CREATEPROCESS_MANIFEST_RESOURCE (1).<br /><br /> Para más información, consulte la opción **/outputresource** de [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**RegistrarScriptFile**|Parámetro **String** opcional.<br /><br /> Especifica el nombre del archivo de script de registrador ( *.rgs*) que se usará para la compatibilidad con manifiestos COM sin registro.<br /><br /> Para más información, consulte la opción **/rgs** de [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ReplacementsFile**|Parámetro **String** opcional.<br /><br /> Especifica el archivo que contiene los valores de las cadenas reemplazables en el archivo de script de registrador ( *.rgs*).<br /><br /> Para más información, consulte la opción **/replacements** de [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**ResourceOutputFileName**|Parámetro **String** opcional.<br /><br /> Especifica el archivo de recursos de resultados usado para incrustar el manifiesto en los resultados del proyecto.|
|**Sources**|Parámetro `ITaskItem[]` opcional.<br /><br /> Especifica una lista de archivos de código fuente de manifiesto, separados por espacios.<br /><br /> Para más información, consulte la opción **/manifest** de [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**SuppressDependencyElement**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, genera un manifiesto sin elementos de dependencia. Si este parámetro es `true`, especifique también el parámetro de tarea **ManifestFromManagedAssemblyMT**.<br /><br /> Para más información, consulte la opción **/nodependency** de [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**SuppressStartupBanner**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, evita que se muestre el copyright y el mensaje de número de versión cuando la tarea se inicia.<br /><br /> Para más información, consulte la opción **/nologo** de [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**TrackerLogDirectory**|Parámetro `String` opcional.<br /><br /> Especifica el directorio intermedio en que se almacenan los registros de seguimiento para esta tarea.|
|**TypeLibraryFile**|Parámetro **String** opcional.<br /><br /> Especifica el nombre del archivo de biblioteca de tipos ( *.tlb*). Si especifica este parámetro, especifique también el parámetro de tarea **ComponentFileNameMT**.<br /><br /> Para más información, consulte la opción **/tlb** de [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**UpdateFileHashes**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, se calcula el valor hash de los archivos de la ruta de acceso especificada por el parámetro de tarea **UpdateFileHashesSearchPathMT**. Luego se actualiza el valor del atributo **hash** del elemento **file** del manifiesto usando el valor calculado.<br /><br /> Para más información, consulte la opción **/hashupdate** de [Mt.exe](/windows/desktop/SbsCs/mt-exe). Consulte también el parámetro **UpdateFileHashesSearchPath** de esta tabla.|
|**UpdateFileHashesSearchPath**|Parámetro `String` opcional.<br /><br /> Especifica la ruta de acceso de búsqueda que se debe usar al actualizar los hashes del archivo. Use este parámetro con el parámetro de tarea **UpdateFileHashesMT**.<br /><br /> Para obtener más información, vea el parámetro **UpdateFileHashes** de esta tabla.|
|**VerboseOutput**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, muestra información de depuración detallada.<br /><br /> Para más información, consulte la opción **/verbose** de [Mt.exe](/windows/desktop/SbsCs/mt-exe).|

## <a name="see-also"></a>Vea también
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
