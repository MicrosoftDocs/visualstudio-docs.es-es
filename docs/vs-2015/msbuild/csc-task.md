---
title: Csc (tarea) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Csc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Csc task [MSBuild]
- MSBuild, Csc task
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3cab96aece51252c5a847e07fc3863e6b6f0bf5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766194"
---
# <a name="csc-task"></a>Csc (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Encapsula CSC.exe y genera archivos ejecutables (.exe), archivos de biblioteca de vínculos dinámicos (.dll) o archivos de módulos de códigos (.netmodule). Para obtener más información sobre CSC.exe, consulte [Opciones del compilador de C#](http://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44).  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `Csc` .  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Parámetro `String[]` opcional.<br /><br /> Especifica más directorios donde buscar referencias. Para obtener más información, consulte [/lib (Opciones del compilador de C#)](http://msdn.microsoft.com/library/b0efcc88-e8aa-4df4-a00b-8bdef70b7673).|  
|`AddModules`|Parámetro `String` opcional.<br /><br /> Especifica uno o varios módulos que formarán parte del ensamblado. Para obtener más información, consulte [/addmodule (Opciones del compilador de C#)](http://msdn.microsoft.com/library/ed604546-0dc2-4bd4-9a3e-610a8d973e58).|  
|`AllowUnsafeBlocks`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, compila el código que utiliza la palabra clave [unsafe](http://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0). Para obtener más información, consulte [/unsafe (Opciones del compilador de C#)](http://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc).|  
|`ApplicationConfiguration`|Parámetro `String` opcional.<br /><br /> Especifique el archivo de configuración de la aplicación que contiene una configuración de enlace de ensamblados.|  
|`BaseAddress`|Parámetro `String` opcional.<br /><br /> Especifica la dirección base preferida para cargar una DLL. La dirección base predeterminada para un archivo DLL se establece mediante [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Common Language Runtime. Para obtener más información, consulte [/baseaddress (Opciones del compilador de C#)](http://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).|  
|`CheckForOverflowUnderflow`|Parámetro `Boolean` opcional.<br /><br /> Especifica si la aritmética de enteros que desborda los límites del tipo de datos inicia una excepción en tiempo de ejecución. Para obtener más información, consulte [/checked (Opciones del compilador de C#)](http://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).|  
|`CodePage`|Parámetro `Int32` opcional.<br /><br /> Especifica la página de códigos que se va a usar para todos los archivos de código fuente de la compilación. Para obtener más información, consulte [/codepage (Opciones del compilador de C#)](http://msdn.microsoft.com/library/75942989-b69a-4308-90a0-840c73d2c478).|  
|`DebugType`|Parámetro `String` opcional.<br /><br /> Especifica el tipo de depuración. `DebugType` puede ser `full` o `pdbonly`. El valor predeterminado es `full`, que permite a un depurador adjuntarlo a un programa en ejecución. Especificar `pdbonly` permite depurar el código fuente cuando el programa se inicia en el depurador, pero solo mostrará el ensamblador cuando el programa que se ejecuta está asociado al depurador.<br /><br /> Este parámetro invalida el parámetro `EmitDebugInformation`.<br /><br /> Para obtener más información, consulte [/debug (opciones del compilador de C#)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`DefineConstants`|Parámetro `String` opcional.<br /><br /> Define los símbolos de preprocesador. Para obtener más información, consulte [/define (Opciones del compilador de C#)](http://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e).|  
|`DelaySign`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, especifica que quiere un ensamblado completamente firmado. Si `false`, especifica que solo quiere colocar la clave pública en el ensamblado.<br /><br /> Este parámetro no tiene ningún efecto a menos que se utilice con el parámetro `KeyFile` o `KeyContainer`.<br /><br /> Para obtener más información, consulte [/delaysign (Opciones del compilador de C#)](http://msdn.microsoft.com/library/bcb058eb-2933-4e7f-b356-5c941db4de75).|  
|`DisabledWarnings`|Parámetro `String` opcional.<br /><br /> Especifica la lista de advertencias que se va a desactivar. Para obtener más información, consulte [/nowarn (Opciones del compilador de C#)](http://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4).|  
|`DocumentationFile`|Parámetro `String` opcional.<br /><br /> Procesa los comentarios de documentación generando un archivo XML. Para obtener más información, consulte [/doc (Opciones del compilador de C#)](http://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a).|  
|`EmitDebugInformation`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, la tarea genera información de depuración y la coloca en un archivo de base de datos del programa (.pdb). Si `false`, la tarea no emite ninguna información de depuración. El valor predeterminado es `false`. Para obtener más información, consulte [/debug (Opciones del compilador de C#)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`ErrorReport`|Parámetro `String` opcional.<br /><br /> Proporciona una forma cómoda para notificar un error interno de C# a Microsoft. Este parámetro puede tener un valor de `prompt`, `send` o `none`. Si el parámetro se establece en `prompt`, recibirá un mensaje cuando se produzca un error interno del compilador. El mensaje le permite enviar un informe de errores a Microsoft por vía electrónica. Si el parámetro se establece en `send`, se envía automáticamente un informe de errores. Si el parámetro se establece en `none`, el error solo se notifica en la salida de texto del compilador. El valor predeterminado es `none`. Para obtener más información, consulte [/errorreport (Opciones del compilador de C#)](http://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).|  
|`FileAlignment`|Parámetro `Int32` opcional.<br /><br /> Especifica el tamaño de las secciones del archivo de salida. Para obtener más información, consulte [/filealign (Opciones del compilador de C#)](http://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).|  
|`GenerateFullPaths`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, especifica la ruta de acceso absoluta al archivo en los resultados del compilador. Si `false`, especifica el nombre del archivo. El valor predeterminado es `false`. Para obtener más información, consulte [/fullpaths (Opciones del compilador de C#)](http://msdn.microsoft.com/library/d2a5f857-cbb2-430b-879c-d648aaf0b8c4).|  
|`KeyContainer`|Parámetro `String` opcional.<br /><br /> Especifica el nombre del contenedor de claves criptográficas. Para obtener más información, consulte [/keycontainer (Opciones del compilador de C#)](http://msdn.microsoft.com/library/b3982b6d-2382-4f7e-bebd-ce98eaa30763).|  
|`KeyFile`|Parámetro `String` opcional.<br /><br /> Especifica el nombre de archivo que contiene la clave criptográfica. Para obtener más información, consulte [/keyfile (Opciones del compilador de C#)](http://msdn.microsoft.com/library/0815f9de-ace4-4e98-b4c6-13c55dea40c2).|  
|`LangVersion`|Parámetro `String` opcional.<br /><br /> Especifica la versión del idioma que se va a usar. Para obtener más información, consulte [/langversion (Opciones del compilador de C#)](http://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).|  
|`LinkResources`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Crea un vínculo a un recurso [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] en el archivo de salida; el archivo de recursos no se coloca en el archivo de salida.<br /><br /> Los elementos que se pasan a este parámetro pueden tener entradas de metadatos opcionales denominadas `LogicalName` y `Access`. `LogicalName` corresponde al parámetro `identifier` del modificador `/linkresource` y `Access` corresponde al parámetro `accessibility-modifier`. Para obtener más información, consulte [/linkresource (Opciones del compilador de C#)](http://msdn.microsoft.com/library/440c26c2-77c1-4811-a0a3-57cce3f5fc96).|  
|`MainEntryPoint`|Parámetro `String` opcional.<br /><br /> Especifica la ubicación del método `Main`. Para obtener más información, consulte [/main (Opciones del compilador de C#)](http://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049).|  
|`ModuleAssemblyName`|Parámetro `String` opcional.<br /><br /> Especifica el nombre del ensamblado del que este módulo formará parte.|  
|`NoConfig`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, indica al compilador que no compile con el archivo csc.rsp. Para obtener más información, consulte [/noconfig (Opciones del compilador de C#)](http://msdn.microsoft.com/library/cd26967e-e494-4c8c-b5c9-af13b2f78b2e).|  
|`NoLogo`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, suprime la visualización de la información de encabezado del compilador. Para obtener más información, consulte [/nologo (Opciones del compilador de C#)](http://msdn.microsoft.com/library/426afb36-a8fb-469d-9c45-a35d9512557c).|  
|`NoStandardLib`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, impide la importación del archivo mscorlib.dll, que define el espacio de nombres System completo. Utilice este parámetro si quiere definir o crear sus propios objetos y su espacio de nombres System. Para obtener más información, consulte [/nostdlib (Opciones del compilador de C#)](http://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).|  
|`NoWin32Manifest`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, no incluya el manifiesto Win32 predeterminado.|  
|`Optimize`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, activa las optimizaciones. Si `false`, desactiva las optimizaciones. Para obtener más información, consulte [/optimize (Opciones del compilador de C#)](http://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0).|  
|`OutputAssembly`|Parámetro de salida `String` opcional.<br /><br /> Especifica el nombre del archivo de salida. Para obtener más información, consulte [/out (Opciones del compilador de C#)](http://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5).|  
|`PdbFile`|Parámetro `String` opcional.<br /><br /> Especifica el nombre del archivo de información de depuración. El nombre predeterminado es el nombre del archivo de salida con una extensión .pdb.|  
|`Platform`|Parámetro `String` opcional.<br /><br /> Especifica la plataforma del procesador que debe destinar el archivo de salida. Este parámetro puede tener un valor de `x86`, `x64` o `anycpu`. El valor predeterminado es `anycpu`. Para obtener más información, consulte [/platform (Opciones del compilador de C#)](http://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04).|  
|`References`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Hace que la tarea importe información de tipo pública de los elementos especificados en el proyecto actual. Para obtener más información, consulte [/reference (Opciones del compilador de C#)](http://msdn.microsoft.com/library/8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4).<br /><br /> Si quiere especificar un alias de referencia [!INCLUDE[csprcs](../includes/csprcs-md.md)] en un archivo [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], agregue los metadatos `Aliases` al elemento "Reference" original. Por ejemplo, para establecer el alias "LS1" en la siguiente línea de comandos CSC:<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> debe utilizar:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Inserta un recurso [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] en el archivo de salida.<br /><br /> Los elementos que se pasan a este parámetro pueden tener entradas de metadatos opcionales denominadas `LogicalName` y `Access`. `LogicalName` corresponde al parámetro `identifier` del modificador `/resource` y `Access` corresponde al parámetro `accessibility-modifier`. Para obtener más información, consulte [/resource (Opciones del compilador de C#)](http://msdn.microsoft.com/library/5212666e-98ab-47e4-a497-b5545ab15c7f).|  
|`ResponseFiles`|Parámetro `String` opcional.<br /><br /> Especifica el archivo de respuesta que contiene comandos para esta tarea. Para obtener más información, consulte [@ (especificar archivo de respuesta)](http://msdn.microsoft.com/library/dda4fa9f-a02c-400f-8b6a-d58834e13d7f).|  
|`Sources`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica uno o varios archivos de origen de [!INCLUDE[csprcs](../includes/csprcs-md.md)].|  
|`TargetType`|Parámetro `String` opcional.<br /><br /> Especifica el formato del archivo de salida. Este parámetro puede tener un valor de `library`, que crea una biblioteca de código, `exe`, que crea una aplicación de consola, `module`, que crea un módulo, o `winexe`, que crea un programa de Windows. El valor predeterminado es `library`. Para obtener más información, consulte [/target (Opciones del compilador de C#)](http://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f).|  
|`TreatWarningsAsErrors`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, trata todas las advertencias como errores. Para obtener más información, consulte [/warnaserror (Opciones del compilador de C#)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).|  
|`UseHostCompilerIfAvailable`|Parámetro `Boolean` opcional.<br /><br /> Indica a la tarea que utilice el objeto de compilador en proceso, si está disponible. Se utiliza únicamente por [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|`Utf8Output`|Parámetro `Boolean` opcional.<br /><br /> Registra los resultados del compilador mediante la codificación UTF-8. Para obtener más información, consulte [/utf8output (Opciones del compilador de C#)](http://msdn.microsoft.com/library/27ff7381-c281-45d7-b2eb-1ad644b1354e).|  
|`WarningLevel`|Parámetro `Int32` opcional.<br /><br /> Especifica el nivel de advertencia que debe mostrar el compilador. Para obtener más información, consulte [/warn (Opciones del compilador de C#)](http://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71).|  
|`WarningsAsErrors`|Parámetro `String` opcional.<br /><br /> Especifica una lista de advertencias que se tratarán como errores. Para obtener más información, consulte [/warnaserror (Opciones del compilador de C#)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Este parámetro invalida el parámetro `TreatWarningsAsErrors`.|  
|`WarningsNotAsErrors`|Parámetro `String` opcional.<br /><br /> Especifica una lista de advertencias que no se tratarán como errores. Para obtener más información, consulte [/warnaserror (Opciones del compilador de C#)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Este parámetro solo es útil si el parámetro `TreatWarningsAsErrors` está establecido en `true`.|  
|`Win32Icon`|Parámetro `String` opcional.<br /><br /> Inserta un archivo .ico en el ensamblado, lo que proporciona al archivo de salida la apariencia deseada en el Explorador de archivos. Para obtener más información, consulte [/win32icon (opciones del compilador de C#)](http://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138).|  
|`Win32Manifest`|Parámetro `String` opcional.<br /><br /> Especifica el manifiesto de Win32 que se incluirá.|  
|`Win32Resource`|Parámetro `String` opcional.<br /><br /> Inserta un archivo de recurso de Win32 (.res) en el archivo de salida. Para obtener más información, consulte [/win32res (Opciones del compilador de C#)](http://msdn.microsoft.com/library/3c33f750-6948-4c7e-a27e-bef98f77255b).|  
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase `Microsoft.Build.Tasks.ManagedCompiler`, que hereda de la clase <xref:Microsoft.Build.Tasks.ToolTaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.ToolTask>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [ToolTaskExtension (Clase base)](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se utiliza la tarea `Csc` para compilar un ejecutable de los archivos de origen en la colección de elementos `Compile`.  
  
```  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Tareas](../msbuild/msbuild-tasks.md)
