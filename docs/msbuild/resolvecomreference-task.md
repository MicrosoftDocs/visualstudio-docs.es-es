---
title: "ResolveComReference (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, ResolveCOMReference (tarea)"
  - "ResolveCOMReference (tarea) [MSBuild]"
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# ResolveComReference (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Toma una lista de uno o más nombres de biblioteca de tipos o archivos .tlb y resuelve esas bibliotecas de tipos en ubicaciones de disco.  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `ResolveCOMReference`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`DelaySign`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, se sitúa la clave pública en el ensamblado.  Si es `false`, firma totalmente el ensamblado.|  
|`EnvironmentVariables`|Parámetro `String[]` opcional.<br /><br /> Matriz de pares de variables de entorno, separadas por signos igual.  Estas variables se pasan a los archivos tlbimp.exe y aximp.exe generados además de, o invalidando selectivamente, el bloque de entorno regular.|  
|`ExecuteAsTool`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, se ejecutan tlbimp.exe y aximp.exe desde la versión de .NET Framework de destino adecuada fuera de proceso para generar los ensamblados de contenedor necesarios.  Este parámetro permite la compatibilidad con múltiples versiones.|  
|`IncludeVersionInInteropName`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, la versión de la biblioteca de tipos será incluida en el nombre de contenedor.  El valor predeterminado es `false`.|  
|`KeyContainer`|Parámetro `String` opcional.<br /><br /> Especifica un contenedor que contiene una clave pública\/privada<br /><br /> par de claves.|  
|`KeyFile`|Parámetro `String` opcional.<br /><br /> Especifica un elemento que contiene una clave pública\/privada<br /><br /> par de claves.|  
|`NoClassMembers`|Parámetro `Boolean` opcional.|  
|`ResolvedAssemblyReferences`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica las referencias de ensamblado resueltas.|  
|`ResolvedFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los nombres de archivo completos del disco asociados a las ubicaciones físicas de las bibliotecas de tipos que se proporcionaron como entrada para esta tarea.|  
|`ResolvedModules`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.|  
|`SdkToolsPath`|Parámetro [String](assetId:///String?qualifyHint=False&autoUpgrade=True) opcional.<br /><br /> Si `ExecuteAsTool` es `true`, este parámetro debe establecerse como la ruta de acceso a las herramientas del SDK para la versión de .NET Framework de destino.|  
|`StateFile`|Parámetro assetId:///String?qualifyHint=False&autoUpgrade=True opcional.<br /><br /> Especifica el archivo caché de las marcas de tiempo de los componentes COM.  Si no está presente, cada ejecución regenerará todos los contenedores.|  
|`TargetFrameworkVersion`|Parámetro assetId:///String?qualifyHint=False&autoUpgrade=True opcional.<br /><br /> Especifica la versión de .NET Framework de destino del proyecto.<br /><br /> El valor predeterminado es `String.Empty`.  lo que significa que no hay filtrado para una referencia basada en la versión de .NET Framework de destino.|  
|`TargetProcessorArchitecture`|Parámetro assetId:///String?qualifyHint=False&autoUpgrade=True opcional.<br /><br /> Especifica la arquitectura preferida del procesador de destino.  Pasado a la marca tlbimp.exe \/equipo después de la traducción.<br /><br /> El valor del parámetro debe ser un miembro de <xref:Microsoft.Build.Utilities.ProcessorArchitecture>.|  
|`TypeLibFiles`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica la ruta de acceso del archivo de biblioteca de tipos para las referencias COM.  Los elementos incluidos en este parámetro pueden contener metadatos de elemento.  Para obtener más información, vea más adelante la sección "Metadatos del elemento TypeLibFiles".|  
|`TypeLibNames`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los nombres de biblioteca de tipos que se deben resolver.  Los elementos incluidos en este parámetro deben contener algunos metadatos de elemento.  Para obtener más información, vea más adelante la sección "Metadatos del elemento TypeLibNames".|  
|`WrapperOutputDirectory`|Parámetro `String` opcional.<br /><br /> Ubicación en el disco donde se coloca el ensamblado de interoperabilidad generado.  Si no se especifican estos metadatos de elemento, la tarea utiliza la ruta de acceso absoluta del directorio en el que está ubicado el archivo de proyecto.|  
  
## Comentarios  
  
## Metadatos del elemento TypeLibNames  
 En la tabla siguiente se describen los metadatos de elemento disponibles para los elementos pasados al parámetro `TypeLibNames`.  
  
|Metadatos|Descripción|  
|---------------|-----------------|  
|`GUID`|Metadatos de elemento necesarios.<br /><br /> Identificador de interfaz \(GUID\) para la biblioteca de tipos.  Si no se especifican estos metadatos de elemento, se produce un error en la tarea.|  
|`VersionMajor`|Metadatos de elemento necesarios.<br /><br /> La versión principal de la biblioteca de tipos.  Si no se especifican estos metadatos de elemento, se produce un error en la tarea.|  
|`VersionMinor`|Metadatos de elemento necesarios.<br /><br /> La versión secundaria de la biblioteca de tipos.  Si no se especifican estos metadatos de elemento, se produce un error en la tarea.|  
|`LocaleIdentifier`|Metadatos de elemento opcionales.<br /><br /> El identificador de configuración regional \(o LCID\) para la biblioteca de tipos.  Se especifica como un valor de 32 bits que identifica el lenguaje humano preferido por un usuario, una región o una aplicación.  Si no se especifican estos metadatos de elemento, la tarea utiliza un identificador de configuración regional predeterminado "0."|  
|`WrapperTool`|Metadatos de elemento opcionales.<br /><br /> Especifica la herramienta contenedor que se utiliza para generar el contenedor de ensamblado para esta biblioteca de tipos.  Si no se especifican estos metadatos de elemento, la tarea utiliza una herramienta contenedor predeterminada "tlbimp".  Las opciones disponibles de bibliotecas de tipos, sin distinción entre mayúsculas y minúsculas, son las siguientes:<br /><br /> -   `Primary`: Utilice esta herramienta contenedor cuando desee utilizar un ensamblado de interoperabilidad primario ya generado para el componente COM.  Cuando utilice esta herramienta contenedor, no especifique un directorio de resultados de contenedor, ya que provocaría un error en la tarea.<br />-   `TLBImp`: Utilice esta herramienta contenedor cuando desee generar un ensamblado de interoperabilidad para el componente COM.<br />-   `AXImp`: Utilice esta herramienta contenedor cuando desee generar un ensamblado de interoperabilidad para un control ActiveX.|  
  
## Metadatos de elemento TypeLibFiles  
 En la tabla siguiente se describen los metadatos de elemento disponibles para los elementos pasados al parámetro `TypeLibFiles`.  
  
|Metadatos|Descripción|  
|---------------|-----------------|  
|`WrapperTool`|Metadatos de elemento opcionales.<br /><br /> Especifica la herramienta contenedor que se utiliza para generar el contenedor de ensamblado para esta biblioteca de tipos.  Si no se especifican estos metadatos de elemento, la tarea utiliza una herramienta contenedor predeterminada "tlbimp".  Las opciones disponibles de bibliotecas de tipos, sin distinción entre mayúsculas y minúsculas, son las siguientes:<br /><br /> -   `Primary`: Utilice esta herramienta contenedor cuando desee utilizar un ensamblado de interoperabilidad primario ya generado para el componente COM.  Cuando utilice esta herramienta contenedor, no especifique un directorio de resultados de contenedor, ya que provocaría un error en la tarea.<br />-   `TLBImp`: Utilice esta herramienta contenedor cuando desee generar un ensamblado de interoperabilidad para el componente COM.<br />-   `AXImp`: Utilice esta herramienta contenedor cuando desee generar un ensamblado de interoperabilidad para un control ActiveX.|  
  
> [!NOTE]
>  Cuanta más información proporcione para identificar únicamente una biblioteca de tipos, mayores posibilidades habrá de que la tarea se resuelva en el archivo correcto del disco.  
  
## Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Utilities.Task> .  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [Task Base \(Clase\)](../msbuild/task-base-class.md).  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)