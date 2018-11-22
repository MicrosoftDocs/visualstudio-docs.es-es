---
title: Vbc (tarea) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Vbc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Vbc task [MSBuild]
- MSBuild, Vbc task
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ed9563f4149b550e123cf74a09f19245514fe97
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281867"
---
# <a name="vbc-task"></a>Vbc (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Incluye vbc.exe, que genera ejecutables (.exe), archivos de biblioteca de vínculos dinámicos (.dll) o módulos de códigos (.netmodule). Para obtener más información sobre vbc.exe, vea [Compilador de línea de comandos de Visual Basic](http://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c).  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `Vbc` .  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Parámetro `String[]` opcional.<br /><br /> Especifica carpetas adicionales en las que buscar ensamblados especificados en el atributo References.|  
|`AddModules`|Parámetro `String[]` opcional.<br /><br /> Hace que el compilador facilite al proyecto que se está compilando toda la información de tipos presente en los archivos especificados. Este parámetro corresponde al modificador [/addmodule](http://msdn.microsoft.com/library/fb4b89d4-4926-4f20-868d-427fa28497b2) del compilador de vbc.exe.|  
|`BaseAddress`|Parámetro `String` opcional.<br /><br /> Especifica la dirección base del archivo DLL. Este parámetro corresponde al modificador [/baseaddress](http://msdn.microsoft.com/library/c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47) del compilador de vbc.exe.|  
|`CodePage`|Parámetro `Int32` opcional.<br /><br /> Especifica la página de códigos que se va a usar para todos los archivos de código fuente de la compilación. Este parámetro corresponde al modificador [/codepage](http://msdn.microsoft.com/library/be36ec33-6800-4505-838c-4124564f5cc9) del compilador de vbc.exe.|  
|`DebugType`|Parámetro `String[]` opcional.<br /><br /> Hace que el compilador genere información de depuración. Este parámetro puede tener los valores siguientes:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> El valor predeterminado es `full`, que permite asociar un depurador al programa en ejecución. Un valor de `pdbonly` permite la depuración de código fuente cuando el programa se inicia en el depurador, pero muestra código de lenguaje ensamblador solo cuando el programa en ejecución está asociado al depurador. Para obtener más información, vea [/debug (Visual Basic)](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`DefineConstants`|Parámetro `String[]` opcional.<br /><br /> Permite definir constantes condicionales para el compilador. Los pares símbolo-valor van separados por punto y coma, y se especifican con la siguiente sintaxis:<br /><br /> *symbol1* `=` *value1* `;` *symbol2* `=` *value2*<br /><br /> Este parámetro corresponde al modificador [/define](http://msdn.microsoft.com/library/f735c57d-1cf9-4f2f-a26f-0de630fd4077) del compilador de vbc.exe.|  
|`DelaySign`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, la tarea coloca la clave pública en el ensamblado. Si es `false`, la tarea firma completamente el ensamblado. El valor predeterminado es `false`. Este parámetro no tiene ningún efecto a no ser que se use con el parámetro `KeyFile` o el parámetro `KeyContainer`. Este parámetro corresponde al modificador [/delaysign](http://msdn.microsoft.com/library/c76e61a4-1884-4252-9fb2-377f99caa690) del compilador de vbc.exe.|  
|`DisabledWarnings`|Parámetro `String` opcional.<br /><br /> Suprime las advertencias especificadas. Solo necesita especificar la parte numérica del identificador de advertencia. Las advertencias múltiples se separan con punto y coma. Este parámetro corresponde al modificador [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) del compilador de vbc.exe.|  
|`DocumentationFile`|Parámetro `String` opcional.<br /><br /> Procesa los comentarios de documentación en el archivo XML especificado. Este parámetro invalida el atributo `GenerateDocumentation`. Para obtener más información, vea [/doc](http://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`EmitDebugInformation`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, la tarea genera información de depuración y la coloca en un archivo .pdb. Para obtener más información, vea [/debug (Visual Basic)](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`ErrorReport`|Parámetro `String` opcional.<br /><br /> Especifica cómo debe documentar la tarea los errores internos del compilador. Este parámetro puede tener los valores siguientes:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Si `prompt` está especificado y se produce un error del compilador interno, le aparece una opción al usuario sobre si enviar los datos de error a Microsoft.<br /><br /> Si `send` está especificado y se produce un error del compilador interno, la tarea envía los datos de error a Microsoft.<br /><br /> El valor predeterminado es `none`, que notifica errores solo en la salida de texto.<br /><br /> Este parámetro corresponde al modificador [/errorreport](http://msdn.microsoft.com/library/a7fe83a2-a6d8-460c-8dad-79a8f433f501) del compilador de vbc.exe.|  
|`FileAlignment`|Parámetro `Int32` opcional.<br /><br /> Especifica, en bytes, dónde se alinean las secciones del archivo de salida. Este parámetro puede tener los valores siguientes:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Este parámetro corresponde al modificador [/filealign](http://msdn.microsoft.com/library/cc61ec3d-ad38-4b28-9659-099d73cad099) del compilador de vbc.exe.|  
|`GenerateDocumentation`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, genera información de documentación y la coloca en un archivo XML con el nombre del archivo ejecutable o la biblioteca que está creando la tarea. Para obtener más información, vea [/doc](http://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`Imports`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Importa espacios de nombres de las colecciones de elementos especificadas. Este parámetro corresponde al modificador [/imports](http://msdn.microsoft.com/library/9a93fb53-c080-497b-bf9b-441022dbbc39) del compilador de vbc.exe.|  
|`KeyContainer`|Parámetro `String` opcional.<br /><br /> Especifica el nombre del contenedor de claves criptográficas. Este parámetro corresponde al modificador [/keycontainer](http://msdn.microsoft.com/library/6a9bc861-1752-4db1-9f64-b5252f0482cc) del compilador de vbc.exe.|  
|`KeyFile`|Parámetro `String` opcional.<br /><br /> Especifica el nombre de archivo que contiene la clave criptográfica. Para obtener más información, vea [/keyfile](http://msdn.microsoft.com/library/ffa82a4b-517a-4c6c-9889-5bae7b534bb8).|  
|`LangVersion`|Opcional [String] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) parámetro.<br /><br /> Especifica la versión del idioma, "9" o "10".|  
|`LinkResources`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Crea un vínculo a un recurso de .NET Framework en el archivo de salida; el archivo de recursos no se coloca en el archivo de salida. Este parámetro corresponde al modificador [/linkresource](http://msdn.microsoft.com/library/cf4dcad8-17b7-404c-9184-29358aa05b15) del compilador de vbc.exe.|  
|`MainEntryPoint`|Parámetro `String` opcional.<br /><br /> Especifica la clase o el módulo que contiene el procedimiento `Sub Main`. Este parámetro corresponde al modificador [/main](http://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0) del compilador de vbc.exe.|  
|`ModuleAssemblyName`|Parámetro `String` opcional.<br /><br /> Especifica el ensamblado del que este módulo forma parte.|  
|`NoConfig`|Parámetro `Boolean` opcional.<br /><br /> Especifica que el compilador no debe usar el archivo vbc.rsp. Este parámetro corresponde al parámetro [/noconfig](http://msdn.microsoft.com/library/a7405067-bd21-4171-adf4-a126fa3ad6c3) del compilador de vbc.exe.|  
|`NoLogo`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, suprime la visualización de la información de encabezado del compilador. Este parámetro corresponde al modificador [/nologo](http://msdn.microsoft.com/library/25ef54b6-d676-4639-a2d2-a747a158bc07) del compilador de vbc.exe.|  
|`NoStandardLib`|Parámetro `Boolean` opcional.<br /><br /> Hace que el compilador no haga referencia a las bibliotecas estándar. Este parámetro corresponde al modificador [/nostdlib](http://msdn.microsoft.com/library/140381b8-dc96-4ad5-ae11-792c9ed0be4d) del compilador de vbc.exe.|  
|`NoVBRuntimeReference`|Parámetro `Boolean` opcional.<br /><br /> Solo para uso interno. Si es True, evita la referencia automática en Microsoft.VisualBasic.dll.|  
|`NoWarnings`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, la tarea suprime todas las advertencias. Para obtener más información, vea [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).|  
|`Optimize`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, permite las optimizaciones del compilador. Este parámetro corresponde al modificador [/optimize](http://msdn.microsoft.com/library/fcba4a97-3622-4b87-a891-0f77deab4998) del compilador de vbc.exe.|  
|`OptionCompare`|Parámetro `String` opcional.<br /><br /> Especifica la forma en que se realizan las comparaciones de cadenas. Este parámetro puede tener los valores siguientes:<br /><br /> -   `binary`<br />-   `text`<br /><br /> El valor `binary` especifica que la tarea usa comparaciones de cadenas binarias. El valor `text` especifica que la tarea usa comparaciones de cadenas de texto. El valor predeterminado de este parámetro es `binary`. Este parámetro corresponde al modificador [/optioncompare](http://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4) del compilador de vbc.exe.|  
|`OptionExplicit`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, se requiere la declaración explícita de variables. Este parámetro corresponde al modificador [/optionexplicit](http://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7) del compilador de vbc.exe.|  
|`OptionInfer`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, permite la inferencia de tipos de variables.|  
|`OptionStrict`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, la tarea exige la semántica estricta de tipos para restringir las conversiones implícitas de tipos. Este parámetro corresponde al modificador [/optionstrict](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) del compilador de vbc.exe.|  
|`OptionStrictType`|Parámetro `String` opcional.<br /><br /> Especifica qué semántica estricta de tipos genera una advertencia. Actualmente, solo se admite "custom". Este parámetro corresponde al modificador [/optionstrict](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) del compilador de vbc.exe.|  
|`OutputAssembly`|Parámetro de salida `String` opcional.<br /><br /> Especifica el nombre del archivo de salida. Este parámetro corresponde al modificador [/out](http://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae) del compilador de vbc.exe.|  
|`Platform`|Parámetro `String` opcional.<br /><br /> Especifica la plataforma del procesador que debe destinar el archivo de salida. Este parámetro puede tener un valor de `x86`, `x64`, `Itanium` o `anycpu`. El valor predeterminado es `anycpu`. Este parámetro corresponde al modificador [/platform](http://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1) del compilador de vbc.exe.|  
|`References`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Hace que la tarea importe información de tipo pública de los elementos especificados en el proyecto actual. Este parámetro corresponde al modificador [/reference](http://msdn.microsoft.com/library/66bdfced-bbf6-43d1-a554-bc0990315737) del compilador de vbc.exe.|  
|`RemoveIntegerChecks`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, deshabilita las comprobaciones de errores de desbordamiento de enteros. El valor predeterminado es `false`. Este parámetro corresponde al modificador [/removeintchecks](http://msdn.microsoft.com/library/c1835bd5-1e38-4fba-bd2f-6984774765d4) del compilador de vbc.exe.|  
|`Resources`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Incrusta un recurso de .NET Framework en el archivo de salida. Este parámetro corresponde al modificador [/resource](http://msdn.microsoft.com/library/eee2f227-91f2-4f2b-a9d6-1c51c5320858) del compilador de vbc.exe.|  
|`ResponseFiles`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica el archivo de respuesta que contiene comandos para esta tarea. Este parámetro corresponde a la opción [@ (Especificar archivo de respuesta)](http://msdn.microsoft.com/library/a6847eaa-e5f9-4303-9421-45b55484b9ca) del compilador de vbc.exe.|  
|`RootNamespace`|Parámetro `String` opcional.<br /><br /> Especifica el espacio de nombres de la raíz para todas las declaraciones de tipos. Este parámetro corresponde al modificador [/rootnamespace](http://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783) del compilador de vbc.exe.|  
|`SdkPath`|Parámetro `String` opcional.<br /><br /> Especifica la ubicación de mscorlib.dll y microsoft.visualbasic.dll. Este parámetro corresponde al modificador [/sdkpath](http://msdn.microsoft.com/library/fec8a3f1-b791-4a37-8af7-344859f8212d) del compilador de vbc.exe.|  
|`Sources`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica uno o varios archivos de origen de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].|  
|`TargetCompactFramework`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, la tarea toma como destino [!INCLUDE[Compact](../includes/compact-md.md)]. Este modificador corresponde al modificador [/netcf](http://msdn.microsoft.com/library/db7cfa59-c315-401c-a59b-0daf355343d6) del compilador de vbc.exe.|  
|`TargetType`|Parámetro `String` opcional.<br /><br /> Especifica el formato del archivo de salida. Este parámetro puede tener un valor de `library`, que crea una biblioteca de código, `exe`, que crea una aplicación de consola, `module`, que crea un módulo, o `winexe`, que crea un programa de Windows. El valor predeterminado es `library`. Este parámetro corresponde al modificador [/target](http://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c) del compilador de vbc.exe.|  
|`Timeout`|Parámetro `Int32` opcional.<br /><br /> Especifica el tiempo en milisegundos después del cual se termina la tarea ejecutable. El valor predeterminado es `Int.MaxValue`, que indica que no hay período de tiempo de espera.|  
|`ToolPath`|Parámetro `String` opcional.<br /><br /> Especifica la ubicación desde donde la tarea cargará el archivo ejecutable subyacente (vbc.exe). Si no se especifica este parámetro, la tarea usa la ruta de instalación del SDK que se corresponde con la versión de la plataforma que está ejecutando [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
|`TreatWarningsAsErrors`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, todas las advertencias se tratan como errores. Para obtener más información, vea [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).|  
|`UseHostCompilerIfAvailable`|Parámetro `Boolean` opcional.<br /><br /> Indica a la tarea que utilice el objeto de compilador en proceso, si está disponible. Se utiliza únicamente por [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|`Utf8Output`|Parámetro `Boolean` opcional.<br /><br /> Registra los resultados del compilador mediante la codificación UTF-8. Este parámetro corresponde al modificador [/utf8output](http://msdn.microsoft.com/library/8ab36b1e-027a-49ac-85b4-f48997d9e4d6) del compilador de vbc.exe.|  
|`Verbosity`|Parámetro `String` opcional.<br /><br /> Especifica el nivel de detalle de los resultados del compilador. El nivel de detalle puede ser `Quiet`, `Normal` (el valor predeterminado) o `Verbose`.|  
|`WarningsAsErrors`|Parámetro `String` opcional.<br /><br /> Especifica una lista de advertencias que se tratarán como errores. Para obtener más información, vea [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Este parámetro invalida el parámetro `TreatWarningsAsErrors`.|  
|`WarningsNotAsErrors`|Parámetro `String` opcional.<br /><br /> Especifica una lista de advertencias que no se tratarán como errores. Para obtener más información, vea [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Este parámetro solo es útil si el parámetro `TreatWarningsAsErrors` está establecido en `true`.|  
|`Win32Icon`|Parámetro `String` opcional.<br /><br /> Inserta un archivo .ico en el ensamblado, lo que proporciona al archivo de salida la apariencia deseada en el Explorador de archivos. Este parámetro corresponde al modificador [/win32icon](http://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) del compilador de vbc.exe.|  
|`Win32Resources`|Parámetro `String` opcional.<br /><br /> Inserta un archivo de recurso de Win32 (.res) en el archivo de salida. Este parámetro corresponde al modificador [/win32resource](http://msdn.microsoft.com/library/e226946d-19ce-4cc9-91f5-aed24f77aa2b) del compilador de vbc.exe.|  
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.ToolTaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.ToolTask>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [ToolTaskExtension (Clase base)](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se compila un proyecto [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## <a name="see-also"></a>Vea también  
 [Compilador de línea de comandos de Visual Basic](http://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)   
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)



