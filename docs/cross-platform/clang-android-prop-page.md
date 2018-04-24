---
title: Propiedades de proyectos Clang (C++ para Android) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 663140ea-a568-472b-a79a-dfea8818e06a
author: corob
ms.author: mblome
manager: douge
f1_keywords:
- VC.Project.VCClangCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCClangCompilerTool.DebugInformationFormat
- VC.Project.VCClangCompilerTool.ObjectFile
- VC.Project.VCClangCompilerTool.WarningLevel
- VC.Project.VCClangCompilerTool.WarnAsError
- VC.Project.VCClangCompilerTool.Verbose
- VC.Project.VCClangCompilerTool.Optimization
- VC.Project.VCClangCompilerTool.StrictAliasing
- VC.Project.VCClangCompilerTool.OmitFramePointers
- VC.Project.VCClangCompilerTool.ExceptionHandling
- VC.Project.VCClangCompilerTool.EnableFunctionLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.FloatABI
- VC.Project.VCClangCompilerTool.BufferSecurityCheck
- VC.Project.VCClangCompilerTool.PIC
- VC.Project.VCClangCompilerTool.UseShortEnums
- VC.Project.VCClangCompilerTool.RuntimeTypeInfo
- VC.Project.VCClangCompilerTool.CLanguageStandard
- VC.Project.VCClangCompilerTool.CppLanguageStandard
- VC.Project.VCClangCompilerTool.PreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefineAllPreprocessorDefinitions
- VC.Project.VCClangCompilerTool.ShowIncludes
- VC.Project.VCClangCompilerTool.PrecompiledHeader
- VC.Project.VCClangCompilerTool.PrecompiledHeaderFile
- VC.Project.VCClangCompilerTool.PrecompiledHeaderOutputFileDirectory
- VC.Project.VCClangCompilerTool.PrecompiledHeaderCompileAs
- VC.Project.VCClangCompilerTool.CompileAs
- VC.Project.VCClangCompilerTool.ForcedIncludeFiles
- VC.Project.VCClangCompilerTool.MultiProcessorCompilation
- vc.project.AdditionalOptionsPage
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 8a1fd92a41f145e097615bea4434ea80fd592416
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="clang-project-properties-android-c"></a>Propiedades de proyectos Clang (C++ para Android)

Property | Description | Opciones
--- | ---| ---
Directorios de inclusión adicionales | Especifica uno o más directorios que se agregarán a la ruta de acceso de inclusión; si hay más de uno, sepárelos mediante punto y coma. (-I[ruta_de_acceso]).
Formato de información de depuración | Especifica el tipo de información de depuración generado por el compilador. | **Ninguno**: no produce información de depuración, por lo que la compilación puede ser más rápida.<br>**Información de depuración completa (DWARF2)**: genera información de depuración DWARF2.<br>**Información de número de línea**: genera únicamente información de número de línea.<br>
Nombre de archivo objeto | Especifica un nombre para reemplazar el nombre del archivo objeto predeterminado. Puede ser un nombre de archivo o de directorio. (/Fo[nombre]).
Nivel de advertencia | Permite seleccionar cómo será de estricto el compilador en cuanto a los errores de código.  Las otras marcas deben agregarse directamente a Opciones adicionales. (/w, /Weverything). | **Desactivar todas las advertencias**: deshabilita todas las advertencias del compilador.<br>**Habilitar todas las advertencias**: habilita todas las advertencias, incluidas las deshabilitadas de manera predeterminada.<br>
Tratar advertencias como errores | Trata todas las advertencias del compilador como errores. Para un proyecto nuevo, puede ser mejor usar /WX en todas las compilaciones. Resolver todas las advertencias es una forma de asegurar el menor número posible de defectos de código difíciles de encontrar.
Habilitar modo detallado | Muestra comandos para ejecutar y usar la salida detallada.
Optimización | Especifica el nivel de optimización de la aplicación. | **Personalizado**: optimización personalizada.<br>**Deshabilitado**: deshabilita la optimización.<br>**Minimizar tamaño**: optimiza el tamaño.<br>**Maximizar velocidad**: optimiza la velocidad.<br>**Optimización completa**: optimizaciones costosas.<br>
Creación de alias estricta | Se da por supuesto que las reglas de alias son las más estrictas.  Nunca se dará por supuesto que un objeto de un tipo se encuentra en la misma dirección que un objeto de un tipo distinto.
Omitir puntero de marcos | Suprime la creación de punteros de marcos en la pila de llamadas.
Habilitar excepciones de C++ | Especifica el modelo de control de excepciones que usará el compilador. | **No**: deshabilita el control de excepciones.<br>**Sí**: habilita el control de excepciones.<br>**Desenredar tablas**: genera los datos estáticos necesarios, pero no afecta al código generado.<br>
Habilitar vinculación en el nivel de función | Permite que el compilador empaquete las funciones individuales con formato de funciones empaquetadas (COMDATs). Es necesario para que funcione Editar y continuar.     (ffunction-sections).
Habilitar vinculación en el nivel de datos | Permite que las optimizaciones del enlazador quiten datos no usados al emitir cada elemento de datos en una sección distinta.
Habilitar SIMD(Neon) avanzado | Habilita la generación de código para hardware de punto flotante NEON. Esto solo es válido para la arquitectura ARM.
ABI de punto flotante | Opción de selección para elegir ABI de punto flotante. | **Soft**: hace que el compilador genere una salida que contiene llamadas de biblioteca para operaciones de punto flotante.<br>**SoftFP**: permite generar código con instrucciones de punto flotante de hardware, pero sigue usando las convenciones de llamadas flotantes de software (Soft).<br>**Hard**: permite generar instrucciones de punto flotante y usa convenciones de llamada específicas de FPU.<br>
Comprobación de seguridad | La comprobación de seguridad ayuda a detectar desbordamientos del búfer de pila, un ataque común contra la seguridad de un programa. (fstack-protector). | **Deshabilitar comprobación de seguridad**: deshabilita la comprobación de seguridad.<br>**Habilitar comprobación de seguridad**: habilita la comprobación de seguridad. (fstack-protector).<br>
Código independiente de posición | Genera código independiente de posición (PIC) para usarlo en una biblioteca compartida.
Usar enumeraciones breves | El tipo de enumeración usa solo los bytes que necesita el conjunto de entrada de valores posibles.
Habilitar información de tipo en tiempo de ejecución | Agrega código para comprobar los tipos de objetos de C++ en tiempo de ejecución (información de tipo en tiempo de ejecución).     (frtti, fno-rtti).
Estándar de lenguaje C | Determina el estándar de lenguaje C. | **Predetermiado**<br>**C89**: estándar de lenguaje C89.<br>**C99**: estándar de lenguaje C99.<br>**C11**: estándar de lenguaje C11.<br>**C99 (dialecto GNU)**: estándar de lenguaje C99 (dialecto GNU).<br>**C11 (dialecto GNU)**: estándar de lenguaje C11 (dialecto GNU).<br>
Estándar de lenguaje C++ | Determina el estándar de lenguaje C++. | **Predetermiado**<br>**C++03**: estándar de lenguaje C++03.<br>**C++11**: estándar de lenguaje C++11.<br>**C++14**: estándar de lenguaje C++14.<br>**C++03 (dialecto GNU)**: estándar de lenguaje C++03 (dialecto GNU).<br>**C++11 (dialecto GNU)**: estándar de lenguaje C++11 (dialecto GNU).<br>**C++14 (dialecto GNU)**: estándar de lenguaje C++14 (dialecto GNU).<br>
Definiciones de preprocesador | Define un símbolo de preprocesamiento para el archivo de código fuente. (-D).
Anular definiciones del preprocesador | Especifica la anulación de una o varias definiciones del preprocesador.  (-U [macro]).
Anular todas las definiciones del preprocesador | Anula la definición de todos los valores del preprocesador definidos previamente.  (-undef).
Mostrar inclusiones | Genera una lista de archivos de inclusión con los resultados del compilador.  (-H).
Encabezado precompilado | Crear o usar encabezado precompilado: habilita la creación o el uso de un encabezado precompilado durante la compilación. | **Usar**: se usa un encabezado precompilado.<br>**No usar encabezados precompilados**: no se usa ningún encabezado precompilado.<br>
Archivo de encabezado precompilado | Especifica un nombre de archivo de encabezado que se va a usar para un archivo de encabezado precompilado. Este archivo también se agregará a "Archivos de inclusión obligatorios" durante la compilación.
Directorio de archivos de salida del encabezado precompilado | Especifica el directorio del encabezado precompilado generado. Este directorio también se agregará a "Directorios de inclusión adicionales" durante la compilación.
Compilar encabezado precompilado como | Seleccione la opción de lenguaje de compilación para el archivo de encabezado precompilado (-x c-header, -x c++-header). | **Compilar como código de C**: compila como código de C.<br>**Compilar como código de C++**: compila como código de C++.<br>
Compilar como | Permite seleccionar la opción de lenguaje de compilación para los archivos .c y .cpp.  En la opción "Predeterminado", la detección se realizará en función de la extensión ".c" o ".cpp". (-x c, -x c++). | **Predeterminado**: opción predeterminada.<br>**Compilar como código de C**: compila como código de C.<br>**Compilar como código de C++**: compila como código de C++.<br>
Archivos de inclusión obligatorios | Uno o más archivos de inclusión obligatorios.     (-include [nombre]).
Compilación multiprocesador | Compilación multiprocesador.
Opciones adicionales | Opciones adicionales.
