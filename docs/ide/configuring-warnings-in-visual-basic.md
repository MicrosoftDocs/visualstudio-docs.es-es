---
title: Configurar advertencias en Visual Basic
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Basic], warnings
- run-time errors, warnings
- warnings, configuring
ms.assetid: 99cf4781-bd4d-47b4-91b9-217933509f82
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8cb2cec8258813fa9c93c466afb607ce88acc7e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865971"
---
# <a name="configuring-warnings-in-visual-basic"></a>Configuración de advertencias in Visual Basic

El compilador [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] incluye un conjunto de advertencias sobre código susceptible de provocar errores en tiempo de ejecución. Puede usar esa información para escribir un código mejor, más limpio y rápido con menos errores. Por ejemplo, el compilador generará una advertencia cuando el usuario intente invocar un miembro de una variable de objeto sin asignar, volver de una función sin establecer el valor devuelto, o ejecutar un bloque `Try` con errores en la lógica para detectar excepciones.

 En ocasiones, el compilador proporciona lógica adicional en nombre del usuario para que este pueda centrarse en la tarea en cuestión, en lugar de anticipar posibles errores. En versiones anteriores de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], **Option Strict** se usaba para limitar la lógica adicional que proporciona el compilador de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Configurar advertencias le permite limitar esta lógica de una forma más pormenorizada, en el nivel de las advertencias individuales.

 Es posible que quiera personalizar el proyecto y desactivar algunas advertencias que no afectan a su aplicación, así como convertir otras advertencias en errores. En esta página se explica cómo activar y desactivar las advertencias individuales.

## <a name="turning-warnings-off-and-on"></a>Activación y desactivación de las advertencias
 Hay dos formas diferentes de configurar advertencias: puede configurarlas mediante el **Diseñador de proyectos** o puede usar las opciones del compilador **/warnaserror** y **/nowarn**.

 En la pestaña **Compilar** de la página **Diseñador de proyectos**, puede activar y desactivar las advertencias. Seleccione la casilla **Deshabilitar todas las advertencias** para deshabilitar todas las advertencias; seleccione **Tratar todas las advertencias como errores** para tratar todas las advertencias como errores. Algunas advertencias individuales se pueden alternar como errores o advertencias en la tabla mostrada.

 Si **Option Strict** está establecido en **Desactivado**, las advertencias relacionadas con **Option Strict** no se pueden tratar independientemente unas de otras. Si **Option Strict** está establecido en **Activado**, las advertencias asociadas se tratan como errores, no importa cuál sea su estado. Si **Option Strict** está establecido en **Personalizado** al especificar `/optionstrict:custom` en el compilador de línea de comandos, las advertencias de **Option Strict** se pueden activar o desactivar por separado.

 La opción de línea de comandos **/warnaserror** del compilador también se puede usar para especificar si las advertencias se tratan como errores. Puede agregar una lista delimitada por comas a esta opción para especificar qué advertencias se deben tratar como errores o advertencias usando + o -. En la siguiente tabla, se detallan las posibles opciones.

|Opción de la línea de comandos|Especifica|
| - |---------------|
|`/warnaserror+`|Se tratan todas las advertencias como errores.|
|`/warnsaserror`-|No se tratan las advertencias como errores. Este es el valor predeterminado.|
|`/warnaserror+:<warning list` `>`|Se tratan las advertencias específicas como errores, enumeradas por su número de identificación de error en una lista delimitada por comas.|
|`/warnaserror-:<warning list>`|No se tratan las advertencias específicas como errores, enumeradas por su número de identificación de error en una lista delimitada por comas.|
|`/nowarn`|No se notifican las advertencias.|
|`/nowarn:<warning list>`|No se notifican las advertencias específicas, enumeradas por su número de identificación de error en una lista delimitada por comas.|

 La lista de advertencias contiene los números de identificación de error de las advertencias que deben tratarse como errores, que se pueden usar con las opciones de línea de comandos para activar o desactivar advertencias específicas. Si la lista de advertencias contiene un número no válido, se notifica un error.

## <a name="examples"></a>Ejemplos
 En esta tabla de ejemplos de argumentos de línea de comandos se describe qué hace cada argumento.

|Argumento|Descripción|
|--------------|-----------------|
|`vbc /warnaserror`|Especifica que todas las advertencias se deben tratar como errores.|
|`vbc /warnaserror:42024`|Especifica que la advertencia 42024 se debe tratar como un error.|
|`vbc /warnaserror:42024,42025`|Especifica que las advertencias 42024 y 42025 se deben tratar como errores.|
|`vbc /nowarn`|Especifica que no se debe notificar ninguna advertencia.|
|`vbc /nowarn:42024`|Especifica que no se debe notificar la advertencia 42024.|
|`vbc /nowarn:42024,42025`|Especifica que no se deben notificar las advertencias 42024 y 42025.|

## <a name="types-of-warnings"></a>Tipos de advertencias
 Esta es una lista de advertencias que es posible que quiera tratar como errores.

### <a name="implicit-conversion-warning"></a>Advertencia de conversión implícita
 Se genera para instancias de conversión implícita. No incluyen las conversiones implícitas de un tipo numérico intrínseco a una cadena cuando se usa el operador `&`. De manera predeterminada, está desactivada para nuevos proyectos.

 Id.: 42016

### <a name="late-bound-method-invocation-and-overload-resolution-warning"></a>Advertencia de resolución de sobrecarga e invocación de método enlazada en tiempo de ejecución
 Se genera para instancias de enlace en tiempo de ejecución. De manera predeterminada, está desactivada para nuevos proyectos.

 Id.: 42017

### <a name="operands-of-type-object-warnings"></a>Advertencias de operandos de tipo Object
 Se generan cuando se producen operandos de tipo `Object` que crearían un error con **Option Strict On**. De manera predeterminada, está activada para nuevos proyectos.

 Id.: 42018 y 42019

### <a name="declarations-require-as-clause-warnings"></a>Advertencias de declaraciones que requieren la cláusula "As"
 Se generan cuando una declaración de propiedad, función o variable a la que le falta una cláusula `As` habría creado un error con **Option Strict On**. Las variables que no tienen un tipo asignado se supone que son de tipo `Object`. De manera predeterminada, está activada para nuevos proyectos.

 Id.: 42020 (declaración de variable), 42021 (declaración de función) y 42022 (declaración de propiedad).

### <a name="possible-null-reference-exception-warnings"></a>Advertencias de excepción de referencia nula posible
 Se generan cuando se usa una variable antes de que se le asigne un valor. De manera predeterminada, está activada para nuevos proyectos.

 Id.: 42104, 42030

### <a name="unused-local-variable-warning"></a>Advertencia de variable local sin usar
 Se genera cuando se declara una variable local pero nunca se hace referencia a ella. De manera predeterminada, está activada.

 Id.: 42024

### <a name="access-of-shared-member-through-instance-variable-warning"></a>Advertencia de acceso de miembro compartido mediante una variable de instancia
 Se genera cuando el acceso a un miembro compartido mediante una instancia puede tener efectos secundarios o cuando el acceso a un miembro compartido mediante una variable de instancia no es el lado derecho de una expresión o se pasa como un parámetro. De manera predeterminada, está activada para nuevos proyectos.

 Id.: 42025

### <a name="recursive-operator-or-property-access-warnings"></a>Advertencias de acceso a la propiedad u operador de forma recursiva
 Se genera cuando el cuerpo de una rutina usa el mismo operador o propiedad en que se define. De manera predeterminada, está activada para nuevos proyectos.

 Id.: 42004 (operador), 42026 (propiedad)

### <a name="function-or-operator-without-return-value-warning"></a>Advertencia de función u operador sin valor devuelto
 Se genera cuando la función u operador no tiene un valor devuelto especificado. Esto incluye la omisión de un `Set` a la variable local implícita con el mismo nombre que la función. De manera predeterminada, está activada para nuevos proyectos.

 Id.: 42105 (función), 42016 (operador)

### <a name="overloads-modifier-used-in-a-module-warning"></a>Advertencia de modificador Overloads usado en un módulo
 Se genera cuando `Overloads` se usa en un `Module`. De manera predeterminada, está activada para nuevos proyectos.

 Id.: 42028

### <a name="duplicate-or-overlapping-catch-blocks-warnings"></a>Advertencias de bloques Catch duplicados o superpuestos
 Se genera cuando un bloque `Catch` nunca se alcanza debido a su relación con otros bloques `Catch` que se han definido. De manera predeterminada, está activada para nuevos proyectos.

 Id.: 42029, 42031

## <a name="see-also"></a>Vea también

- [Tipos de error](/dotnet/visual-basic/programming-guide/language-features/error-types)
- [Try...Catch...Finally (instrucción)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)
- [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)
- [/warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)
- [Página Compilación, Diseñador de proyectos (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Advertencias del compilador desactivadas de forma predeterminada](/cpp/preprocessor/compiler-warnings-that-are-off-by-default)