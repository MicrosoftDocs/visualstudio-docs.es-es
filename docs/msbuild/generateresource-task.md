---
title: GenerateResource (Tarea) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateResource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateResource task
- GenerateResource task [MSBuild]
ms.assetid: c0aff32f-f2cc-46f6-9c3e-a5c9f8f912b1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c830b640b3efb4e963d62402bbf68d1bc7dff0e9
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176959"
---
# <a name="generateresource-task"></a>GenerateResource (tarea)
Convierte entre archivos *.txt* y *.resx* (formato de recursos basado en XML) y archivos *.resources* binarios de Common Language Runtime, que se pueden insertar en un archivo ejecutable binario en tiempo de ejecución o compilar en ensamblados satélite. Esta tarea normalmente se usa para convertir archivos *.txt* o *.resx* en archivos *.resources*. La tarea `GenerateResource` es funcionalmente similar a [resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator).  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `GenerateResource` .  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`AdditionalInputs`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene entradas adicionales a la comprobación de dependencias realizada por esta tarea. Por ejemplo, los archivos de proyecto y de destino normalmente deben ser entradas de modo que, si se actualizan, se vuelvan a generar todos los recursos.|  
|`EnvironmentVariables`|Parámetro `String[]` opcional.<br /><br /> Especifica una matriz de pares nombre-valor de variables de entorno que deben pasarse al ejecutable *resgen.exe* generado, además del bloque de entorno normal (o su invalidación selectiva).|  
|`ExcludedInputPaths`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica una matriz de elementos que especifican rutas de acceso en las que las entradas de las que se lleva a cabo el seguimiento se van a omitir durante la comprobación de actualización.|  
|`ExecuteAsTool`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, se ejecutan *tlbimp.exe* y *aximp.exe* desde la plataforma de destino adecuada fuera de proceso para generar los ensamblados de contenedor necesarios. Este parámetro permite compatibilidad con múltiples versiones de `ResolveComReferences`.|  
|`FilesWritten`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene los nombres de todos los archivos escritos en el disco. Esto incluye el archivo de la caché, si existe. Este parámetro es útil para las implementaciones de Clean.|  
|`MinimalRebuildFromTracking`|Parámetro `Boolean` opcional.<br /><br /> Obtiene o establece un modificador que especifica si se va a usar la compilación incremental de la que se realiza el seguimiento. Si es `true`, se activa la compilación incremental; de lo contrario, se forzará una recompilación.|  
|`NeverLockTypeAssemblies`|Parámetro `Boolean` opcional.<br /><br /> Obtiene o establece un valor booleano que especifica si se va a crear una nueva clase [AppDomain](/dotnet/api/system.appdomain) para evaluar los archivos de recursos (*.resx*) (true) o crear una nueva clase [AppDomain](/dotnet/api/system.appdomain) solo cuando los archivos de recursos hagan referencia al ensamblado de un usuario (false).|  
|`OutputResources`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica el nombre de los archivos generados, como los archivos *.resources*. Si no especifica un nombre, se usa el nombre del archivo de entrada coincidente, y el archivo *.resources* que se crea se coloca en el directorio que contiene el archivo de entrada.|  
|`PublicClass`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, crea una clase de recurso fuertemente tipada como clase pública.|  
|`References`|Parámetro `String[]` opcional.<br /><br /> Hace referencia a tipos de carga en archivos *.resx*. Los elementos de datos del archivo *.resx* pueden tener un tipo .NET. Cuando se lee el archivo *.resx*, se debe resolver esta situación. Normalmente, se resuelve correctamente utilizando reglas de carga de tipo estándar. Si proporciona los ensamblados en `References`, serán prioritarios.<br /><br /> Este parámetro no se requiere para los recursos fuertemente tipados.|  
|`SdkToolsPath`|Parámetro `String` opcional.<br /><br /> Especifica la ruta de acceso a las herramientas del SDK, como *resgen.exe*.|  
|`Sources`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica los elementos que se van a convertir. Los elementos pasados a este parámetro deben tener una de las extensiones de archivo siguientes:<br /><br /> -   *.txt*: especifica la extensión de un archivo de texto que se va a convertir. Los archivos de texto solo pueden contener recursos de cadena.<br />-   *.resx*: especifica la extensión de un archivo de recursos basado en XML que se va a convertir.<br />-   *.restext*: especifica el mismo formato que *.txt*. Esta extensión diferente es útil si desea distinguir claramente los archivos de origen que contienen recursos de otros archivos de origen en su proceso de compilación.<br />-   *.resources*: especifica la extensión de un archivo de recursos que se va a convertir.|  
|`StateFile`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica la ruta de acceso a un archivo de la caché opcional que se usa para acelerar la comprobación de dependencias de vínculos en archivos de entrada *.resx*.|  
|`StronglyTypedClassName`|Parámetro `String` opcional.<br /><br /> Especifica el nombre de clase para la clase de recurso fuertemente tipada. Si no se especifica este parámetro, se utiliza el nombre base del archivo de recursos.|  
|`StronglyTypedFilename`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el nombre de archivo para el archivo de origen. Si no se especifica este parámetro, el nombre de la clase se utiliza como nombre de archivo base, y la extensión depende del lenguaje. Por ejemplo: *MyClass.cs*.|  
|`StronglyTypedLanguage`|Parámetro `String` opcional.<br /><br /> Especifica el lenguaje que se utilizará para generar el origen de clase del recurso fuertemente tipado. Este parámetro debe coincidir exactamente con uno de los lenguajes utilizado por CodeDomProvider. Por ejemplo: `VB` o `C#`.<br /><br /> Cuando se pasa un valor a este parámetro, se indica a la tarea que genere recursos fuertemente tipados.|  
|`StronglyTypedManifestPrefix`|Parámetro `String` opcional.<br /><br /> Especifica el espacio de nombres del recurso o prefijo del manifiesto que se va a utilizar en el origen de clase generado para el recurso fuertemente tipado.|  
|`StronglyTypedNamespace`|Parámetro `String` opcional.<br /><br /> Especifica el espacio de nombres que se usará para el origen de clase generado del recurso fuertemente tipado. Si no se especifica este parámetro, cualquier recurso fuertemente tipado se encontrará en el espacio de nombres global.|  
|`TLogReadFiles`|Parámetro de solo lectura <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Obtiene una matriz de elementos que representan los registros de seguimiento de lectura.|  
|`TLogWriteFiles`|Parámetro de solo lectura <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Obtiene una matriz de elementos que representan los registros de seguimiento de escritura.|  
|`ToolArchitecture`|Parámetro <xref:System.String?displayProperty=fullName> opcional.<br /><br /> Se utiliza para determinar si debe utilizarse o no *Tracker.exe* para generar *ResGen.exe*.<br /><br /> Debe ser analizable para un miembro de la enumeración <xref:Microsoft.Build.Utilities.ExecutableType>. Si es `String.Empty`, utiliza una heurística para determinar una arquitectura predeterminada. Debe ser analizable para un miembro de la enumeración Microsoft.Build.Utilities.ExecutableType.|  
|`TrackerFrameworkPath`|Parámetro `String` opcional.<br /><br /> Especifica la ruta de acceso a la ubicación de .NET Framework adecuada que contiene *FileTracker.dll*.<br /><br /> Si está establecido, el usuario asume la responsabilidad de comprobar que el valor de bits de *FileTracker.dll* que pasa coincide con el valor de bits del archivo *ResGen.exe* que va a emplear. Si no está establecido, la tarea decide la ubicación adecuada basándose en la versión actual de .NET Framework.|  
|`TrackerLogDirectory`|Parámetro `String` opcional.<br /><br /> Especifica el directorio intermedio en el que se van a colocar los registros de seguimiento de la ejecución de esta tarea.|  
|`TrackerSdkPath`|Parámetro `String` opcional.<br /><br /> Especifica la ruta de acceso a la ubicación de Windows SDK adecuada que contiene *Tracker.exe*.<br /><br /> Si está establecido, el usuario asume la responsabilidad de comprobar que el valor de bits de *Tracker.exe* que pasa coincide con el valor de bits del archivo *ResGen.exe* que va a emplear. Si no está establecido, la tarea decide la ubicación adecuada basándose en el SDK de Windows actual.|  
|`TrackFileAccess`|Parámetro <xref:System.Boolean> opcional.<br /><br /> Si es true, el directorio del archivo de entrada se utiliza para resolver rutas de acceso de archivo relativas.|  
|`UseSourcePath`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, especifica que el directorio del archivo de entrada se utiliza para resolver las rutas de acceso de archivo relativas.|  
  
## <a name="remarks"></a>Comentarios  
 Debido a que los archivos *.resx* pueden contener vínculos a otros archivos de recursos, no basta con comparar las marcas de tiempo de los archivos *.resx* y *.resources* para ver si las salidas están actualizadas. En su lugar, la tarea `GenerateResource` sigue los vínculos de los archivos *.resx* y comprueba también las marcas de tiempo de los archivos vinculados. Esto significa que, por lo general, no debe utilizar los atributos `Inputs` y `Outputs` en el destino que contiene la tarea `GenerateResource`, puesto que podría causar que se omitiera cuando tendría que ejecutarse.  
  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension (Clase base)](../msbuild/taskextension-base-class.md).  
  
 Cuando se utiliza MSBuild 4.0 para proyectos de .NET 3.5, la compilación puede dar error en los recursos x86. Para evitar este problema, puede compilar el destino como un ensamblado AnyCPU.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa la tarea `GenerateResource` para generar archivos *.resources* a partir de los archivos especificados por la colección de elementos `Resx`.  
  
```xml  
<GenerateResource  
    Sources="@(Resx)"  
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">  
    <Output  
        TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
 La tarea `GenerateResource` utiliza los metadatos \<LogicalName> de un elemento \<EmbeddedResource> para denominar el recurso insertado en un ensamblado.  
  
 Si se da por hecho que el ensamblado se denomina myAssembly, el siguiente código genera un recurso insertado denominado *someQualifier.someResource.resources*:  
  
```xml  
<ItemGroup>   <EmbeddedResource Include="myResource.resx">       <LogicalName>someQualifier.someResource.resources</LogicalName>   </EmbeddedResource></ItemGroup>  
```  
  
 Sin los metadatos \<LogicalName>, el recurso se denominaría *myAssembly.myResource.resources*.  Este ejemplo solo se aplica al proceso de compilación de Visual Basic y Visual C#.  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
