---
title: Tarea ClangCompile | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.clangcompile
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), ClangCompile task
- ClangCompile task (MSBuild (C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 1bd1d749461c423d51e0f5b736563a9f9aa757c5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747343"
---
# <a name="clangcompile-task"></a>Tarea ClangCompile

Incluye la herramienta del compilador de Microsoft C++, clang.exe.

## <a name="parameters"></a>Parámetros

En la tabla siguiente se describen los parámetros de la tarea **ClangCompile**.

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Parámetro **string[]** opcional.<br/><br/>Especifica uno o más directorios que se agregarán a la ruta de acceso de inclusión; si hay más de uno, sepárelos mediante punto y coma.<br/><br/>Use `-I[path]`.|
|**AdditionalOptions**|Parámetro **string** opcional.|
|**BufferSecurityCheck**|Parámetro **string** opcional.<br/><br/>La comprobación de seguridad ayuda a detectar desbordamientos del búfer de pila, un ataque común contra la seguridad de un programa. <br/><br/>Use `fstack-protector`.|
|**BuildingInIde**|Parámetro **bool** opcional.|
|**CLanguageStandard**|Parámetro **string** opcional.<br/><br/>Determina el estándar de lenguaje C.<br/><br/>Use `std=[value]` con el valor de **c89**, **c99**, **c11**, **gnu99** o **gnu11**.|
|**ClangVersion**|Parámetro **string** opcional.|
|**CompileAs**|Parámetro **string** opcional.<br/><br/>Permite seleccionar la opción de lenguaje de compilación para los archivos .c y .cpp. En la opción predeterminada, la detección se realizará en función de la extensión .c o .cpp.<br/><br/>Use `-x c`, `-x c++`.|
|**CppLanguageStandard**|Parámetro **string** opcional.<br/><br/>Determina el estándar de lenguaje C++.<br/><br/>Use `std=[value]` con el valor de **c++98**, **c++11**, **c++1y**, **gnu++98**, **gnu++11** o **gnu++1y**.|
|**DataLevelLinking**|Parámetro **bool** opcional.<br/><br/>Permite que las optimizaciones del enlazador quiten datos no usados al emitir cada elemento de datos en una sección distinta.|
|**DebugInformationFormat**|Parámetro **string** opcional.<br/><br/>Especifica el tipo de información de depuración generado por el compilador.<br/><br/>**None**, no produce información de depuración, por lo que la compilación puede ser más rápida (use `g0`).<br/>**FullDebug**, genere información de depuración de DWARF2 (use `g2 -gdwarf-2`).<br/>**LineNumber**, genere solo información del número de línea (use `gline-tables-only`).|
|**EnableNeonCodegen**|Parámetro **bool** opcional.<br/><br/>Habilita la generación de código para hardware de punto flotante NEON. Solo es válido para la arquitectura ARM.|
|**ExceptionHandling**|Parámetro **string** opcional.<br/><br/>Especifica el modelo de control de excepciones que usará el compilador.<br/><br/>**Disabled**, deshabilite el control de excepciones (use `fno-exceptions`).<br/>**Enabled**, habilite el control de excepciones (use `fexceptions`).<br/>**UnwindTables**, genera cualquier dato estático necesario, pero no afrcta al código generado(use `funwind-tables`).|
|**FloatABI**|Parámetro **string** opcional.<br/><br/>Opción de selección para elegir ABI de punto flotante.<br/><br/>**soft**, hace que el compilador genere una salida que contiene llamadas de biblioteca para operaciones de punto flotante (use `mfloat-abi=soft`).<br/>**softfp**, permite generar código con instrucciones de punto flotante de hardware, pero sigue usando las convenciones de llamadas flotantes de software (use `mfloat-abi=softfp`).<br/>**hard**, permite generar instrucciones de punto flotante y usa convenciones de llamadas específicas de FPU (use `mfloat-abi=hard`).|
|**ForcedIncludeFiles**|Parámetro **string[]** opcional.<br/><br/>Uno o más archivos de inclusión obligatorios.<br/><br/>Use `-include [name]`.|
|**FunctionLevelLinking**|Parámetro **bool** opcional.<br/><br/>Permite que el compilador empaquete las funciones individuales con formato de funciones empaquetadas (COMDATs). Es necesario para que funcione Editar y continuar.<br/><br/>Use `ffunction-sections`.|
|**GccToolChain**|Parámetro **string** opcional.<br/><br/>Ruta de carpetas a la cadena de herramientas Gcc.|
|**GNUMode**|Parámetro **bool** opcional.<br/><br/>|
|**MSCompatibility**|Parámetro **bool** opcional.<br/><br/>Habilitar la compatibilidad total con Microsoft C++.|
|**MSCompatibilityVersion**|Parámetro **string** opcional.<br/><br/>Valor separado por puntos que representa el número de versión del compilador de Microsoft del que se informa en _MSC_VER (0 = no definirlo [valor predeterminado]).|
|**MSExtensions**|Parámetro **bool** opcional.<br/><br/>Aceptar algunas construcciones no estándar que admita el compilador de Microsoft.|
|**MSCompilerVersion**|Parámetro **string** opcional.<br/><br/>Número de versión del compilador de Microsoft del que se informa en _MSC_VER (0 = no definirlo [valor predeterminado]).|
|**MSVCErrorReport**|Parámetro **bool** opcional.<br/><br/>Informar de los errores que pueda usar Visual Studio para realizar un análisis en busca de información de archivos y líneas.|
|**ObjectFileName**|Parámetro **string** opcional.<br/><br/>Especifica un nombre para reemplazar el nombre del archivo objeto predeterminado. Puede ser un nombre de archivo o de directorio.<br/><br/>Use `/Fo[name]`.|
|**OmitFramePointers**|Parámetro **bool** opcional.<br/><br/>Suprime la creación de punteros de marcos en la pila de llamadas.|
|**Optimization**|Parámetro **string** opcional.<br/><br/>Especifica el nivel de optimización de la aplicación.<br/><br/>**Custom**, optimización personalizada.<br/>**Disabled**, deshabilite la optimización (use `O0`).<br/>**MinSize**, optimice el tamaño (use `Os`).<br/>**MaxSpeed**, optimice la velocidad (use `O2`).<br/>**Full**, optimizaciones costosas (use `O3`).|
|**PositionIndependentCode**|Parámetro **bool** opcional.<br/><br/>Genera código independiente de posición (PIC) para usarlo en una biblioteca compartida.|
|**PrecompiledHeader**|Parámetro **string** opcional.<br/><br/>Habilita la creación o el uso de un encabezado precompilado durante la compilación.|
|**PrecompiledHeaderFile**|Parámetro **string** opcional.<br/><br/>Especifica un nombre de archivo de encabezado que se va a usar para un archivo de encabezado precompilado. Este archivo también se agregará a **Archivos de inclusión obligatorios** durante la compilación.|
|**PrecompiledHeaderOutputFileDirectory**|Parámetro **string** opcional.<br/><br/>Especifica el directorio del encabezado precompilado generado. Este directorio también se agregará a **Directorios de inclusión adicionales** durante la compilación.|
|**PrecompiledHeaderCompileAs**|Parámetro **string** opcional.<br/><br/>Seleccione la opción de lenguaje de compilación para el archivo de encabezado precompilado.<br/><br/>Use `-x c-header`, `-x c++-header`.|
|**PreprocessorDefinitions**|Parámetro **string[]** opcional.<br/><br/>Define un símbolo de preprocesamiento para el archivo de código fuente.<br/><br/>Use `-D`.|
|**RuntimeLibrary**|Parámetro **string** opcional.<br/><br/>Especifique la biblioteca en tiempo de ejecución para la vinculación.<br/><br/>Use los conmutadores `MSVC /MT`, `/MTd`, `/MD`, `/MDd`.<br/><br/>**MultiThreaded**, hace que la aplicación use la versión estática multiproceso de la biblioteca en tiempo de ejecución.<br/>**MultiThreadedDebug**, define _DEBUG y _MT. Esta opción también hace que el compilador coloque el nombre de la biblioteca LIBCMTD.lib en el archivo .obj, así el vinculador usará LIBCMTD.lib para resolver los símbolos externos.<br/>**MultiThreadedDLL**, hace que la aplicación use la versión específica para multiproceso y la versión específica para DLL de la biblioteca en tiempo de ejecución. Define _MT y _DLL y hace que el compilador sitúe el nombre de la biblioteca MSVCRT.lib en el archivo .obj.<br/>**MultiThreadedDebugDLL**, define _DEBUG, _MT y _DLL y hace que la aplicación use la versión de depuración multiproceso y específica para DLL de la biblioteca en tiempo de ejecución. También hace que el compilador coloque el nombre de la biblioteca MSVCRTD.lib en el archivo .obj.|
|**RuntimeTypeInfo**|Parámetro **bool** opcional.<br/><br/>Agrega código para comprobar los tipos de objetos de C++ en tiempo de ejecución (información de tipo en tiempo de ejecución).<br/><br/>Use `frtti`, `fno-rtti`.|
|**ShowIncludes**|Parámetro **bool** opcional.<br/><br/>Genera una lista de archivos de inclusión con los resultados del compilador.<br/><br/>Use `-H`.|
|**Sources**|Parámetro obligatorio de tipo **ITaskItem[]** .|
|**StrictAliasing**|Parámetro **bool** opcional.<br/><br/>Se da por supuesto que las reglas de alias son las más estrictas. Nunca se dará por supuesto que un objeto de un tipo se encuentra en la misma dirección que un objeto de un tipo distinto.|
|**Sysroot**|Parámetro **string** opcional.<br/><br/>Ruta de carpetas al directorio raíz de encabezados y bibliotecas.|
|**TargetArch**|Parámetro **string** opcional.<br/><br/>Arquitectura de destino.|
|**ThumbMode**|Parámetro **string** opcional.<br/><br/>Cree código que se ejecuta para la microarquitectura Thumb. Solo es válido para la arquitectura ARM.<br/><br/>**Thumb**, genere código Thumb (use `mthumb`).<br/>**ARM**, genere código Arm (use `marm`).<br/>**Disabled**, opción no aplicable a la plataforma elegida.|
|**TrackerLogDirectory**|Parámetro **string** opcional.<br/><br/>Directorio de registro de seguimiento.|
|**TreatWarningAsError**|Parámetro **bool** opcional.<br/><br/>Trata todas las advertencias del compilador como errores.<br/><br/>Para un proyecto nuevo, puede ser mejor usar `/WX` en todas las compilaciones. Resolver todas las advertencias es una forma de asegurar el menor número posible de defectos de código difíciles de encontrar.|
|**UndefinePreprocessorDefinitions**|Parámetro **string[]** opcional.<br/><br/>Especifica la anulación de una o varias definiciones del preprocesador.<br/><br/>Use `-U [macro]`.|
|**UndefineAllPreprocessorDefinitions**|Parámetro **bool** opcional.<br/><br/>Anula la definición de todos los valores del preprocesador definidos previamente.<br/><br/>Use `-undef`.|
|**UseMultiToolTask**|Parámetro **bool** opcional.<br/><br/>Compilación multiprocesador.|
|**UseShortEnums**|Parámetro **bool** opcional.<br/><br/>El tipo de enumeración usa solo los bytes que necesita el conjunto de entrada de valores posibles.|
|**Verbose**|Parámetro **bool** opcional.<br/><br/>Muestra comandos para ejecutar y usar la salida detallada.|
|**WarningLevel**|Parámetro **string** opcional.<br/><br/>Permite seleccionar cómo será de estricto el compilador en cuanto a los errores de código. Las otras marcas deben agregarse directamente a **Opciones adicionales** (consulte `/w`, `/Weverything`).<br/><br/>**TurnOffAllWarnings**, deshabilita todas las advertencias del compilador (use `w`).<br/>**EnableAllWarnings**, habilita todas las advertencias, incluso las deshabilitadas de manera predeterminada (use `Wall`).|

## <a name="see-also"></a>Vea también

[Referencia de tareas](../msbuild/msbuild-task-reference.md)