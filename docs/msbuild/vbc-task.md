---
title: "Vbc (Tarea) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Vbc"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, Vbc (tarea)"
  - "Vbc (tarea) [MSBuild]"
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Vbc (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contiene vbc.exe, que genera archivos ejecutables \(.exe\), bibliotecas de vínculos dinámicos \(.dll\) o módulos de código \(.  netmodule\).  Para obtener más información sobre vbc.exe, consulte [Compilador de línea de comandos de Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index).  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `Vbc`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Parámetro `String[]` opcional.<br /><br /> Especifica carpetas adicionales en las que se han de buscar los ensamblados especificados en el atributo References.|  
|`AddModules`|Parámetro `String[]` opcional.<br /><br /> Hace que el compilador facilite la información de tipos presente en los archivos especificados al proyecto que se compila actualmente.  Este parámetro corresponde al modificador [\/addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) del compilador de vbc.exe.|  
|`BaseAddress`|Parámetro `String` opcional.<br /><br /> Especifica la dirección base del archivo DLL.  Este parámetro corresponde al modificador [\/baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) del compilador de vbc.exe.|  
|`CodePage`|Parámetro `Int32` opcional.<br /><br /> Especifica la página de códigos que se va a utilizar para todos los archivos de código fuente en la compilación.  Este parámetro corresponde al modificador [\/codepage](/dotnet/visual-basic/reference/command-line-compiler/codepage) del compilador de vbc.exe.|  
|`DebugType`|Parámetro `String[]` opcional.<br /><br /> Hace que el compilador genere información de depuración.  Este parámetro puede tener los valores siguientes:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> El valor predeterminado es `full`, que permite adjuntar un depurador al programa en ejecución.  Un valor de `pdbonly` permite depurar el código fuente cuando el programa se inicializa en el depurador, pero sólo mostrará el código de lenguaje de ensamblado cuando el programa que se ejecuta está asociado al depurador.  Para obtener más información, vea [\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|`DefineConstants`|Parámetro `String[]` opcional.<br /><br /> Permite definir constantes condicionales para el compilador.  Los pares símbolo\/valor van separados por punto y coma y se especifican con la siguiente sintaxis:<br /><br /> *símbolo1* `=` *valor1* `;` *símbolo2* `=` *valor2*<br /><br /> Este parámetro corresponde al modificador [\/define](/dotnet/visual-basic/reference/command-line-compiler/define) del compilador de vbc.exe.|  
|`DelaySign`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, la tarea coloca la clave pública en el ensamblado.  Si es `false`, la tarea firma totalmente el ensamblado.  El valor predeterminado es `false`. Este parámetro no tiene ningún efecto a menos que se utilice con el parámetro `KeyFile` o el parámetro `KeyContainer`.  Este parámetro corresponde al modificador [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) del compilador de vbc.exe.|  
|`DisabledWarnings`|Parámetro `String` opcional.<br /><br /> Suprime las advertencias especificadas.  Sólo hay que especificar la parte numérica del identificador de advertencia.  Las advertencias múltiples están separadas con punto y coma.  Este parámetro corresponde al modificador [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) del compilador de vbc.exe.|  
|`DocumentationFile`|Parámetro `String` opcional.<br /><br /> Procesa los comentarios de documentación en el archivo XML especificado.  Este parámetro reemplaza el atributo `GenerateDocumentation`.  Para obtener más información, vea [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).|  
|`EmitDebugInformation`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, la tarea genera información de depuración y la coloca en un archivo .pdb.  Para obtener más información, vea [\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|`ErrorReport`|Parámetro `String` opcional.<br /><br /> Especifica cómo la tarea debería documentar los errores internos del compilador.  Este parámetro puede tener los valores siguientes:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Si se especifica `prompt` y se produce un error interno del compilador, se mostrará un mensaje al usuario con la opción de enviar los datos de error a Microsoft.<br /><br /> Si se especifica `send` y se produce un error interno del compilador, la tarea envía los datos de error a Microsoft.<br /><br /> El valor predeterminado es `none`, que sólo muestra los errores en formato texto.<br /><br /> Este parámetro corresponde al modificador [\/errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) del compilador de vbc.exe.|  
|`FileAlignment`|Parámetro `Int32` opcional.<br /><br /> Especifica, en bytes, dónde alinear las secciones del archivo de salida.  Este parámetro puede tener los valores siguientes:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Este parámetro corresponde al modificador [\/filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) del compilador de vbc.exe.|  
|`GenerateDocumentation`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, genera información de documentación y la coloca en un archivo XML con el nombre del archivo ejecutable o biblioteca que está creando la tarea.  Para obtener más información, vea [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).|  
|`Imports`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Importa los espacios de nombres de las colecciones de elementos especificadas.  Este parámetro corresponde al modificador [\/imports](/dotnet/visual-basic/reference/command-line-compiler/imports) del compilador de vbc.exe.|  
|`KeyContainer`|Parámetro `String` opcional.<br /><br /> Especifica el nombre del contenedor de claves criptográficas.  Este parámetro corresponde al modificador [\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) del compilador de vbc.exe.|  
|`KeyFile`|Parámetro `String` opcional.<br /><br /> Especifica el nombre de archivo que contiene la clave criptográfica.  Para obtener más información, vea [\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile).|  
|`LangVersion`|Parámetro [String](assetId:///String?qualifyHint=False&autoUpgrade=True) opcional.<br /><br /> Especifica la versión del lenguaje, "9" o "10".|  
|`LinkResources`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Crea un vínculo con un archivo de recursos de .NET Framework en el archivo de salida, pero el archivo de recursos no se coloca en el archivo de salida.  Este parámetro corresponde al modificador [\/linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) del compilador de vbc.exe.|  
|`MainEntryPoint`|Parámetro `String` opcional.<br /><br /> Especifica la clase o el módulo que contiene el procedimiento `Sub Main`.  Este parámetro corresponde al modificador [\/main](/dotnet/visual-basic/reference/command-line-compiler/main) del compilador de vbc.exe.|  
|`ModuleAssemblyName`|Parámetro `String` opcional.<br /><br /> Especifica el ensamblado del que forma parte este módulo.|  
|`NoConfig`|Parámetro `Boolean` opcional.<br /><br /> Especifica que el compilador no debería utilizar el archivo vbc.rsp.  Este parámetro corresponde al modificador [\/noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) del compilador de vbc.exe.|  
|`NoLogo`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, suprime la presentación de información de titular del compilador.  Este parámetro corresponde al modificador [\/nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) del compilador de vbc.exe.|  
|`NoStandardLib`|Parámetro `Boolean` opcional.<br /><br /> Hace que el compilador no haga referencia a las bibliotecas estándar.  Este parámetro corresponde al modificador [\/nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) del compilador de vbc.exe.|  
|`NoVBRuntimeReference`|Parámetro `Boolean` opcional.<br /><br /> Solo para uso interno.  Si es true, impide la referencia automática a Microsoft.VisualBasic.dll.|  
|`NoWarnings`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, la tarea suprime todas las advertencias.  Para obtener más información, vea [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).|  
|`Optimize`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, habilita las optimizaciones del compilador.  Este parámetro corresponde al modificador [\/optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) del compilador de vbc.exe.|  
|`OptionCompare`|Parámetro `String` opcional.<br /><br /> Especifica la forma de realizar las comparaciones de cadenas.  Este parámetro puede tener los valores siguientes:<br /><br /> -   `binary`<br />-   `text`<br /><br /> El valor `binary` especifica que la tarea utiliza las comparaciones de cadenas binarias.  El valor `text` especifica que la tarea utiliza las comparaciones de cadenas de texto.  El valor predeterminado de este parámetro es `binary`.  Este parámetro corresponde al modificador [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) del compilador de vbc.exe.|  
|`OptionExplicit`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, se necesita la declaración explícita de variables.  Este parámetro corresponde al modificador [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) del compilador de vbc.exe.|  
|`OptionInfer`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, permite la inferencia de tipos de variables.|  
|`OptionStrict`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, la tarea fuerza la semántica de tipos estricta para que restrinja las conversiones de tipos implícitas.  Este parámetro corresponde al modificador [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) del compilador de vbc.exe.|  
|`OptionStrictType`|Parámetro `String` opcional.<br /><br /> Especifica que una semántica de tipos estricta genere una advertencia.  Actualmente, solo "personalizado" es compatible.  Este parámetro corresponde al modificador [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) del compilador de vbc.exe.|  
|`OutputAssembly`|Parámetro de salida `String` opcional.<br /><br /> Especifica el nombre del archivo de salida.  Este parámetro corresponde al modificador [\/out](/dotnet/visual-basic/reference/command-line-compiler/out) del compilador de vbc.exe.|  
|`Platform`|Parámetro `String` opcional.<br /><br /> Especifica la plataforma del procesador de destino del archivo de salida.  Este parámetro puede tener un valor de `x86`, `x64`, `Itanium` o `anycpu`.  El valor predeterminado es `anycpu`.  Este parámetro corresponde al modificador [\/platform](/dotnet/visual-basic/reference/command-line-compiler/platform) del compilador de vbc.exe.|  
|`References`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Hace que la tarea importe la información de tipo pública de los elementos especificados al proyecto actual.  Este parámetro corresponde al modificador [\/reference](/dotnet/visual-basic/reference/command-line-compiler/reference) del compilador de vbc.exe.|  
|`RemoveIntegerChecks`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, deshabilita las comprobaciones de errores del desbordamiento de enteros.  El valor predeterminado es `false`.  Este parámetro corresponde al modificador [\/removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) del compilador de vbc.exe.|  
|`Resources`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Incrusta un recurso de .NET Framework en el archivo de salida.  Este parámetro corresponde al modificador [\/resource](/dotnet/visual-basic/reference/command-line-compiler/resource) del compilador de vbc.exe.|  
|`ResponseFiles`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica el archivo de respuesta que contiene los comandos para esta tarea.  Este parámetro corresponde a la opción [@ \(especificar archivo de respuesta\)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) del compilador de vbc.exe.|  
|`RootNamespace`|Parámetro `String` opcional.<br /><br /> Especifica el espacio de nombres raíz para todas las declaraciones de tipos.  Este parámetro corresponde al modificador [\/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) del compilador de vbc.exe.|  
|`SdkPath`|Parámetro `String` opcional.<br /><br /> Especifica la ubicación de mscorlib.dll y microsoft.visualbasic.dll.  Este parámetro corresponde al modificador [\/sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) del compilador de vbc.exe.|  
|`Sources`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica uno o varios archivos de origen de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].|  
|`TargetCompactFramework`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, la tarea tiene como destino [!INCLUDE[Compact](../extensibility/includes/compact_md.md)].  Este modificador corresponde al modificador [\/netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) del compilador de vbc.exe.|  
|`TargetType`|Parámetro `String` opcional.<br /><br /> Especifica el formato del archivo de salida.  Este parámetro puede tener un valor de `library`, que crea una biblioteca de códigos, `exe`, que crea una aplicación de consola, `module`, que crea un módulo, o `winexe`, que crea un programa de Windows.  El valor predeterminado es `library`.  Este parámetro corresponde al modificador [\/target](/dotnet/visual-basic/reference/command-line-compiler/target) del compilador de vbc.exe.|  
|`Timeout`|Parámetro `Int32` opcional.<br /><br /> Especifica el tiempo, en milisegundos, tras el cual se termina la tarea ejecutable.  El valor predeterminado es `Int.MaxValue`; es decir, no existe tiempo de espera.|  
|`ToolPath`|Parámetro `String` opcional.<br /><br /> Especifica la ubicación desde donde la tarea cargará el archivo ejecutable subyacente \(vbc.exe\).  Si no se especifica este parámetro, la tarea utiliza la ruta de acceso de instalación de SDK correspondiente a la versión de Framework que está ejecutando [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|`TreatWarningsAsErrors`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, todas las advertencias se tratan como errores.  Para obtener más información, vea [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).|  
|`UseHostCompilerIfAvailable`|Parámetro `Boolean` opcional.<br /><br /> Indica a la tarea que utilice el objeto de compilador en proceso, si está disponible.  Esta propiedad se utiliza únicamente en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|`Utf8Output`|Parámetro `Boolean` opcional.<br /><br /> Registra los resultados del compilador mediante la codificación UTF\-8.  Este parámetro corresponde al modificador [\/utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) del compilador de vbc.exe.|  
|`Verbosity`|Parámetro `String` opcional.<br /><br /> Especifica el contenido de los resultados del compilador.  Los valores del contenido pueden ser `Quiet`, `Normal` \(valor predeterminado\), o `Verbose`.|  
|`WarningsAsErrors`|Parámetro `String` opcional.<br /><br /> Especifica una lista de advertencias que se tratarán como errores.  Para obtener más información, vea [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Este parámetro reemplaza el parámetro `TreatWarningsAsErrors`.|  
|`WarningsNotAsErrors`|Parámetro `String` opcional.<br /><br /> Especifica una lista de advertencias que no se tratarán como errores.  Para obtener más información, vea [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Este parámetro sólo resulta útil si el parámetro `TreatWarningsAsErrors` se establece en `true`.|  
|`Win32Icon`|Parámetro `String` opcional.<br /><br /> Inserta un archivo .ico en el ensamblado, que proporciona al archivo de salida la apariencia deseada en el Explorador de archivos.  Este parámetro corresponde al modificador [\/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) del compilador de vbc.exe.|  
|`Win32Resources`|Parámetro `String` opcional.<br /><br /> Inserta un recurso de Win32 archivo \(.res\) en el archivo de salida.  Este parámetro corresponde al modificador [\/win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) del compilador de vbc.exe.|  
  
## Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.ToolTaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.ToolTask>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [ToolTaskExtension \(Clase base\)](../msbuild/tooltaskextension-base-class.md).  
  
## Ejemplo  
 En el siguiente ejemplo se compila un proyecto de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## Vea también  
 [Compilador de línea de comandos de Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)