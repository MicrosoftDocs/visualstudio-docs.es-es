---
title: Csc (tarea) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#Csc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Csc task [MSBuild]
- MSBuild, Csc task
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
caps.latest.revision: "26"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d0e0907e7127f83055bfafbcd4491576d94bc2c0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="csc-task"></a>Csc (Tarea)
Encapsula CSC.exe y genera archivos ejecutables (.exe), archivos de biblioteca de vínculos dinámicos (.dll) o archivos de módulos de códigos (.netmodule). Para obtener más información sobre CSC.exe, consulte [Opciones del compilador de C#](/dotnet/csharp/language-reference/compiler-options/index).  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `Csc` .  
  
|Parámetro|Description|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Parámetro `String[]` opcional.<br /><br /> Especifica más directorios donde buscar referencias. Para obtener más información, consulte [/lib (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option).|  
|`AddModules`|Parámetro `String` opcional.<br /><br /> Especifica uno o varios módulos que formarán parte del ensamblado. Para obtener más información, consulte [/addmodule (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option).|  
|`AllowUnsafeBlocks`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, compila el código que utiliza la palabra clave [unsafe](/dotnet/csharp/language-reference/keywords/unsafe). Para obtener más información, consulte [/unsafe (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).|  
|`ApplicationConfiguration`|Parámetro `String` opcional.<br /><br /> Especifique el archivo de configuración de la aplicación que contiene una configuración de enlace de ensamblados.|  
|`BaseAddress`|Parámetro `String` opcional.<br /><br /> Especifica la dirección base preferida para cargar una DLL. La dirección base predeterminada para un archivo DLL se establece mediante [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Common Language Runtime. Para obtener más información, consulte [/baseaddress (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).|  
|`CheckForOverflowUnderflow`|Parámetro `Boolean` opcional.<br /><br /> Especifica si la aritmética de enteros que desborda los límites del tipo de datos inicia una excepción en tiempo de ejecución. Para obtener más información, consulte [/checked (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).|  
|`CodePage`|Parámetro `Int32` opcional.<br /><br /> Especifica la página de códigos que se va a usar para todos los archivos de código fuente de la compilación. Para obtener más información, consulte [/codepage (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option).|  
|`DebugType`|Parámetro `String` opcional.<br /><br /> Especifica el tipo de depuración. `DebugType` puede ser `full` o `pdbonly`. El valor predeterminado es `full`, que permite a un depurador adjuntarlo a un programa en ejecución. Especificar `pdbonly` permite depurar el código fuente cuando el programa se inicia en el depurador, pero solo mostrará el ensamblador cuando el programa que se ejecuta está asociado al depurador.<br /><br /> Este parámetro invalida el parámetro `EmitDebugInformation`.<br /><br /> Para obtener más información, consulte [/debug (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).|  
|`DefineConstants`|Parámetro `String` opcional.<br /><br /> Define los símbolos de preprocesador. Para obtener más información, consulte [/define (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).|  
|`DelaySign`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, especifica que quiere un ensamblado completamente firmado. Si `false`, especifica que solo quiere colocar la clave pública en el ensamblado.<br /><br /> Este parámetro no tiene ningún efecto a menos que se utilice con el parámetro `KeyFile` o `KeyContainer`.<br /><br /> Para obtener más información, consulte [/delaysign (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option).|  
|`DisabledWarnings`|Parámetro `String` opcional.<br /><br /> Especifica la lista de advertencias que se va a desactivar. Para obtener más información, consulte [/nowarn (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).|  
|`DocumentationFile`|Parámetro `String` opcional.<br /><br /> Procesa los comentarios de documentación generando un archivo XML. Para obtener más información, consulte [/doc (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).|  
|`EmitDebugInformation`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, la tarea genera información de depuración y la coloca en un archivo de base de datos del programa (.pdb). Si `false`, la tarea no emite ninguna información de depuración. El valor predeterminado es `false`. Para obtener más información, consulte [/debug (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).|  
|`ErrorReport`|Parámetro `String` opcional.<br /><br /> Proporciona una forma cómoda para notificar un error interno de C# a Microsoft. Este parámetro puede tener un valor de `prompt`, `send` o `none`. Si el parámetro se establece en `prompt`, recibirá un mensaje cuando se produzca un error interno del compilador. El mensaje le permite enviar un informe de errores a Microsoft por vía electrónica. Si el parámetro se establece en `send`, se envía automáticamente un informe de errores. Si el parámetro se establece en `none`, el error solo se notifica en la salida de texto del compilador. El valor predeterminado es `none`. Para obtener más información, consulte [/errorreport (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).|  
|`FileAlignment`|Parámetro `Int32` opcional.<br /><br /> Especifica el tamaño de las secciones del archivo de salida. Para obtener más información, consulte [/filealign (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).|  
|`GenerateFullPaths`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, especifica la ruta de acceso absoluta al archivo en los resultados del compilador. Si `false`, especifica el nombre del archivo. El valor predeterminado es `false`. Para obtener más información, consulte [/fullpaths (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option).|  
|`KeyContainer`|Parámetro `String` opcional.<br /><br /> Especifica el nombre del contenedor de claves criptográficas. Para obtener más información, consulte [/keycontainer (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option).|  
|`KeyFile`|Parámetro `String` opcional.<br /><br /> Especifica el nombre de archivo que contiene la clave criptográfica. Para obtener más información, consulte [/keyfile (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option).|  
|`LangVersion`|Parámetro `String` opcional.<br /><br /> Especifica la versión del idioma que se va a usar. Para obtener más información, consulte [/langversion (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).|  
|`LinkResources`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Crea un vínculo a un recurso [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] en el archivo de salida; el archivo de recursos no se coloca en el archivo de salida.<br /><br /> Los elementos que se pasan a este parámetro pueden tener entradas de metadatos opcionales denominadas `LogicalName` y `Access`. `LogicalName` corresponde al parámetro `identifier` del modificador `/linkresource` y `Access` corresponde al parámetro `accessibility-modifier`. Para obtener más información, consulte [/linkresource (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option).|  
|`MainEntryPoint`|Parámetro `String` opcional.<br /><br /> Especifica la ubicación del método `Main`. Para obtener más información, consulte [/main (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option).|  
|`ModuleAssemblyName`|Parámetro `String` opcional.<br /><br /> Especifica el nombre del ensamblado del que este módulo formará parte.|  
|`NoConfig`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, indica al compilador que no compile con el archivo csc.rsp. Para obtener más información, consulte [/noconfig (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option).|  
|`NoLogo`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, suprime la visualización de la información de encabezado del compilador. Para obtener más información, consulte [/nologo (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option).|  
|`NoStandardLib`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, impide la importación del archivo mscorlib.dll, que define el espacio de nombres System completo. Utilice este parámetro si quiere definir o crear sus propios objetos y su espacio de nombres System. Para obtener más información, consulte [/nostdlib (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).|  
|`NoWin32Manifest`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, no incluya el manifiesto Win32 predeterminado.|  
|`Optimize`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, activa las optimizaciones. Si `false`, desactiva las optimizaciones. Para obtener más información, consulte [/optimize (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).|  
|`OutputAssembly`|Parámetro de salida `String` opcional.<br /><br /> Especifica el nombre del archivo de salida. Para obtener más información, consulte [/out (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).|  
|`OutputRefAssembly`|Parámetro `String` opcional.<br /><br /> Especifica el nombre del archivo de ensamblado de referencia de salida. Para más información, consulte [/refout (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option).|  
|`PdbFile`|Parámetro `String` opcional.<br /><br /> Especifica el nombre del archivo de información de depuración. El nombre predeterminado es el nombre del archivo de salida con una extensión .pdb.|  
|`Platform`|Parámetro `String` opcional.<br /><br /> Especifica la plataforma del procesador que debe destinar el archivo de salida. Este parámetro puede tener un valor de `x86`, `x64` o `anycpu`. El valor predeterminado es `anycpu`. Para obtener más información, consulte [/platform (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).|  
|`References`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Hace que la tarea importe información de tipo pública de los elementos especificados en el proyecto actual. Para obtener más información, consulte [/reference (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Si quiere especificar un alias de referencia [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] en un archivo [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], agregue los metadatos `Aliases` al elemento "Reference" original. Por ejemplo, para establecer el alias "LS1" en la siguiente línea de comandos CSC:<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> debe utilizar:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Inserta un recurso [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] en el archivo de salida.<br /><br /> Los elementos que se pasan a este parámetro pueden tener entradas de metadatos opcionales denominadas `LogicalName` y `Access`. `LogicalName` corresponde al parámetro `identifier` del modificador `/resource` y `Access` corresponde al parámetro `accessibility-modifier`. Para obtener más información, consulte [/resource (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option).|  
|`ResponseFiles`|Parámetro `String` opcional.<br /><br /> Especifica el archivo de respuesta que contiene comandos para esta tarea. Para obtener más información, consulte [@ (especificar archivo de respuesta)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option).|  
|`Sources`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica uno o varios archivos de origen de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].|  
|`TargetType`|Parámetro `String` opcional.<br /><br /> Especifica el formato del archivo de salida. Este parámetro puede tener un valor de `library`, que crea una biblioteca de código, `exe`, que crea una aplicación de consola, `module`, que crea un módulo, o `winexe`, que crea un programa de Windows. El valor predeterminado es `library`. Para obtener más información, consulte [/target (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).|  
|`TreatWarningsAsErrors`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, trata todas las advertencias como errores. Para obtener más información, consulte [/warnaserror (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).|  
|`UseHostCompilerIfAvailable`|Parámetro `Boolean` opcional.<br /><br /> Indica a la tarea que utilice el objeto de compilador en proceso, si está disponible. Se utiliza únicamente por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|`Utf8Output`|Parámetro `Boolean` opcional.<br /><br /> Registra los resultados del compilador mediante la codificación UTF-8. Para obtener más información, consulte [/utf8output (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option).|  
|`WarningLevel`|Parámetro `Int32` opcional.<br /><br /> Especifica el nivel de advertencia que debe mostrar el compilador. Para obtener más información, consulte [/warn (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).|  
|`WarningsAsErrors`|Parámetro `String` opcional.<br /><br /> Especifica una lista de advertencias que se tratarán como errores. Para obtener más información, consulte [/warnaserror (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Este parámetro invalida el parámetro `TreatWarningsAsErrors`.|  
|`WarningsNotAsErrors`|Parámetro `String` opcional.<br /><br /> Especifica una lista de advertencias que no se tratarán como errores. Para obtener más información, consulte [/warnaserror (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Este parámetro solo es útil si el parámetro `TreatWarningsAsErrors` está establecido en `true`.|  
|`Win32Icon`|Parámetro `String` opcional.<br /><br /> Inserta un archivo .ico en el ensamblado, lo que proporciona al archivo de salida la apariencia deseada en el Explorador de archivos. Para obtener más información, consulte [/win32icon (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option).|  
|`Win32Manifest`|Parámetro `String` opcional.<br /><br /> Especifica el manifiesto de Win32 que se incluirá.|  
|`Win32Resource`|Parámetro `String` opcional.<br /><br /> Inserta un archivo de recurso de Win32 (.res) en el archivo de salida. Para obtener más información, consulte [/win32res (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option).|  
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase `Microsoft.Build.Tasks.ManagedCompiler`, que hereda de la clase <xref:Microsoft.Build.Tasks.ToolTaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.ToolTask>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [ToolTaskExtension (Clase base)](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se utiliza la tarea `Csc` para compilar un ejecutable de los archivos de origen en la colección de elementos `Compile`.  
  
```xml  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Tareas](../msbuild/msbuild-tasks.md)
