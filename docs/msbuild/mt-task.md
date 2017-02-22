---
title: "MT (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCManifestTool.ResourceOutputFileName"
  - "VC.Project.VCManifestTool.SuppressDependencyElement"
  - "VC.Project.VCManifestTool.ManifestFromManagedAssembly"
  - "VC.Project.VCManifestTool.GenerateCategoryTags"
  - "VC.Project.VCManifestTool.EnableDPIAwareness"
  - "vc.task.mt"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBUILD (Visual C++), MT (tarea)"
  - "MT (tarea) (MSBuild (Visual C++))"
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MT (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Incluye la Herramienta Manifiesto de Microsoft, mt.exe.  Para obtener más información, vea "Mt.exe" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea **MT**.  La mayoría de los parámetros de tarea, y algunos conjuntos de parámetros, corresponden a una opción de la línea de comandos.  
  
> [!NOTE]
>  La documentación de mt.exe utiliza un guión \(**\-**\) como el prefijo para las opciones de la línea de comandos, pero este tema utiliza una barra diagonal \(**\/**\).  Cualquier prefijo es aceptable.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|**AdditionalManifestFiles**|Parámetro **String\[\]** opcional.<br /><br /> Especifica el nombre de uno o más archivos de manifiesto.<br /><br /> Para obtener más información, vea la opción **\/manifest** de "Mt.exe" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**AdditionalOptions**|Parámetro **String** opcional.<br /><br /> Una lista de opciones de la línea de comandos.  Por ejemplo, "*\/opción1 \/opción2 \/opción\#*".  Utilice este parámetro para especificar opciones de la línea de comandos que no son representadas por ningún otro parámetro de tarea **MT**.<br /><br /> Para obtener más información, vea "Mt.exe" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**AssemblyIdentity**|Parámetro **String** opcional.<br /><br /> Especifica los valores de atributo del elemento **assemblyIdentity** del manifiesto.  Especifique una lista delimitada por comas, en la que el primer componente es el valor del atributo `name`, seguido por uno o varios pares nombre\-valor que tienen el formato, *\<nombre de atributo\> \=\<valor\_de\_atributo\>*.<br /><br /> Para obtener más información, vea la opción **\/identity** de "Mt.exe" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**ComponentFileName**|Parámetro **String** opcional.<br /><br /> Especifica el nombre de la biblioteca de vínculos dinámicos que piensa compilar a partir de los archivos .rgs o .tlb.  Se requiere este parámetro si se especifican los parámetros **RegistrarScriptFile** o **TypeLibraryFile** de la tarea MT.<br /><br /> Para obtener más información, vea la opción **\/dll** de "Mt.exe" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**DependencyInformationFile**|Parámetro **String** opcional.<br /><br /> Especifica el archivo de información de dependencia utilizado por Visual Studio para realizar el seguimiento de la información de dependencia de compilación de la herramienta de manifiesto.|  
|**EmbedManifest**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, incrusta el archivo de manifiesto en el ensamblado.  Si es `false`, se crea como un archivo de manifiesto independiente.|  
|**EnableDPIAwareness**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, se agrega a la información de manifiesto que marca la aplicación como conocedora del valor de PPP.  Escribir una aplicación que tiene en cuenta los PPP hace que la interfaz de usuario tenga una buena apariencia con una gran variedad de valores de pantalla con PPP altos.<br /><br /> Para obtener más información, vea "High DPI" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**GenerateCatalogFiles**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, genera archivos de definición \(.cdf\) de catálogo.<br /><br /> Para obtener más información, vea la opción **\/makecdfs** de "Mt.exe" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**GenerateCategoryTags**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, hace que se generen etiquetas de categoría.  Si este parámetro es `true`, también se debe especificar el parámetro de tarea **ManifestFromManagedAssembly MT**.<br /><br /> Para obtener más información, vea la opción **\/category** de "Mt.exe" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**InputResourceManifests**|Parámetro **String** opcional.<br /><br /> Proporcione el manifiesto de un recurso de tipo RT\_MANIFEST que tiene el identificador especificado.  Especifique un recurso con el formato, *\<archivo\>\[***;** *\[***\#***\]\<id\_de\_recurso\>\]*, donde el parámetro `resource_id` opcional es un número de 16 bits no negativo.<br /><br /> Si no se especifica ningún `resource_id`, se utiliza el valor predeterminado CREATEPROCESS\_MANIFEST\_RESOURCE \(1\).<br /><br /> Para obtener más información, vea la opción **\/inputresource** de "Mt.exe" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**ManifestFromManagedAssembly**|Parámetro **String** opcional.<br /><br /> Genera un manifiesto a partir del ensamblado administrado especificado.<br /><br /> Para obtener más información, vea la opción **\/managedassemblyname** de "Mt.exe" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**ManifestToIgnore**|Parámetro **String** opcional.<br /><br /> \(No se utiliza\).|  
|**OutputManifestFile**|Parámetro **String** opcional.<br /><br /> Especifica el nombre del manifiesto de salida.  Si se omite este parámetro y solo se trabaja en un manifiesto, ese manifiesto se modifica en contexto.<br /><br /> Para obtener más información, vea la opción **\/out** de "Mt.exe" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**OutputResourceManifests**|Parámetro **String** opcional.<br /><br /> Establezca la salida del manifiesto a un recurso de tipo RT\_MANIFEST que tiene el identificador especificado.  El recurso tiene el formato, *\<archivo\>\[***;** *\[***\#***\]\<id\_de\_recurso\>\]*, donde el parámetro `resource_id` opcional es un número de 16 bits no negativo.<br /><br /> Si no se especifica ningún `resource_id`, se utiliza el valor predeterminado CREATEPROCESS\_MANIFEST\_RESOURCE \(1\).<br /><br /> Para obtener más información, vea la opción **\/outputresource** de "Mt.exe" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**RegistrarScriptFile**|Parámetro **String** opcional.<br /><br /> Especifica el nombre del archivo de script del Registro \(.rgs\) que se debe utilizar para la compatibilidad de manifiestos COM sin registro.<br /><br /> Para obtener más información, vea la opción **\/rgs** de "Mt.exe" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**ReplacementsFile**|Parámetro **String** opcional.<br /><br /> Especifica el archivo que contiene los valores de las cadenas reemplazables en el archivo de script del Registro \(.rgs\).<br /><br /> Para obtener más información, vea la opción **\/replacements** de "Mt.exe" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**ResourceOutputFileName**|Parámetro **String** opcional.<br /><br /> Especifica el archivo de recursos de salida utilizado para incrustar el manifiesto en la salida del proyecto.|  
|**Sources**|Parámetro `ITaskItem[]` opcional.<br /><br /> Especifica una lista de archivos de origen de manifiesto separada por espacios.<br /><br /> Para obtener más información, vea la opción **\/manifest** de "Mt.exe" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**SuppressDependencyElement**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, genera un manifiesto sin elementos de dependencia.  Si este parámetro es `true`, especifique también el parámetro de tarea **ManifestFromManagedAssembly MT**.<br /><br /> Para obtener más información, vea la opción **\/nodependency** de "Mt.exe" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**SuppressStartupBanner**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, evita la presentación del copyright y del mensaje de número de versión cuando la tarea se inicia.<br /><br /> Para obtener más información, vea la opción **\/nologo** de "Mt.exe" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**TrackerLogDirectory**|Parámetro `String` opcional.<br /><br /> Especifica el directorio intermedio donde se almacenan los registros de seguimiento de esta tarea.|  
|**TypeLibraryFile**|Parámetro **String** opcional.<br /><br /> Especifica el nombre del archivo de la biblioteca de tipos \(.tlb\).  Si especifica este parámetro, especifique también el parámetro de tarea **ComponentFileName MT**.<br /><br /> Para obtener más información, vea la opción **\/tlb** de "Mt.exe" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**UpdateFileHashes**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, calcula el valor hash de los archivos en la ruta de acceso especificada por el parámetro de tarea **UpdateFileHashesSearchPathMT** y, a continuación, actualiza el valor del atributo **hash** del elemento **file** del manifiesto utilizando el valor calculado.<br /><br /> Para obtener más información, vea la opción **\/hashupdate** de "Mt.exe" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  También vea el parámetro **UpdateFileHashesSearchPath** de esta tabla.|  
|**UpdateFileHashesSearchPath**|Parámetro `String` opcional.<br /><br /> Especifica la ruta de búsqueda que se desea utilizar cuando se actualizan los hash de archivo.  Use este parámetro con el parámetro de tarea**UpdateFileHashes MT**.<br /><br /> Para obtener más información, vea el parámetro **UpdateFileHashes** en esta tabla.|  
|**VerboseOutput**|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, muestra información de depuración detallada.<br /><br /> Para obtener más información, vea la opción **\/verbose** de "Mt.exe" en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
  
## Comentarios  
  
## Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)