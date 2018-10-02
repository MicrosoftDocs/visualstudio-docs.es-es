---
title: CL (tarea) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
- vc.task.cl
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (Visual C++), CL task
- CL task (MSBuild (Visual C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e10c5d6ed0e4b992f5b573cd46bd1248d8d24d90
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "47592821"
---
# <a name="cl-task"></a>CL (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CL (tarea)](https://docs.microsoft.com/visualstudio/msbuild/cl-task).  
  
  
Incluye la herramienta compilador de Visual C++, cl.exe. El compilador genera archivos ejecutables (.exe), archivos de biblioteca de vínculos dinámicos (.dll) o archivos de módulos de códigos (.netmodule). Para obtener más información, consulte [Opciones del compilador](http://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c).  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea **CL**. La mayoría de los parámetros de tarea, así como algunos conjuntos de parámetros, corresponden a una opción de línea de comandos.  
  
-   **AdditionalIncludeDirectories**  
  
     Parámetro String[] opcional.  
  
     Agrega un directorio a la lista de directorios en que se buscan archivos de inclusión.  
  
     Para obtener más información, consulte [/I (Directorios de inclusión adicionales)](http://msdn.microsoft.com/library/3e9add2a-5ed8-4d15-ad79-5b411e313a49).  
  
-   **AdditionalOptions**  
  
     Parámetro String opcional.  
  
     Una lista de opciones de la línea de comandos. Por ejemplo, "/*option1* /*option2* /*option#*". Utilice este parámetro para especificar opciones de la línea de comandos que no están representadas por ningún otro parámetro de tarea.  
  
     Para obtener más información, consulte [Opciones del compilador](http://msdn.microsoft.com/library/ed3376c8-bef4-4c9a-80e9-3b5da232644c).  
  
-   **AdditionalUsingDirectories**Parámetro String[] opcional.  
  
     Especifica un directorio en que el compilador debe buscar para resolver las referencias de archivos que se pasan a la directiva **#using**.  
  
     Para obtener más información, consulte [/AI (Especificar directorios de metadatos)](http://msdn.microsoft.com/library/fb9c1846-504c-4a3b-bb39-c8696de32f6f).  
  
-   **AlwaysAppend**  
  
     Parámetro String opcional.  
  
     Una cadena que siempre se emite en la línea de comandos. Su valor predeterminado es "**/c**".  
  
-   **AssemblerListingLocation**  
  
     Crea un archivo de lista que contiene el código de ensamblado.  
  
     Para obtener más información, consulte la opción **/Fa** en [/FA, /Fa (Archivo de lista)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
-   **AssemblerOutput**  
  
     Parámetro String opcional.  
  
     Crea un archivo de lista que contiene el código de ensamblado.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **NoListing** - *\<none>*  
  
    -   **AssemblyCode** - **/FA**  
  
    -   **AssemblyAndMachineCode** - **/FAc**  
  
    -   **AssemblyAndMachineCode** - **/FAc**  
  
    -   **All** - **/FAcs**  
  
     Para obtener más información, consulte las opciones **/FA**, **/FAc**, **/FAs** y **/FAcs** en [/FA, /Fa (Archivo de lista)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
-   **BasicRuntimeChecks**  
  
     Parámetro String opcional.  
  
     Activa y desactiva la característica de comprobación de errores en tiempo de ejecución, junto con el pragma [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b).  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **Default** -                          *\<none>*  
  
    -   **StackFrameRuntimeCheck** -  **/RTCs**  
  
    -   **UninitializedLocalUsageCheck** - **/RTCu**  
  
    -   **EnableFastChecks** -                          **/RTC1**  
  
     Para obtener más información, consulte [/RTC (Comprobaciones de errores de tiempo de ejecución)](http://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368).  
  
-   **BrowseInformation**  
  
     Parámetro booleano opcional.  
  
     Si `true`, crea un archivo de información de examen.  
  
     Para obtener más información, consulte la opción **/FR** en [/FR, /Fr (Crear archivo .Sbr)](http://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896).  
  
-   **BrowseInformationFile**  
  
     Parámetro String opcional.  
  
     Especifica un nombre de archivo para el archivo de información de examen.  
  
     Para obtener más información, consulte el parámetro **BrowseInformation** en esta tabla y también [/FR, /Fr (Crear archivo .Sbr)](http://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896).  
  
-   **BufferSecurityCheck**  
  
     Parámetro booleano opcional.  
  
     Si `true`, detecta algunas saturaciones de búfer que sobrescriben la dirección de retorno, una técnica común para aprovechar código que no impone restricciones de tamaño de búfer.  
  
     Para obtener más información, consulte [/GS (Comprobación de seguridad del búfer)](http://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e).  
  
-   **BuildingInIDE**  
  
     Parámetro booleano opcional.  
  
     Si `true`, indica que el IDE invoca **MSBuild**. De lo contrario, **MSBuild** se invoca en la línea de comandos.  
  
-   **CallingConvention**  
  
     Parámetro String opcional.  
  
     Especifica la convención de llamada, que determina el orden en que los argumentos de función se insertan en la pila, si la función de llamador o de llamada quita los argumentos de la pila al final de la llamada y la convención de decoración de nombres que el compilador utiliza para identificar funciones individuales.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **Cdecl** - **/Gd**  
  
    -   **FastCall** -                          **/Gr**  
  
    -   **StdCall** -                          **/Gz**  
  
     Para obtener más información, consulte [/Gd, /Gr, /Gv, /Gz (Convención de llamada)](http://msdn.microsoft.com/library/fd3110cb-2d77-49f2-99cf-a03f9ead00a3).  
  
-   **CompileAs**  
  
     Parámetro String opcional.  
  
     Especifica si se debe compilar el archivo de entrada como un archivo de código fuente de C o C++.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **Default** - *\<none>*  
  
    -   **CompileAsC** - **/TC**  
  
    -   **CompileAsCpp** - **/TP**  
  
     Para obtener más información, consulte [/Tc, /Tp, /TC, /TP (Especificar el tipo del archivo de origen)](http://msdn.microsoft.com/library/7d9d0a65-338b-427c-8b48-fff30e2f9d2b).  
  
-   **CompileAsManaged**  
  
     Parámetro String opcional.  
  
     Permite que las aplicaciones y los componentes usen las características de Common Language Runtime (CLR).  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **false** - *\<none>*  
  
    -   **true** - **/clr**  
  
    -   **Pure** - **/clr:pure**  
  
    -   **Safe** - **/clr:safe**  
  
    -   **OldSyntax** -   **/CLR: oldSyntax**  
  
     Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](http://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).  
  
-   **CreateHotpatchableImage**  
  
     Parámetro booleano opcional.  
  
     Si `true`, indica al compilador que prepare una imagen para *aplicar una revisión reciente*. Este parámetro garantiza que la primera instrucción de cada función sea de dos bytes, lo cual es necesario para aplicar una revisión reciente.  
  
     Para obtener más información, consulte [/hotpatch (Crear una imagen a la que se puede aplicar una revisión reciente)](http://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798).  
  
-   **DebugInformationFormat**  
  
     Parámetro String opcional.  
  
     Seleccione el tipo de información de depuración que se crea para el programa y si esta información se conserva en archivos objeto (.obj) o en una base de datos de programa (PDB).  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **OldStyle** - **/Z7**  
  
    -   **ProgramDatabase** -   **/Zi**  
  
    -   **EditAndContinue** -   **/Zi**  
  
     Para obtener más información, consulte [/Z7, /Zi, /ZI (Formato de la información de depuración)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).  
  
-   **DisableLanguageExtensions**  
  
     Parámetro booleano opcional.  
  
     Si **true**, indica al compilador que emita un error para las construcciones de lenguaje que no son compatibles con ANSI C o ANSI C++.  
  
     Para obtener más información, consulte la opción **/Za** en [/Za, /Ze (Desactivar extensiones de lenguaje)](http://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2).  
  
-   **DisableSpecificWarnings**  
  
     Parámetro String[] opcional.  
  
     Desactiva los números de advertencia que se especifican en una lista delimitada por punto y coma.  
  
     Para obtener más información, consulte la opción `/wd` en [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Nivel de advertencia)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
-   **EnableEnhancedInstructionSet**  
  
     Parámetro String opcional.  
  
     Especifica la arquitectura para la generación de código que utiliza las instrucciones de las extensiones SIMD de streaming (SSE) y las extensiones SIMD de streaming 2 (SSE2).  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **StreamingSIMDExtensions** - **/arch:SSE**  
  
    -   **StreamingSIMDExtensions2** - **/arch:SSE2**  
  
     Para obtener más información, consulte [/arch (x86)](http://msdn.microsoft.com/library/9dd5a75d-06e4-4674-aade-33228486078d).  
  
-   **EnableFiberSafeOptimizations**  
  
     Parámetro booleano opcional.  
  
     Si `true`, admite la seguridad de fibras para los datos asignados mediante almacenamiento local de subprocesos estáticos, es decir, los datos asignados mediante `__declspec(thread)`.  
  
     Para obtener más información, consulte [/GT (Admitir el almacenamiento local de subprocesos seguros para fibra)](http://msdn.microsoft.com/library/071fec79-c701-432b-9970-457344133159).  
  
-   **EnablePREfast**  
  
     Parámetro booleano opcional.  
  
     Si `true`, habilita el análisis de código.  
  
     Para obtener más información, consulte [/analize (Análisis de código)](http://msdn.microsoft.com/library/81da536a-e030-4bd4-be18-383927597d08).  
  
-   **ErrorReporting**  
  
     Parámetro String opcional.  
  
     Permite proporcionar directamente a Microsoft información sobre los errores internos del compilador (ICE). De forma predeterminada, la configuración de compilaciones del IDE es **Prompt** y la configuración en las compilaciones de la línea de comandos es **Queue**.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **None** - **/errorReport:none**  
  
    -   **Prompt** - **/errorReport:prompt**  
  
    -   **Queue** - **/errorReport:queue**  
  
    -   **Send** - **/errorReport:send**  
  
     Para obtener más información, consulte [/errorReport (Informar de errores de compilador interno)](http://msdn.microsoft.com/library/819828f8-b0a5-412c-9c57-bf822f17e667).  
  
-   **ExceptionHandling**  
  
     Parámetro String opcional.  
  
     Especifica el modelo de control de excepciones que usará el compilador.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **false** - *\<none>*  
  
    -   **Async** - **/EHa**  
  
    -   **Sync** - **/EHsc**  
  
    -   **SyncCThrow** - **/EHs**  
  
     Para obtener más información, consulte [/EH (Modelo de control de excepciones)](http://msdn.microsoft.com/library/754b916f-d206-4472-b55a-b6f1b0f2cb4d).  
  
-   **ExpandAttributedSource**  
  
     Parámetro booleano opcional.  
  
     Si `true`, crea un archivo de lista con los atributos expandidos insertados en el archivo origen.  
  
     Para obtener más información, consulte [/Fx (Combinar código insertado)](http://msdn.microsoft.com/library/14f0e301-3bab-45a3-bbdf-e7ce66f20560).  
  
-   **FavorSizeOrSpeed**  
  
     Parámetro String opcional.  
  
     Especifica si se va a favorecer el tamaño o la velocidad del código.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **Neither** - *\<none>*  
  
    -   **Size** - **/Os**  
  
    -   **Speed** - **/Ot**  
  
     Para obtener más información, consulte [/Os, /Ot (Favorecer código pequeño, favorecer código rápido)](http://msdn.microsoft.com/library/9a340806-fa15-4308-892c-355d83cac0f2).  
  
-   **FloatingPointExceptions**  
  
     Parámetro booleano opcional.  
  
     Si `true`, activa el modelo confiable de excepción de punto flotante. Las excepciones se generarán inmediatamente después de desencadenarse.  
  
     Para obtener más información, consulte la opción **fp:except** en [/fp (Especificar comportamiento de punto flotante)](http://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e).  
  
-   **FloatingPointModel**  
  
     Parámetro String opcional.  
  
     Establece el modelo de punto flotante.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **Precise** - **/fp:precise**  
  
    -   **Strict** - **/fp:strict**  
  
    -   **Fast** - **/fp:fast**  
  
     Para obtener más información, consulte [/fp (Especificar comportamiento de punto flotante)](http://msdn.microsoft.com/library/10469d6b-e68b-4268-8075-d073f4f5d57e).  
  
-   **ForceConformanceInForLoopScope**  
  
     Parámetro booleano opcional.  
  
     Si `true`, implementa el comportamiento estándar de C++ en los bucles [for](http://msdn.microsoft.com/library/6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a) que utilizan las extensiones de Microsoft ([/Ze](http://msdn.microsoft.com/library/65e49258-7161-4289-a176-7c5c0656b1a2)).  
  
     Para obtener más información, consulte [/Zc:forScope (Forzar ajuste en el ámbito del bucle For)](http://msdn.microsoft.com/library/3031f02d-3b14-4ad0-869e-22b0110c3aed).  
  
-   **ForcedIncludeFiles**  
  
     Parámetro `String[]` opcional.  
  
     Hace que el preprocesador procese uno o varios archivos de encabezado especificados.  
  
     Para obtener más información, consulte [/FI (Dar nombre al archivo de inclusión forzado)](http://msdn.microsoft.com/library/07e79577-8152-4df9-a64c-aae08c603397).  
  
-   **ForcedUsingFiles**  
  
     Parámetro **String[]** opcional.  
  
     Hace que el preprocesador procese uno o varios archivos **#using** especificados.  
  
     Para obtener más información, consulte [/FU (Dar nombre al archivo #using forzado)](http://msdn.microsoft.com/library/698f8603-457f-435a-baff-5ac9243d6ca1).  
  
-   **FunctionLevelLinking**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, permite que el compilador empaquete las funciones individuales con formato de funciones empaquetadas (COMDATs).  
  
     Para obtener más información, consulte [/Gy (Habilitar vinculación en el nivel de función)](http://msdn.microsoft.com/library/0d3cf14c-ed7d-4ad3-b4b6-104e56f61046).  
  
-   **GenerateXMLDocumentationFiles**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, hace que el compilador procese los comentarios de documentación en archivos de código fuente y código y cree un archivo .xdc para cada archivo de código fuente que tenga comentarios de documentación.  
  
     Para obtener más información, consulte [/doc (Procesar comentarios de documentación) (C/C ++)](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Consulte también el parámetro **XMLDocumentationFileName** en esta tabla.  
  
-   **IgnoreStandardIncludePath**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, impide que el compilador busque archivos de inclusión en los directorios especificados en las variables de entorno PATH e INCLUDE.  
  
     Para obtener más información, consulte [/X (Omitir rutas de acceso de inclusión estándar)](http://msdn.microsoft.com/library/16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef).  
  
-   **InlineFunctionExpansion**  
  
     Parámetro **String** opcional.  
  
     Especifica el nivel de expansión de funciones insertadas para la compilación.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **Default** - *\<none>*  
  
    -   **Disabled** - **/Ob0**  
  
    -   **OnlyExplicitInline** - **/Ob1**  
  
    -   **AnySuitable** - **/Ob2**  
  
     Para obtener más información, consulte [/Ob (Expansión de funciones insertadas)](http://msdn.microsoft.com/library/f134e6df-e939-4980-a01d-47425dbc562a).  
  
-   **IntrinsicFunctions**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, reemplaza algunas llamadas a función con formas intrínsecas o especiales de la función que ayudarán a que la aplicación se ejecute con mayor rapidez.  
  
     Para obtener más información, consulte [/Oi (Generar funciones intrínsecas)](http://msdn.microsoft.com/library/fa4a3bf6-0ed8-481b-91c0-add7636132b4).  
  
-   **MinimalRebuild**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, habilita la recompilación mínima, que determina si es necesario recompilar los archivos de origen de C++ que incluyen definiciones de clases de C++ cambiadas (almacenadas en archivos de encabezado [.h]).  
  
     Para obtener más información, consulte [/Gm (Habilitar recompilación mínima)](http://msdn.microsoft.com/library/d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59).  
  
-   **MultiProcessorCompilation**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, utilice varios procesadores para compilar. Este parámetro crea un proceso para cada procesador efectivo en su equipo.  
  
     Para obtener más información, consulte [/MP (Compilar con varios procesos)](http://msdn.microsoft.com/library/a932b14a-74fe-4b45-84e4-6bf53f0f5e07). Consulte también el parámetro **ProcessorNumber** en esta tabla.  
  
-   **ObjectFileName**  
  
     Parámetro **String** opcional.  
  
     Especifica un nombre de archivo objeto (.obj) o un directorio que se utilizará en lugar del predeterminado.  
  
     Para obtener más información, consulte [/Fo (Nombre del archivo objeto)](http://msdn.microsoft.com/library/0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6).  
  
-   **ObjectFiles**  
  
     Parámetro **String[]** opcional.  
  
     Una lista de los archivos objeto.  
  
-   **OmitDefaultLibName**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, omite el nombre de la biblioteca en tiempo de ejecución de C predeterminado del archivo objeto (.obj). De forma predeterminada, el compilador sitúa el nombre de la biblioteca en el archivo .obj para dirigir el enlazador hacia la biblioteca correcta.  
  
     Para obtener más información, consulte [/Zl (Omitir nombre de biblioteca predeterminada)](http://msdn.microsoft.com/library/b27d39d0-44d6-498c-84ae-27c1326fee59).  
  
-   **OmitFramePointers**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, suprime la creación de punteros de marcos en la pila de llamadas.  
  
     Para obtener más información, consulte [/Oy (Omisión de puntero de marco)](http://msdn.microsoft.com/library/c451da86-5297-4c5a-92bc-561d41379853).  
  
-   **OpenMPSupport**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, hace que el compilador procese cláusulas y directivas de OpenMP.  
  
     Para obtener más información, consulte [/openmp (Habilitar la compatibilidad con OpenMP 2.0)](http://msdn.microsoft.com/library/9082b175-18d3-4378-86a7-c0eb95664e13).  
  
-   **Optimization**  
  
     Parámetro **String** opcional.  
  
     Especifica diversas optimizaciones de código para la velocidad y el tamaño.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **Disabled** - **/Od**  
  
    -   **MinSpace** - **/O1**  
  
    -   **MaxSpeed** - **/O2**  
  
    -   **Full** - **/Ox**  
  
     Para obtener más información, consulte [/O (Opciones) (Optimizar código)](http://msdn.microsoft.com/library/77997af9-5555-4b3d-aa57-6615b27d4d5d).  
  
-   **PrecompiledHeader**  
  
     Parámetro **String** opcional.  
  
     Crear o utilizar un archivo de encabezado precompilado (.pch) durante la compilación.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **NotUsing** - *\<none>*  
  
    -   **Create** - **/Yc**  
  
    -   **Use** - **/Yu**  
  
     Para obtener más información, consulte [/Yc (Crear archivo de encabezado precompilado)](http://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) y [/Yu (Utilizar el archivo de encabezado precompilado)](http://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f). Consulte también los parámetros **PrecompiledHeaderFile** y **PrecompiledHeaderOutputFile** en esta tabla.  
  
-   **PrecompiledHeaderFile**  
  
     Parámetro **String** opcional.  
  
     Especifica un nombre de archivo de encabezado precompilado para crear o utilizar.  
  
     Para obtener más información, consulte [/Yc (Crear archivo de encabezado precompilado)](http://msdn.microsoft.com/library/47c2e555-b4f5-46e6-906e-ab5cf21f0678) y [/Yu (Utilizar el archivo de encabezado precompilado)](http://msdn.microsoft.com/library/24f1bd0e-b624-4296-a17e-d4b53e374e1f).  
  
-   **PrecompiledHeaderOutputFile**  
  
     Parámetro **String** opcional.  
  
     Especifica un nombre de ruta de acceso a un encabezado precompilado en lugar de utilizar el nombre de ruta de acceso predeterminado.  
  
     Para obtener más información, consulte [/Fp (Dar nombre al archivo .Pch)](http://msdn.microsoft.com/library/0fcd9cbd-e09f-44d3-9715-b41efb5d0be2).  
  
-   **PreprocessKeepComments**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, conserva los comentarios durante el preprocesamiento.  
  
     Para obtener más información, consulte [/C (Conservar los comentarios durante el preprocesamiento)](http://msdn.microsoft.com/library/944567ca-16bc-4728-befe-d414a7787f26).  
  
-   **PreprocessorDefinitions**  
  
     Parámetro `String[]` opcional.  
  
     Define un símbolo de preprocesamiento para el archivo de origen.  
  
     Para obtener más información, vea [/D (definiciones de preprocesador)](http://msdn.microsoft.com/library/b53fdda7-8da1-474f-8811-ba7cdcc66dba).  
  
-   **PreprocessOutput**  
  
     Parámetro `ITaskItem[]` opcional.  
  
     Define una matriz de elementos de elementos de salida del preprocesador que las tareas pueden consumir y emitir.  
  
-   **PreprocessOutputPath**  
  
     Parámetro `String` opcional.  
  
     Especifica el nombre del archivo de salida en el que el parámetro **PreprocessToFile** escribe la salida preprocesada.  
  
     Para obtener más información, consulte [/Fi (Preprocesar el nombre del archivo de salida)](http://msdn.microsoft.com/library/6d0ba983-a8b7-41ec-84f5-b4688ef8efee).  
  
-   **PreprocessSuppressLineNumbers**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, preprocesa archivos de origen de C y C++ y copia los archivos preprocesados en el dispositivo de salida estándar.  
  
     Para obtener más información, consulte [/EP (Preprocesar para stdout sin directivas #line)](http://msdn.microsoft.com/library/6ec411ae-e33d-4ef5-956e-0054635eabea).  
  
-   **PreprocessToFile**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, preprocesa archivos de origen de C y C++ y escribe la salida preprocesada en un archivo.  
  
     Para obtener más información, consulte [/P (Preprocesar para un archivo)](http://msdn.microsoft.com/library/123ee54f-8219-4a6f-9876-4227023d83fc).  
  
-   **ProcessorNumber**  
  
     Parámetro `Integer` opcional.  
  
     Especifica el número máximo de procesadores que se utilizan en una compilación con varios procesadores. Utilice este parámetro en combinación con el parámetro **MultiProcessorCompilation**.  
  
-   **ProgramDataBaseFileName**  
  
     Parámetro `String` opcional.  
  
     Especifica un nombre de archivo para el archivo de base de datos del programa (PDB).  
  
     Para obtener más información, consulte [/Fd (Nombre del archivo de base de datos del programa)](http://msdn.microsoft.com/library/3977a9ed-f0ac-45df-bf06-01cedd2ba85a).  
  
-   **RuntimeLibrary**  
  
     Parámetro `String` opcional.  
  
     Indica si un módulo multiproceso es un archivo DLL y selecciona versiones comerciales o de depuración de la biblioteca en tiempo de ejecución.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **MultiThreaded** - **/MT**  
  
    -   **MultiThreadedDebug** - **/MTd**  
  
    -   **MultiThreadedDLL** - **/MD**  
  
    -   **MultiThreadedDebugDLL** - **/MDd**  
  
     Para obtener más información, consulte [/MD, / MT, /LD (Utilizar la biblioteca en tiempo de ejecución)](http://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579).  
  
-   **RuntimeTypeInfo**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, agrega código para comprobar los tipos de objetos de C++ en tiempo de ejecución (información de tipo en tiempo de ejecución).  
  
     Para obtener más información, consulte [/GR (Habilitar información de tipo en tiempo de ejecución)](http://msdn.microsoft.com/library/d1f9f850-dcec-49fd-96ef-e72d01148906).  
  
-   **ShowIncludes**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, hace que el compilador genere una lista de los archivos de inclusión.  
  
     Para obtener más información, consulte [/showIncludes (Enumerar archivos de inclusión)](http://msdn.microsoft.com/library/0b74b052-f594-45a6-a7c7-09e1a319547d).  
  
-   **SmallerTypeCheck**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, informa de un error de tiempo de ejecución si un valor se asigna a un tipo de datos más pequeño y produce una pérdida de datos.  
  
     Para obtener más información, consulte la opción **/RTCc** en [/RTC (Comprobaciones de errores de tiempo de ejecución)](http://msdn.microsoft.com/library/9702c558-412c-4004-acd5-80761f589368).  
  
-   **Sources**  
  
     Parámetro `ITaskItem[]` requerido.  
  
     Especifica una lista de archivos de código fuente, separados por espacios.  
  
-   **StringPooling**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, permite al compilador crear una copia de cadenas idénticas en la imagen del programa.  
  
     Para obtener más información, consulte [/GF (Eliminar cadenas duplicadas)](http://msdn.microsoft.com/library/bb7b5d1c-8e1f-453b-9298-8fcebf37d16c).  
  
-   **StructMemberAlignment**  
  
     Parámetro `String` opcional.  
  
     Especifica la alineación de bytes para todos los miembros de una estructura.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **Default** - **/Zp1**  
  
    -   **1Byte** - **/Zp1**  
  
    -   **2Bytes** - **/Zp2**  
  
    -   **4Bytes** - **/Zp4**  
  
    -   **8Bytes** - **/Zp8**  
  
    -   **16Bytes** - **/Zp16**  
  
     Para obtener más información, consulte [/Zp (Alineación de miembros de Struct)](http://msdn.microsoft.com/library/5242f656-ed9b-48a3-bc73-cfcf3ed2520f).  
  
-   **SuppressStartupBanner**  
  
     Parámetro `Boolean` opcional.  
  
     Si es `true`, evita que se muestre el copyright y el mensaje de número de versión cuando la tarea se inicia.   
  
     Para obtener más información, consulte [/nologo (Suprimir el titular de inicio) (C/C ++)](http://msdn.microsoft.com/library/75930d8b-b11c-4db8-99e5-b52f97da0693).  
  
-   **TrackerLogDirectory**  
  
     Parámetro `String` opcional.  
  
     Especifica el directorio intermedio en que se almacenan los registros de seguimiento para esta tarea.  
  
     Para obtener más información, consulte los parámetros **TLogReadFiles** y **TLogWriteFiles** en esta tabla.  
  
-   **TreatSpecificWarningsAsErrors**  
  
     Parámetro **String[]** opcional.  
  
     Trata la lista especificada de advertencias del compilador como errores.  
  
     Para obtener más información, consulte la opción **/we**`n` en [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Nivel de advertencia)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
-   **TreatWarningAsError**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, trata todas las advertencias del compilador como errores.  
  
     Para obtener más información, consulte la opción **/WX** en [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Nivel de advertencia)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
-   **TreatWChar_tAsBuiltInType**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, trate el tipo `wchar_t` como un tipo nativo.  
  
     Para obtener más información, vea [/Zc:wchar_t (wchar_t es un tipo nativo)](http://msdn.microsoft.com/library/b0de5a84-da72-4e5a-9a4e-541099f939e0).  
  
-   **UndefineAllPreprocessorDefinitions**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, anula la definición de los símbolos específicos de Microsoft que el compilador define.  
  
     Para obtener más información, consulte la opción **/u** en [/U, /u (Anular la definición de símbolos)](http://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a).  
  
-   **UndefinePreprocessorDefinitions**  
  
     Parámetro `String[]` opcional.  
  
     Especifica una lista de uno o más símbolos de preprocesador para anular la definición.  
  
     Para obtener más información, consulte la opción **/U** en [/U, /u (Anular la definición de símbolos)](http://msdn.microsoft.com/library/7bc0474f-6d1f-419b-807d-0d8816763b2a).  
  
-   **UseFullPaths**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, muestra la ruta de acceso completa de archivos de código fuente pasados al compilador en diagnósticos.  
  
     Para obtener más información, consulte [/FC (Ruta de acceso completa de archivo de código fuente en diagnósticos)](http://msdn.microsoft.com/library/1f11414e-cb42-421b-be68-9d369aab036b).  
  
-   **UseUnicodeForAssemblerListing**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, hace que el archivo de salida se cree en formato UTF-8.  
  
     Para obtener más información, consulte la opción **/FAu** en [/FA, /Fa (Archivo de lista)](http://msdn.microsoft.com/library/c7507d0e-c69d-44f9-b8e2-d2c398697402).  
  
-   **WarningLevel**  
  
     Parámetro `String` opcional.  
  
     Especifica el nivel de advertencia máximo que el compilador generará.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **TurnOffAllWarnings** - **/W0**  
  
    -   **Level1** - **/W1**  
  
    -   **Level2** - **/W2**  
  
    -   **Level3** - **/W3**  
  
    -   **Level4** - **/W4**  
  
    -   **EnableAllWarnings** - **/Wall**  
  
     Para obtener más información, consulte la opción **/W**_n_ en [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Nivel de advertencia)](http://msdn.microsoft.com/library/d6bc7bf5-c754-4879-909c-8e3a67e2629f).  
  
-   **WholeProgramOptimization**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, habilita la optimización de todo el programa.  
  
     Para obtener más información, consulte [/GL (Optimización de todo el programa)](http://msdn.microsoft.com/library/09d51e2d-9728-4bd0-b5dc-3b8284aca1d1).  
  
-   **XMLDocumentationFileName**  
  
     Parámetro `String` opcional.  
  
     Especifica el nombre de los archivos de documentación XML generados. Este parámetro puede ser un nombre de archivo o directorio.  
  
     Para obtener más información, consulte el argumento `name` en [/doc (Procesar comentarios de documentación) (C/C ++)](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Consulte también el parámetro **GenerateXMLDocumentationFiles** en esta tabla.  
  
-   **MinimalRebuildFromTracking**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, se realiza una compilación incremental con seguimiento; si `false`, se realiza una recompilación.  
  
-   **TLogReadFiles**  
  
     Parámetro `ITaskItem[]` opcional.  
  
     Especifica una matriz de elementos que representan los *registros de seguimiento de archivos de lectura*.  
  
     Un registro de seguimiento de archivos de lectura (.tlog) contiene los nombres de los archivos de entrada que una tarea lee, y el sistema de compilación de proyecto lo utiliza para admitir las compilaciones incrementales. Para obtener más información, consulte los parámetros **TrackerLogDirectory** y **TrackFileAccess** en esta tabla.  
  
-   **TLogWriteFiles**  
  
     Parámetro `ITaskItem[]` opcional.  
  
     Especifica una matriz de elementos que representan los *registros de seguimiento de archivos de escritura*.  
  
     Un registro de seguimiento de archivos de escritura (.tlog) contiene los nombres de los archivos de salida que una tarea escribe, y el sistema de compilación de proyecto lo utiliza para admitir las compilaciones incrementales. Para obtener más información, consulte los parámetros **TrackerLogDirectory** y **TrackFileAccess** en esta tabla.  
  
-   **TrackFileAccess**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, realiza un seguimiento de los patrones de acceso a archivos.  
  
     Para obtener más información, consulte los parámetros **TLogReadFiles** y **TLogWriteFiles** en esta tabla.  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)



