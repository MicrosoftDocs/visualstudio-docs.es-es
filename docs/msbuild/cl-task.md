---
title: CL (tarea) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
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
caps.latest.revision: 18
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 4ad346483c37e1f221ebd396a60d30b5bf94a028
ms.lasthandoff: 02/22/2017

---
# <a name="cl-task"></a>CL (Tarea)
Incluye la herramienta compilador de Visual C++, cl.exe. El compilador genera archivos ejecutables (.exe), archivos de biblioteca de vínculos dinámicos (.dll) o archivos de módulos de códigos (.netmodule). Para obtener más información, consulte [Opciones del compilador](/visual-cpp/build/reference/compiler-options).  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea **CL**. La mayoría de los parámetros de tarea, así como algunos conjuntos de parámetros, corresponden a una opción de línea de comandos.  
  
-   **AdditionalIncludeDirectories**  
  
     Parámetro String[] opcional.  
  
     Agrega un directorio a la lista de directorios en que se buscan archivos de inclusión.  
  
     Para obtener más información, consulte [/I (Directorios de inclusión adicionales)](/visual-cpp/build/reference/i-additional-include-directories).  
  
-   **AdditionalOptions**  
  
     Parámetro String opcional.  
  
     Una lista de opciones de la línea de comandos. Por ejemplo, "/*option1* /*option2* /*option#*". Utilice este parámetro para especificar opciones de la línea de comandos que no están representadas por ningún otro parámetro de tarea.  
  
     Para obtener más información, consulte [Opciones del compilador](/visual-cpp/build/reference/compiler-options).  
  
-   **AdditionalUsingDirectories**Parámetro String[] opcional.  
  
     Especifica un directorio en que el compilador debe buscar para resolver las referencias de archivos que se pasan a la directiva **#using**.  
  
     Para obtener más información, consulte [/AI (Especificar directorios de metadatos)](/visual-cpp/build/reference/ai-specify-metadata-directories).  
  
-   **AlwaysAppend**  
  
     Parámetro String opcional.  
  
     Una cadena que siempre se emite en la línea de comandos. Su valor predeterminado es "**/c**".  
  
-   **AssemblerListingLocation**  
  
     Crea un archivo de lista que contiene el código de ensamblado.  
  
     Para obtener más información, consulte la opción **/Fa** en [/FA, /Fa (Archivo de lista)](/visual-cpp/build/reference/fa-fa-listing-file).  
  
-   **AssemblerOutput**  
  
     Parámetro String opcional.  
  
     Crea un archivo de lista que contiene el código de ensamblado.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **NoListing** - *\<none>*  
  
    -   **AssemblyCode** - **/FA**  
  
    -   **AssemblyAndMachineCode** - **/FAc**  
  
    -   **AssemblyAndMachineCode** - **/FAc**  
  
    -   **All** - **/FAcs**  
  
     Para obtener más información, consulte las opciones **/FA**, **/FAc**, **/FAs** y **/FAcs** en [/FA, /Fa (Archivo de lista)](/visual-cpp/build/reference/fa-fa-listing-file).  
  
-   **BasicRuntimeChecks**  
  
     Parámetro String opcional.  
  
     Activa y desactiva la característica de comprobación de errores en tiempo de ejecución, junto con el pragma [runtime_checks](/visual-cpp/preprocessor/runtime-checks).  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **Default** -                          *\<none>*  
  
    -   **StackFrameRuntimeCheck** -  **/RTCs**  
  
    -   **UninitializedLocalUsageCheck** - **/RTCu**  
  
    -   **EnableFastChecks** -                          **/RTC1**  
  
     Para obtener más información, consulte [/RTC (Comprobaciones de errores de tiempo de ejecución)](/visual-cpp/build/reference/rtc-run-time-error-checks).  
  
-   **BrowseInformation**  
  
     Parámetro booleano opcional.  
  
     Si `true`, crea un archivo de información de examen.  
  
     Para obtener más información, consulte la opción **/FR** en [/FR, /Fr (Crear archivo .Sbr)](/visual-cpp/build/reference/fr-fr-create-dot-sbr-file).  
  
-   **BrowseInformationFile**  
  
     Parámetro String opcional.  
  
     Especifica un nombre de archivo para el archivo de información de examen.  
  
     Para obtener más información, consulte el parámetro **BrowseInformation** en esta tabla y también [/FR, /Fr (Crear archivo .Sbr)](/visual-cpp/build/reference/fr-fr-create-dot-sbr-file).  
  
-   **BufferSecurityCheck**  
  
     Parámetro booleano opcional.  
  
     Si `true`, detecta algunas saturaciones de búfer que sobrescriben la dirección de retorno, una técnica común para aprovechar código que no impone restricciones de tamaño de búfer.  
  
     Para obtener más información, consulte [/GS (Comprobación de seguridad del búfer)](/visual-cpp/build/reference/gs-buffer-security-check).  
  
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
  
     Para obtener más información, consulte [/Gd, /Gr, /Gv, /Gz (Convención de llamada)](/visual-cpp/build/reference/gd-gr-gv-gz-calling-convention).  
  
-   **CompileAs**  
  
     Parámetro String opcional.  
  
     Especifica si se debe compilar el archivo de entrada como un archivo de código fuente de C o C++.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **Default** - *\<none>*  
  
    -   **CompileAsC** - **/TC**  
  
    -   **CompileAsCpp** - **/TP**  
  
     Para obtener más información, consulte [/Tc, /Tp, /TC, /TP (Especificar el tipo del archivo de origen)](/visual-cpp/build/reference/tc-tp-tc-tp-specify-source-file-type).  
  
-   **CompileAsManaged**  
  
     Parámetro String opcional.  
  
     Permite que las aplicaciones y los componentes usen las características de Common Language Runtime (CLR).  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **false** - *\<none>*  
  
    -   **true** - **/clr**  
  
    -   **Pure** - **/clr:pure**  
  
    -   **Safe** - **/clr:safe**  
  
    -   **OldSyntax** -  **/CLR: oldSyntax**  
  
     Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](/visual-cpp/build/reference/clr-common-language-runtime-compilation).  
  
-   **CreateHotpatchableImage**  
  
     Parámetro booleano opcional.  
  
     Si `true`, indica al compilador que prepare una imagen para *aplicar una revisión reciente*. Este parámetro garantiza que la primera instrucción de cada función sea de dos bytes, lo cual es necesario para aplicar una revisión reciente.  
  
     Para obtener más información, consulte [/hotpatch (Crear una imagen a la que se puede aplicar una revisión reciente)](/visual-cpp/build/reference/hotpatch-create-hotpatchable-image).  
  
-   **DebugInformationFormat**  
  
     Parámetro String opcional.  
  
     Seleccione el tipo de información de depuración que se crea para el programa y si esta información se conserva en archivos objeto (.obj) o en una base de datos de programa (PDB).  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **OldStyle** - **/Z7**  
  
    -   **ProgramDatabase** -  **/Zi**  
  
    -   **EditAndContinue** -  **/Zi**  
  
     Para obtener más información, consulte [/Z7, /Zi, /ZI (Formato de la información de depuración)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format).  
  
-   **DisableLanguageExtensions**  
  
     Parámetro booleano opcional.  
  
     Si **true**, indica al compilador que emita un error para las construcciones de lenguaje que no son compatibles con ANSI C o ANSI C++.  
  
     Para obtener más información, consulte la opción **/Za** en [/Za, /Ze (Desactivar extensiones de lenguaje)](/visual-cpp/build/reference/za-ze-disable-language-extensions).  
  
-   **DisableSpecificWarnings**  
  
     Parámetro String[] opcional.  
  
     Desactiva los números de advertencia que se especifican en una lista delimitada por punto y coma.  
  
     Para obtener más información, consulte la opción `/wd` en [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Nivel de advertencia)](/visual-cpp/build/reference/compiler-option-warning-level).  
  
-   **EnableEnhancedInstructionSet**  
  
     Parámetro String opcional.  
  
     Especifica la arquitectura para la generación de código que utiliza las instrucciones de las extensiones SIMD de streaming (SSE) y las extensiones SIMD de streaming 2 (SSE2).  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **StreamingSIMDExtensions** - **/arch:SSE**  
  
    -   **StreamingSIMDExtensions2** - **/arch:SSE2**  
  
     Para obtener más información, consulte [/arch (x86)](/visual-cpp/build/reference/arch-x86).  
  
-   **EnableFiberSafeOptimizations**  
  
     Parámetro booleano opcional.  
  
     Si `true`, admite la seguridad de fibras para los datos asignados mediante almacenamiento local de subprocesos estáticos, es decir, los datos asignados mediante `__declspec(thread)`.  
  
     Para obtener más información, consulte [/GT (Admitir el almacenamiento local de subprocesos seguros para fibra)](/visual-cpp/build/reference/gt-support-fiber-safe-thread-local-storage).  
  
-   **EnablePREfast**  
  
     Parámetro booleano opcional.  
  
     Si `true`, habilita el análisis de código.  
  
     Para obtener más información, consulte [/analize (Análisis de código)](/visual-cpp/build/reference/analyze-code-analysis).  
  
-   **ErrorReporting**  
  
     Parámetro String opcional.  
  
     Permite proporcionar directamente a Microsoft información sobre los errores internos del compilador (ICE). De forma predeterminada, la configuración de compilaciones del IDE es **Prompt** y la configuración en las compilaciones de la línea de comandos es **Queue**.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **None** - **/errorReport:none**  
  
    -   **Prompt** - **/errorReport:prompt**  
  
    -   **Queue** - **/errorReport:queue**  
  
    -   **Send** - **/errorReport:send**  
  
     Para obtener más información, consulte [/errorReport (Informar de errores de compilador interno)](/visual-cpp/build/reference/errorreport-report-internal-compiler-errors).  
  
-   **ExceptionHandling**  
  
     Parámetro String opcional.  
  
     Especifica el modelo de control de excepciones que usará el compilador.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **false** - *\<none>*  
  
    -   **Async** - **/EHa**  
  
    -   **Sync** - **/EHsc**  
  
    -   **SyncCThrow** - **/EHs**  
  
     Para obtener más información, consulte [/EH (Modelo de control de excepciones)](/visual-cpp/build/reference/eh-exception-handling-model).  
  
-   **ExpandAttributedSource**  
  
     Parámetro booleano opcional.  
  
     Si `true`, crea un archivo de lista con los atributos expandidos insertados en el archivo origen.  
  
     Para obtener más información, consulte [/Fx (Combinar código insertado)](/visual-cpp/build/reference/fx-merge-injected-code).  
  
-   **FavorSizeOrSpeed**  
  
     Parámetro String opcional.  
  
     Especifica si se va a favorecer el tamaño o la velocidad del código.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **Neither** - *\<none>*  
  
    -   **Size** - **/Os**  
  
    -   **Speed** - **/Ot**  
  
     Para obtener más información, consulte [/Os, /Ot (Favorecer código pequeño, favorecer código rápido)](/visual-cpp/build/reference/os-ot-favor-small-code-favor-fast-code).  
  
-   **FloatingPointExceptions**  
  
     Parámetro booleano opcional.  
  
     Si `true`, activa el modelo confiable de excepción de punto flotante. Las excepciones se generarán inmediatamente después de desencadenarse.  
  
     Para obtener más información, consulte la opción **fp:except** en [/fp (Especificar comportamiento de punto flotante)](/visual-cpp/build/reference/fp-specify-floating-point-behavior).  
  
-   **FloatingPointModel**  
  
     Parámetro String opcional.  
  
     Establece el modelo de punto flotante.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **Precise** - **/fp:precise**  
  
    -   **Strict** - **/fp:strict**  
  
    -   **Fast** - **/fp:fast**  
  
     Para obtener más información, consulte [/fp (Especificar comportamiento de punto flotante)](/visual-cpp/build/reference/fp-specify-floating-point-behavior).  
  
-   **ForceConformanceInForLoopScope**  
  
     Parámetro booleano opcional.  
  
     Si `true`, implementa el comportamiento estándar de C++ en los bucles [for](/visual-cpp/cpp/for-statement-cpp) que utilizan las extensiones de Microsoft ([/Ze](/visual-cpp/build/reference/za-ze-disable-language-extensions)).  
  
     Para obtener más información, consulte [/Zc:forScope (Forzar ajuste en el ámbito del bucle For)](http://msdn.microsoft.com/Library/3031f02d-3b14-4ad0-869e-22b0110c3aed).  
  
-   **ForcedIncludeFiles**  
  
     Parámetro `String[]` opcional.  
  
     Hace que el preprocesador procese uno o varios archivos de encabezado especificados.  
  
     Para obtener más información, consulte [/FI (Dar nombre al archivo de inclusión forzado)](/visual-cpp/build/reference/fi-name-forced-include-file).  
  
-   **ForcedUsingFiles**  
  
     Parámetro **String[]** opcional.  
  
     Hace que el preprocesador procese uno o varios archivos **#using** especificados.  
  
     Para obtener más información, consulte [/FU (Dar nombre al archivo #using forzado)](/visual-cpp/build/reference/fu-name-forced-hash-using-file).  
  
-   **FunctionLevelLinking**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, permite que el compilador empaquete las funciones individuales con formato de funciones empaquetadas (COMDATs).  
  
     Para obtener más información, consulte [/Gy (Habilitar vinculación en el nivel de función)](/visual-cpp/build/reference/gy-enable-function-level-linking).  
  
-   **GenerateXMLDocumentationFiles**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, hace que el compilador procese los comentarios de documentación en archivos de código fuente y código y cree un archivo .xdc para cada archivo de código fuente que tenga comentarios de documentación.  
  
     Para obtener más información, consulte [/doc (Procesar comentarios de documentación) (C/C ++)](/visual-cpp/build/reference/doc-process-documentation-comments-c-cpp). Consulte también el parámetro **XMLDocumentationFileName** en esta tabla.  
  
-   **IgnoreStandardIncludePath**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, impide que el compilador busque archivos de inclusión en los directorios especificados en las variables de entorno PATH e INCLUDE.  
  
     Para obtener más información, consulte [/X (Omitir rutas de acceso de inclusión estándar)](/visual-cpp/build/reference/x-ignore-standard-include-paths).  
  
-   **InlineFunctionExpansion**  
  
     Parámetro **String** opcional.  
  
     Especifica el nivel de expansión de funciones insertadas para la compilación.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **Default** - *\<none>*  
  
    -   **Disabled** - **/Ob0**  
  
    -   **OnlyExplicitInline** - **/Ob1**  
  
    -   **AnySuitable** - **/Ob2**  
  
     Para obtener más información, consulte [/Ob (Expansión de funciones insertadas)](/visual-cpp/build/reference/ob-inline-function-expansion).  
  
-   **IntrinsicFunctions**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, reemplaza algunas llamadas a función con formas intrínsecas o especiales de la función que ayudarán a que la aplicación se ejecute con mayor rapidez.  
  
     Para obtener más información, consulte [/Oi (Generar funciones intrínsecas)](/visual-cpp/build/reference/oi-generate-intrinsic-functions).  
  
-   **MinimalRebuild**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, habilita la recompilación mínima, que determina si es necesario recompilar los archivos de origen de C++ que incluyen definiciones de clases de C++ cambiadas (almacenadas en archivos de encabezado [.h]).  
  
     Para obtener más información, consulte [/Gm (Habilitar recompilación mínima)](/visual-cpp/build/reference/gm-enable-minimal-rebuild).  
  
-   **MultiProcessorCompilation**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, utilice varios procesadores para compilar. Este parámetro crea un proceso para cada procesador efectivo en su equipo.  
  
     Para obtener más información, consulte [/MP (Compilar con varios procesos)](/visual-cpp/build/reference/mp-build-with-multiple-processes). Consulte también el parámetro **ProcessorNumber** en esta tabla.  
  
-   **ObjectFileName**  
  
     Parámetro **String** opcional.  
  
     Especifica un nombre de archivo objeto (.obj) o un directorio que se utilizará en lugar del predeterminado.  
  
     Para obtener más información, consulte [/Fo (Nombre del archivo objeto)](/visual-cpp/build/reference/fo-object-file-name).  
  
-   **ObjectFiles**  
  
     Parámetro **String[]** opcional.  
  
     Una lista de los archivos objeto.  
  
-   **OmitDefaultLibName**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, omite el nombre de la biblioteca en tiempo de ejecución de C predeterminado del archivo objeto (.obj). De forma predeterminada, el compilador sitúa el nombre de la biblioteca en el archivo .obj para dirigir el enlazador hacia la biblioteca correcta.  
  
     Para obtener más información, consulte [/Zl (Omitir nombre de biblioteca predeterminada)](/visual-cpp/build/reference/zl-omit-default-library-name).  
  
-   **OmitFramePointers**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, suprime la creación de punteros de marcos en la pila de llamadas.  
  
     Para obtener más información, consulte [/Oy (Omisión de puntero de marco)](/visual-cpp/build/reference/oy-frame-pointer-omission).  
  
-   **OpenMPSupport**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, hace que el compilador procese cláusulas y directivas de OpenMP.  
  
     Para obtener más información, consulte [/openmp (Habilitar la compatibilidad con OpenMP 2.0)](/visual-cpp/build/reference/openmp-enable-openmp-2-0-support).  
  
-   **Optimization**  
  
     Parámetro **String** opcional.  
  
     Especifica diversas optimizaciones de código para la velocidad y el tamaño.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **Disabled** - **/Od**  
  
    -   **MinSpace** - **/O1**  
  
    -   **MaxSpeed** - **/O2**  
  
    -   **Full** - **/Ox**  
  
     Para obtener más información, consulte [/O (Opciones) (Optimizar código)](/visual-cpp/build/reference/o-options-optimize-code).  
  
-   **PrecompiledHeader**  
  
     Parámetro **String** opcional.  
  
     Crear o utilizar un archivo de encabezado precompilado (.pch) durante la compilación.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **NotUsing** - *\<none>*  
  
    -   **Create** - **/Yc**  
  
    -   **Use** - **/Yu**  
  
     Para obtener más información, consulte [/Yc (Crear archivo de encabezado precompilado)](/visual-cpp/build/reference/yc-create-precompiled-header-file) y [/Yu (Utilizar el archivo de encabezado precompilado)](/visual-cpp/build/reference/yu-use-precompiled-header-file). Consulte también los parámetros **PrecompiledHeaderFile** y **PrecompiledHeaderOutputFile** en esta tabla.  
  
-   **PrecompiledHeaderFile**  
  
     Parámetro **String** opcional.  
  
     Especifica un nombre de archivo de encabezado precompilado para crear o utilizar.  
  
     Para obtener más información, consulte [/Yc (Crear archivo de encabezado precompilado)](/visual-cpp/build/reference/yc-create-precompiled-header-file) y [/Yu (Utilizar el archivo de encabezado precompilado)](/visual-cpp/build/reference/yu-use-precompiled-header-file).  
  
-   **PrecompiledHeaderOutputFile**  
  
     Parámetro **String** opcional.  
  
     Especifica un nombre de ruta de acceso a un encabezado precompilado en lugar de utilizar el nombre de ruta de acceso predeterminado.  
  
     Para obtener más información, consulte [/Fp (Dar nombre al archivo .Pch)](/visual-cpp/build/reference/fp-name-dot-pch-file).  
  
-   **PreprocessKeepComments**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, conserva los comentarios durante el preprocesamiento.  
  
     Para obtener más información, consulte [/C (Conservar los comentarios durante el preprocesamiento)](/visual-cpp/build/reference/c-preserve-comments-during-preprocessing).  
  
-   **PreprocessorDefinitions**  
  
     Parámetro `String[]` opcional.  
  
     Define un símbolo de preprocesamiento para el archivo de origen.  
  
     Para obtener más información, vea [/D (definiciones de preprocesador)](/visual-cpp/build/reference/d-preprocessor-definitions).  
  
-   **PreprocessOutput**  
  
     Parámetro `ITaskItem[]` opcional.  
  
     Define una matriz de elementos de elementos de salida del preprocesador que las tareas pueden consumir y emitir.  
  
-   **PreprocessOutputPath**  
  
     Parámetro `String` opcional.  
  
     Especifica el nombre del archivo de salida en el que el parámetro **PreprocessToFile** escribe la salida preprocesada.  
  
     Para obtener más información, consulte [/Fi (Preprocesar el nombre del archivo de salida)](/visual-cpp/build/reference/fi-preprocess-output-file-name).  
  
-   **PreprocessSuppressLineNumbers**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, preprocesa archivos de origen de C y C++ y copia los archivos preprocesados en el dispositivo de salida estándar.  
  
     Para obtener más información, consulte [/EP (Preprocesar para stdout sin directivas #line)](/visual-cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).  
  
-   **PreprocessToFile**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, preprocesa archivos de origen de C y C++ y escribe la salida preprocesada en un archivo.  
  
     Para obtener más información, consulte [/P (Preprocesar para un archivo)](/visual-cpp/build/reference/p-preprocess-to-a-file).  
  
-   **ProcessorNumber**  
  
     Parámetro `Integer` opcional.  
  
     Especifica el número máximo de procesadores que se utilizan en una compilación con varios procesadores. Utilice este parámetro en combinación con el parámetro **MultiProcessorCompilation**.  
  
-   **ProgramDataBaseFileName**  
  
     Parámetro `String` opcional.  
  
     Especifica un nombre de archivo para el archivo de base de datos del programa (PDB).  
  
     Para obtener más información, consulte [/Fd (Nombre del archivo de base de datos del programa)](/visual-cpp/build/reference/fd-program-database-file-name).  
  
-   **RuntimeLibrary**  
  
     Parámetro `String` opcional.  
  
     Indica si un módulo multiproceso es un archivo DLL y selecciona versiones comerciales o de depuración de la biblioteca en tiempo de ejecución.  
  
     Especifique uno de los valores siguientes, cada uno de los cuales corresponde a una opción de línea de comandos.  
  
    -   **MultiThreaded** - **/MT**  
  
    -   **MultiThreadedDebug** - **/MTd**  
  
    -   **MultiThreadedDLL** - **/MD**  
  
    -   **MultiThreadedDebugDLL** - **/MDd**  
  
     Para obtener más información, consulte [/MD, / MT, /LD (Utilizar la biblioteca en tiempo de ejecución)](/visual-cpp/build/reference/md-mt-ld-use-run-time-library).  
  
-   **RuntimeTypeInfo**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, agrega código para comprobar los tipos de objetos de C++ en tiempo de ejecución (información de tipo en tiempo de ejecución).  
  
     Para obtener más información, consulte [/GR (Habilitar información de tipo en tiempo de ejecución)](/visual-cpp/build/reference/gr-enable-run-time-type-information).  
  
-   **ShowIncludes**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, hace que el compilador genere una lista de los archivos de inclusión.  
  
     Para obtener más información, consulte [/showIncludes (Enumerar archivos de inclusión)](/visual-cpp/build/reference/showincludes-list-include-files).  
  
-   **SmallerTypeCheck**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, informa de un error de tiempo de ejecución si un valor se asigna a un tipo de datos más pequeño y produce una pérdida de datos.  
  
     Para obtener más información, consulte la opción **/RTCc** en [/RTC (Comprobaciones de errores de tiempo de ejecución)](/visual-cpp/build/reference/rtc-run-time-error-checks).  
  
-   **Sources**  
  
     Parámetro `ITaskItem[]` requerido.  
  
     Especifica una lista de archivos de código fuente, separados por espacios.  
  
-   **StringPooling**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, permite al compilador crear una copia de cadenas idénticas en la imagen del programa.  
  
     Para obtener más información, consulte [/GF (Eliminar cadenas duplicadas)](/visual-cpp/build/reference/gf-eliminate-duplicate-strings).  
  
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
  
     Para obtener más información, consulte [/Zp (Alineación de miembros de Struct)](/visual-cpp/build/reference/zp-struct-member-alignment).  
  
-   **SuppressStartupBanner**  
  
     Parámetro `Boolean` opcional.  
  
     Si es `true`, evita que se muestre el copyright y el mensaje de número de versión cuando la tarea se inicia.   
  
     Para obtener más información, consulte [/nologo (Suprimir el titular de inicio) (C/C ++)](/visual-cpp/build/reference/nologo-suppress-startup-banner-c-cpp).  
  
-   **TrackerLogDirectory**  
  
     Parámetro `String` opcional.  
  
     Especifica el directorio intermedio en que se almacenan los registros de seguimiento para esta tarea.  
  
     Para obtener más información, consulte los parámetros **TLogReadFiles** y **TLogWriteFiles** en esta tabla.  
  
-   **TreatSpecificWarningsAsErrors**  
  
     Parámetro **String[]** opcional.  
  
     Trata la lista especificada de advertencias del compilador como errores.  
  
     Para obtener más información, consulte la opción **/we**`n` en [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Nivel de advertencia)](/visual-cpp/build/reference/compiler-option-warning-level).  
  
-   **TreatWarningAsError**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, trata todas las advertencias del compilador como errores.  
  
     Para obtener más información, consulte la opción **/WX** en [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Nivel de advertencia)](/visual-cpp/build/reference/compiler-option-warning-level).  
  
-   **TreatWChar_tAsBuiltInType**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, trate el tipo `wchar_t` como un tipo nativo.  
  
     Para obtener más información, vea [/Zc:wchar_t (wchar_t es un tipo nativo)](http://msdn.microsoft.com/Library/b0de5a84-da72-4e5a-9a4e-541099f939e0).  
  
-   **UndefineAllPreprocessorDefinitions**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, anula la definición de los símbolos específicos de Microsoft que el compilador define.  
  
     Para obtener más información, consulte la opción **/u** en [/U, /u (Anular la definición de símbolos)](/visual-cpp/build/reference/u-u-undefine-symbols).  
  
-   **UndefinePreprocessorDefinitions**  
  
     Parámetro `String[]` opcional.  
  
     Especifica una lista de uno o más símbolos de preprocesador para anular la definición.  
  
     Para obtener más información, consulte la opción **/U** en [/U, /u (Anular la definición de símbolos)](/visual-cpp/build/reference/u-u-undefine-symbols).  
  
-   **UseFullPaths**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, muestra la ruta de acceso completa de archivos de código fuente pasados al compilador en diagnósticos.  
  
     Para obtener más información, consulte [/FC (Ruta de acceso completa de archivo de código fuente en diagnósticos)](/visual-cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).  
  
-   **UseUnicodeForAssemblerListing**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, hace que el archivo de salida se cree en formato UTF-8.  
  
     Para obtener más información, consulte la opción **/FAu** en [/FA, /Fa (Archivo de lista)](/visual-cpp/build/reference/fa-fa-listing-file).  
  
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
  
     Para obtener más información, consulte la opción **/W***n* en [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Nivel de advertencia)](/visual-cpp/build/reference/compiler-option-warning-level).  
  
-   **WholeProgramOptimization**  
  
     Parámetro `Boolean` opcional.  
  
     Si `true`, habilita la optimización de todo el programa.  
  
     Para obtener más información, consulte [/GL (Optimización de todo el programa)](/visual-cpp/build/reference/gl-whole-program-optimization).  
  
-   **XMLDocumentationFileName**  
  
     Parámetro `String` opcional.  
  
     Especifica el nombre de los archivos de documentación XML generados. Este parámetro puede ser un nombre de archivo o directorio.  
  
     Para obtener más información, consulte el argumento `name` en [/doc (Procesar comentarios de documentación) (C/C ++)](/visual-cpp/build/reference/doc-process-documentation-comments-c-cpp). Consulte también el parámetro **GenerateXMLDocumentationFiles** en esta tabla.  
  
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
