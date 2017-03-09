---
title: "Csc (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Csc"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Csc (tarea) [MSBuild]"
  - "MSBuild, Csc (tarea)"
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Csc (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contiene CSC.exe y genera archivos ejecutables (archivos .exe), bibliotecas de vínculos dinámicos (archivos .dll) o módulos de código (archivos .netmodule). Para obtener más información acerca de CSC.exe, vea [Opciones del compilador de C#](/dotnet/csharp/language-reference/compiler-options/index).  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `Csc`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Parámetro `String[]` opcional.<br /><br /> Especifica más directorios donde buscar referencias. Para obtener más información, consulte [/lib (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option).|  
|`AddModules`|Parámetro `String` opcional.<br /><br /> Especifica uno o varios módulos que formarán parte del ensamblado. Para obtener más información, consulte [/addmodule (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option).|  
|`AllowUnsafeBlocks`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, compila código que utiliza el [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) (palabra clave). Para obtener más información, consulte [/unsafe (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).|  
|`ApplicationConfiguration`|Parámetro `String` opcional.<br /><br /> Especifica el archivo de configuración de aplicación que contiene la configuración de enlace de ensamblado.|  
|`BaseAddress`|Parámetro `String` opcional.<br /><br /> Especifica la dirección base preferida para cargar una DLL. La dirección base predeterminada para un archivo DLL se establece el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] en tiempo de ejecución de lenguaje común. Para obtener más información, consulte [/baseaddress (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).|  
|`CheckForOverflowUnderflow`|Parámetro `Boolean` opcional.<br /><br /> Especifica si produce una excepción en tiempo de ejecución en aritmética de enteros que desborda los límites del tipo de datos. Para obtener más información, consulte [/Checked (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).|  
|`CodePage`|Parámetro `Int32` opcional.<br /><br /> Especifica la página de códigos que se va a usar para todos los archivos de código fuente de la compilación. Para obtener más información, consulte [/codepage (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option).|  
|`DebugType`|Parámetro `String` opcional.<br /><br /> Especifica el tipo de depuración. `DebugType` puede ser `full` o `pdbonly`. El valor predeterminado es `full`, que permite a un depurador adjuntarlo a un programa en ejecución. Especificar `pdbonly` permite depurar el código cuando el programa se inicia en el depurador, pero sólo mostrará el ensamblador cuando el programa que se ejecuta está asociado al depurador de origen.<br /><br /> Este parámetro reemplaza el `EmitDebugInformation` parámetro.<br /><br /> Para obtener más información, consulte [/debug (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).|  
|`DefineConstants`|Parámetro `String` opcional.<br /><br /> Define los símbolos de preprocesador. Para obtener más información, consulte [/define (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).|  
|`DelaySign`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, especifica que desea firmar completamente un ensamblado. Si `false`, especifica que sólo desea colocar la clave pública del ensamblado.<br /><br /> Este parámetro no tiene ningún efecto a menos que se usa con el `KeyFile` o `KeyContainer` parámetro.<br /><br /> Para obtener más información, consulte [/delaysign (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option).|  
|`DisabledWarnings`|Parámetro `String` opcional.<br /><br /> Especifica la lista de advertencias que se deshabilitará. Para obtener más información, consulte [/nowarn (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).|  
|`DocumentationFile`|Parámetro `String` opcional.<br /><br /> Procesa los comentarios de documentación generando un archivo XML. Para obtener más información, consulte [/doc (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).|  
|`EmitDebugInformation`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, la tarea genera información de depuración y la coloca en un archivo de programa (.pdb) de base de datos. Si `false`, la tarea no emite ninguna información de depuración. El valor predeterminado es `false`. Para obtener más información, consulte [/debug (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).|  
|`ErrorReport`|Parámetro `String` opcional.<br /><br /> Proporciona una forma cómoda para notificar un error interno de C# a Microsoft. Este parámetro puede tener un valor de `prompt`, `send`, o `none`. Si el parámetro se establece en `prompt`, recibirá un mensaje cuando se produce un error interno del compilador. El símbolo del sistema le permite enviar un informe de errores electrónicamente a Microsoft. Si el parámetro se establece en `send`, un informe de errores se envía automáticamente. Si el parámetro se establece en `none`, el error sólo se notifica en el texto de salida del compilador. El valor predeterminado es `none`. Para obtener más información, consulte [/errorreport (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).|  
|`FileAlignment`|Parámetro `Int32` opcional.<br /><br /> Especifica el tamaño de las secciones del archivo de salida. Para obtener más información, consulte [/filealign (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).|  
|`GenerateFullPaths`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, especifica la ruta de acceso absoluta al archivo en la salida del compilador. Si `false`, especifica el nombre del archivo. El valor predeterminado es `false`. Para obtener más información, consulte [/fullpaths (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option).|  
|`KeyContainer`|Parámetro `String` opcional.<br /><br /> Especifica el nombre del contenedor de claves criptográficas. Para obtener más información, consulte [/keycontainer (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option).|  
|`KeyFile`|Parámetro `String` opcional.<br /><br /> Especifica el nombre de archivo que contiene la clave criptográfica. Para obtener más información, consulte [/keyfile (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option).|  
|`LangVersion`|Parámetro `String` opcional.<br /><br /> Especifica la versión del idioma que se va a usar. Para obtener más información, consulte [/langversion (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).|  
|`LinkResources`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parámetro.<br /><br /> Crea un vínculo a un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] recursos en el archivo de salida; el archivo de recursos no se coloca en el archivo de salida.<br /><br /> Los elementos que se pasan a este parámetro pueden tener entradas opcionales de metadatos denominadas `LogicalName` y `Access`. `LogicalName` corresponde a la `identifier` parámetro de la `/linkresource` cambiar, y `Access` corresponde a `accessibility-modifier` parámetro. Para obtener más información, consulte [/linkresource (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option).|  
|`MainEntryPoint`|Parámetro `String` opcional.<br /><br /> Especifica la ubicación de la `Main` (método). Para obtener más información, consulte [/main (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option).|  
|`ModuleAssemblyName`|Parámetro `String` opcional.<br /><br /> Especifica el nombre del ensamblado que formará parte de este módulo.|  
|`NoConfig`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, le indica al compilador que no compile con el archivo csc.rsp. Para obtener más información, consulte [/noconfig (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option).|  
|`NoLogo`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, suprime la presentación de información de pancarta del compilador. Para obtener más información, consulte [/nologo (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option).|  
|`NoStandardLib`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, evita la importación de mscorlib.dll, que define el espacio de nombres de sistema completo. Utilice este parámetro si desea definir o crear sus propios objetos y espacio de nombres System. Para obtener más información, consulte [/nostdlib (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).|  
|`NoWin32Manifest`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, no incluya el manifiesto de Win32 predeterminado.|  
|`Optimize`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, habilita las optimizaciones. Si `false`, deshabilita las optimizaciones. Para obtener más información, consulte [/optimize (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).|  
|`OutputAssembly`|Parámetro de salida `String` opcional.<br /><br /> Especifica el nombre del archivo de salida. Para obtener más información, consulte [/out (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).|  
|`PdbFile`|Parámetro `String` opcional.<br /><br /> Especifica el nombre del archivo de información de depuración. El nombre predeterminado es el nombre del archivo de salida con una extensión .pdb.|  
|`Platform`|Parámetro `String` opcional.<br /><br /> Especifica la plataforma del procesador que debe destinar el archivo de salida. Este parámetro puede tener un valor de `x86`, `x64`, o `anycpu`. El valor predeterminado es `anycpu`. Para obtener más información, consulte [/platform (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).|  
|`References`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parámetro.<br /><br /> Hace que la tarea Importar información de tipo pública de los elementos especificados en el proyecto actual. Para obtener más información, consulte [/reference (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Puede especificar un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] alias de referencia un [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] archivo agregando los metadatos `Aliases` al elemento "Reference" original. Por ejemplo, para establecer el alias "LS1" en la línea de comandos CSC:<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> debe utilizar:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parámetro.<br /><br /> Incrusta un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] recursos en el archivo de salida.<br /><br /> Los elementos que se pasan a este parámetro pueden tener entradas opcionales de metadatos denominadas `LogicalName` y `Access`. `LogicalName` corresponde a la `identifier` parámetro de la `/resource` cambiar, y `Access` corresponde a `accessibility-modifier` parámetro. Para obtener más información, consulte [/resource (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option).|  
|`ResponseFiles`|Parámetro `String` opcional.<br /><br /> Especifica el archivo de respuesta que contiene comandos para esta tarea. Para obtener más información, consulte [@ (especificar archivo de respuesta)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option).|  
|`Sources`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parámetro.<br /><br /> Especifica uno o más [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] los archivos de origen.|  
|`TargetType`|Parámetro `String` opcional.<br /><br /> Especifica el formato del archivo de salida. Este parámetro puede tener un valor de `library`, que crea una biblioteca de código, `exe`, que crea una aplicación de consola, `module`, que crea un módulo, o `winexe`, que crea un programa de Windows. El valor predeterminado es `library`. Para obtener más información, consulte [/target (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).|  
|`TreatWarningsAsErrors`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, trata todas las advertencias como errores. Para obtener más información, consulte [/warnaserror (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).|  
|`UseHostCompilerIfAvailable`|Parámetro `Boolean` opcional.<br /><br /> Indica a la tarea para utilizar el objeto de compilador en proceso, si está disponible. Sólo utilizan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|`Utf8Output`|Parámetro `Boolean` opcional.<br /><br /> Registra los resultados del compilador utilizando la codificación UTF-8. Para obtener más información, consulte [/utf8output (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option).|  
|`WarningLevel`|Parámetro `Int32` opcional.<br /><br /> Especifica el nivel de advertencia para el compilador mostrar. Para obtener más información, consulte [/warn (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).|  
|`WarningsAsErrors`|Parámetro `String` opcional.<br /><br /> Especifica una lista de advertencias que se tratarán como errores. Para obtener más información, consulte [/warnaserror (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Este parámetro reemplaza el `TreatWarningsAsErrors` parámetro.|  
|`WarningsNotAsErrors`|Parámetro `String` opcional.<br /><br /> Especifica una lista de advertencias que no se tratarán como errores. Para obtener más información, consulte [/warnaserror (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Este parámetro sólo es útil si el `TreatWarningsAsErrors` parámetro está establecido en `true`.|  
|`Win32Icon`|Parámetro `String` opcional.<br /><br /> Inserta un archivo .ico en el ensamblado, lo que le proporciona la apariencia deseada en el Explorador de archivos. Para obtener más información, consulte [/win32icon (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option).|  
|`Win32Manifest`|Parámetro `String` opcional.<br /><br /> Especifica el manifiesto de Win32 que se incluirán.|  
|`Win32Resource`|Parámetro `String` opcional.<br /><br /> Inserta un archivo de recursos (. res) de Win32 en el archivo de salida. Para obtener más información, consulte [/win32res (opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option).|  
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la `Microsoft.Build.Tasks.ManagedCompiler` (clase), que se hereda de la <xref:Microsoft.Build.Tasks.ToolTaskExtension> (clase), que a su vez hereda de la <xref:Microsoft.Build.Utilities.ToolTask> clase. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [ToolTaskExtension (clase Base)](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se utiliza la `Csc` tarea para compilar un ejecutable de los archivos de origen en el `Compile` colección de elementos.  
  
```  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Tareas](../msbuild/msbuild-tasks.md)