---
title: Cambios de código admitidos (C++) | Microsoft Docs
ms.date: 02/18/2020
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C++ language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C++], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: af6c0d88dd230bee768641905e200f1f47749d77
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2020
ms.locfileid: "77629591"
---
# <a name="supported-code-changes-c"></a>Cambios admitidos en el código (C++)
Editar y continuar para C++ proyectos controla la mayoría de los tipos de cambios de código. Sin embargo, algunos cambios no se pueden aplicar durante la ejecución de programa. Para aplicar estos cambios, debe detener la ejecución y compilar una versión nueva del código.

 Vea [Editar y continuar (C++)](../debugger/edit-and-continue-visual-cpp.md) para obtener información sobre cómo trabajar con editar y C++ continuar para en Visual Studio.

## <a name="BKMK_Requirements"></a> Requisitos
### <a name="build-settings-project--properties"></a>Configuración de compilación (propiedades del proyecto >):
  1. **Formato deC++ información de depuración de > General de C/>** : base de datos de programa para editar y continuar (`/ZI`)
  2. **Generación deC++ código de C/> > Habilitar recompilación mínima**: sí (`/Gm`)
  3. **Vinculador > General > habilitar vinculación incremental**: sí (`/INCREMENTAL`)

     Cualquier configuración de vinculador incompatible (como `/SAFESEH`, o `/OPT:`...) debería producir una advertencia _LNK4075_ durante la compilación.  
     Ejemplo: `LINK : warning LNK4075: ignoring '/INCREMENTAL' due to '/OPT:ICF' specification`

### <a name="debugger-settings-debug--options--general"></a>Configuración del depurador (depurar opciones de > > General):
  - Habilitar la opción Editar y continuar nativa

     Cualquier configuración incompatible del compilador o del vinculador produce un error durante la edición y continuación.  
     Ejemplo: `Edit and Continue : error  : ‘file.cpp’ in ‘MyApp.exe’ was not compiled with Edit and Continue enabled. Ensure that the file is compiled with the Program Database for Edit and Continue (/ZI) option.`

## <a name="BKMK_Unsupported_changes"></a> Cambios no admitidos
 Los siguientes cambios deC++ C/no se pueden aplicar durante una sesión de depuración. Si realiza cualquiera de estos cambios y, a continuación, intenta aplicar cambios en el código, aparece un mensaje de error o advertencia en la ventana **salida** .

- La mayoría de los cambios en datos globales o estáticos.

- Cambios en los ejecutables copiados de otro equipo y no compilados localmente.

- Cambios en un tipo de datos que afectan al diseño de un objeto, por ejemplo los miembros de datos de una clase.

- Agregar más de 64 KB de código o datos nuevos.

- Agregar variables que requieran un constructor en un punto anterior al puntero de instrucción.

- Cambios que afecten a una sección del código que requiera una inicialización en tiempo de ejecución.

- Agregar controladores de excepciones, en algunos casos.

- Cambios en archivos de recursos.

- Cambios en el código de archivos de solo lectura.

- Cambios en código sin un archivo PDB correspondiente.

- Cambios en código que no tiene un archivo de objeto.

* Modificar las expresiones lambda que:
  - Tener un miembro estático o global.
  - Se pasan a una función STD::. Esto produce una infracción de ODR genuina y resultados en C1092.

- Editar y continuar no vuelve a actualizar las bibliotecas estáticas. Si realiza un cambio en una biblioteca estática, la ejecución continuará con la versión anterior y no se emitirá ninguna advertencia.

## <a name="BKMK_Unsupported_scenarios"></a> Escenarios no admitidos
 La opción Editar y continuar de C/C++ no se encuentra disponible en los siguientes escenarios de depuración:

- Depurar aplicaciones nativas compiladas con [/Zo (Mejorar la depuración optimizada)](/cpp/build/reference/zo-enhance-optimized-debugging)

- En las versiones de Visual Studio anteriores a Visual Studio 2015 Update 1, depurar aplicaciones o componentes de UWP. A partir de Visual Studio 2015 Update 1, puede usar editar y continuar en aplicaciones C++ para UWP y aplicaciones de DirectX, ya que ahora admite el modificador de `/ZI` compilador con el modificador `/bigobj`. También puede usar Editar y continuar con binarios compilados con el modificador `/FASTLINK` .

- Depurar aplicaciones de la tienda 8/8.1. Estos proyectos utilizan el conjunto de herramientas VC 120 y elC++ modificador C/`/bigobj`. Editar y continuar con `/bigobj` solo se admite en el conjunto de herramientas VC 140.

- Depurar en Windows 98.

- Depuración en modo mixto (nativa o administrada).

- Depuración de JavaScript.

- Depuración de SQL.

- Depurar un archivo de volcado de memoria.

- Edición de código tras una excepción no controlada, cuando no se ha seleccionado la opción **Desenredar la pila de llamadas de las excepciones no controladas** .

- Depure una aplicación utilizando **Adjuntar a** en lugar de ejecutar la aplicación desde la opción **Iniciar** del menú **Depurar** .

- Depuración de código optimizado.

- Depurar una versión anterior del código cuando no ha sido posible generar una nueva versión debido a errores de compilación.

- Usar una ruta de acceso del compilador personalizado (*cl. exe*). Por motivos de seguridad, para volver a compilar un archivo durante editar y continuar, Visual Studio siempre usa el compilador instalado. Si usa una ruta de acceso del compilador personalizada (por ejemplo, a través de una variable de `$(ExecutablePath)` personalizada en el archivo de `*.props`), se muestra una advertencia y Visual Studio recurre al uso del compilador instalado de la misma versión o arquitectura.

- Sistema de compilación de FASTBuild. FASTBuild no es compatible actualmente con el modificador de compilador "habilitar recompilación mínima (`/Gm`)", por lo que no se admite editar y continuar.

- Arquitecturas heredadas/conjuntos de herramientas VC. Con el conjunto de herramientas VC 140, el depurador predeterminado admite editar y continuar con aplicaciones x86 y x64. Los conjuntos de herramientas heredados solo admiten aplicaciones x86. Los conjuntos de herramientas anteriores a VC 120 deben usar el depurador heredado mediante la comprobación de_las opciones de Depuración > > General >_ usar el modo de compatibilidad nativa "para poder usar editar y continuar.

## <a name="BKMK_Linking_limitations"></a> Limitaciones de la vinculación

### <a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Opciones del vinculador que deshabilitan Editar y continuar
 Las siguientes opciones del vinculador deshabilitan Editar y continuar:

- La definición de **/OPT:REF**, **/OPT:ICF**o **/INCREMENTAL:NO** deshabilita Editar y continuar con la advertencia siguiente:  
     `LINK : warning LNK4075: ignoring /EDITANDCONTINUE due to /OPT specification`

- La configuración de **/Order**, **/Release**o **/Force** deshabilita editar y continuar con la siguiente ADVERTENCIA:  
     `LINK : warning LNK4075: ignoring /INCREMENTAL due to /option specification`

- La configuración de alguna opción que impida la creación de un archivo de base de datos de programa (.pdb) deshabilita Editar y continuar sin ninguna advertencia específica.

### <a name="BKMK_Auto_relinking_limitations"></a> Volver a vincular automáticamente las limitaciones
 De forma predeterminada, Editar y continuar vuelve a vincular el programa al final de una sesión de depuración para crear un ejecutable actualizado.

 Editar y continuar no puede volver a vincular el programa si realiza la depuración desde una ubicación distinta de la ubicación de compilación original. Un mensaje le indica que debe recompilar el programa manualmente.

 Editar y continuar no recompila bibliotecas estáticas. Si realiza cambios en una biblioteca estática mediante Editar y continuar, deberá recompilar la biblioteca manualmente y volver a vincular las aplicaciones utilizando la biblioteca.

 Editar y continuar no invoca pasos de compilación personalizada. Si el programa usa pasos de compilación personalizada, conviene recompilarlo manualmente para que se pueda llamar a dichos pasos. En ese caso, puede deshabilitarse la revinculación después de Editar y continuar para asegurarse de que se le pide confirmación antes de recompilar manualmente.

 **Para deshabilitar la revinculación después de Editar y continuar**

1. En el menú **Depurar** , elija **Opciones y configuración**.

2. En el cuadro de diálogo **Opciones** , bajo el nodo **Depuración** , seleccione el nodo **Editar y continuar** .

3. Desactive la casilla **Volver a vincular cambios de códigos después de depurar** .

## <a name="BKMK_Precompiled_header_limitations"></a>Limitaciones de los encabezados precompilados
 De forma predeterminada, Editar y continuar carga y procesa los encabezados precompilados en segundo plano con el fin de acelerar el proceso de los cambios en el código. La carga de encabezados precompilados requiere la asignación de memoria física, lo cual puede constituir un problema si la compilación se lleva a cabo en un equipo con memoria RAM limitada. Es posible saber si esto causará problemas mediante la utilización del Administrador de tareas de Windows para determinar la cantidad de memoria física disponible mientras se lleva a cabo la depuración. Si esta cantidad es mayor que el tamaño de los encabezados precompilados, Editar y continuar no debería presentar ningún problema. Si es inferior al tamaño de los encabezados precompilados, puede evitar que Editar y continuar cargue dichos encabezados en segundo plano.

 **Para deshabilitar la carga en segundo plano de los encabezados precompilados para Editar y continuar**

1. En el menú **Depurar** , elija **Opciones y configuración**.

2. En el cuadro de diálogo **Opciones** , bajo el nodo **Depuración** , seleccione el nodo **Editar y continuar** .

3. Desactive la casilla **Permitir compilación previa** .

## <a name="BKMK_IDL_attribute_limitations"></a>Limitaciones de los atributos IDL
 Con el modo Editar y continuar no se pueden regenerar los archivos de definición de interfaz (IDL). Por tanto, los cambios realizados en los atributos IDL no se reflejarán durante la depuración. Para ver el resultado de los cambios en los atributos IDL, debe detener la depuración y recompilar la aplicación. Editar y continuar no genera ningún error o advertencia si cambian los atributos IDL. Para obtener más información, vea [Atributos IDL](/cpp/windows/idl-attributes).

## <a name="BKMK_Diagnosing_issues"></a>Diagnóstico de problemas
 Si el escenario no se ajusta a ninguna de las condiciones mencionadas anteriormente, puede recopilar más detalles estableciendo el siguiente valor DWORD del registro:
 1. Abra un Símbolo del sistema para desarrolladores.
 2. Ejecute el siguiente comando:  
     `VsRegEdit.exe set “C:\Program Files (x86)\Microsoft Visual Studio\[Version]\[YOUR EDITION]” HKCU Debugger NativeEncDiagnosticLoggingLevel DWORD 1`

 Al establecer este valor en el inicio de una sesión de depuración, los distintos componentes de editar y continuar Spew el registro detallado en el panel **Depuración** > de **ventana de salida** .

## <a name="see-also"></a>Consulte también
- [Editar y continuar (C++)](../debugger/edit-and-continue-visual-cpp.md)
