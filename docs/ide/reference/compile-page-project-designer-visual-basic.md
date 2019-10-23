---
title: Página Compilación, Diseñador de proyectos (Visual Basic)
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesCompile
helpviewer_keywords:
- compilation, Visual Basic projects
- compilation, options [Visual Basic]
- compilers, Visual Basic options
- compilation, instructions [Visual Basic]
- compiler options, Visual Basic
- Project Designer, Compile page
- Compile page in Project Designer
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dfe552db89da4cb4d2a9782a1b5d2c8468833baa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654571"
---
# <a name="compile-page-project-designer-visual-basic"></a>Página Compilación, Diseñador de proyectos (Visual Basic)

Use la página **Compilación** del Diseñador de proyectos para especificar las instrucciones de compilación. En esta página también puede especificar opciones avanzadas del compilador o eventos anteriores o posteriores a la compilación.

Para acceder a la página **Compilación**, seleccione un nodo de proyecto (no el nodo **Solución**) en el **Explorador de soluciones**. Después, pulse **Proyecto**, **Propiedades** en la barra de menús. Cuando se muestre el Diseñador de proyectos, haga clic en la pestaña **Compilar**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Configuración y plataforma

Los valores siguientes le permiten seleccionar la configuración y la plataforma que se mostrarán o modificarán.

> [!NOTE]
> Con las configuraciones de compilación simplificadas, el sistema del proyecto determina si se debe compilar una versión de lanzamiento o depuración. Por tanto, no se muestran las listas **Configuración** y **Plataforma**.

**Configuración**

Especifica qué opciones de configuración se mostrarán o modificarán. Los valores son **Depurar** (el valor predeterminado), **Versión** o **Todas las configuraciones**. Para obtener más información, vea [Descripción de las configuraciones de compilación](../../ide/understanding-build-configurations.md) y [Cómo: Crear y editar configuraciones](../../ide/how-to-create-and-edit-configurations.md).

**Plataforma**

Especifica qué configuración de plataforma se mostrará o modificará. Puede especificar **Cualquier CPU** (el valor predeterminado), **x64** o **x86**.

## <a name="compiler-configuration-options"></a>Opciones de configuración del compilador

Las opciones siguientes permiten establecer las opciones de configuración del compilador.

**Ruta de acceso de salida de la compilación**

Especifica la ubicación de los archivos de salida para la configuración de este proyecto. Escriba la ruta de acceso de salida de la compilación en este cuadro, o bien haga clic en el botón **Examinar** para seleccionar una ruta de acceso. Tenga en cuenta que la ruta de acceso es relativa; si especifica una ruta de acceso absoluta, se guardará como relativa. La ruta de acceso predeterminada es bin\Debug\ o bin\Release\\.

Con las configuraciones de compilación simplificadas, el sistema del proyecto determina si se debe compilar una versión de lanzamiento o depuración. El comando **Compilar** del menú **Depuración** (F5) colocará la compilación en la ubicación de depuración independientemente de la **Ruta de acceso de salida** que especifique. En cambio, el comando **Compilar** del menú **Compilar** la coloca en la ubicación que especifique.

**Option Explicit**

Especifica si se permite la declaración implícita de variables. Seleccione **On** para requerir la declaración explícita de variables. Esto hace que el compilador notifique errores si las variables no se declaran antes de usarlas. Seleccione **Off** para permitir la declaración implícita de variables.

Esta opción corresponde a la opción del compilador [/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).

Si un archivo de código fuente contiene una [instrucción Option Explicit](/dotnet/visual-basic/language-reference/statements/option-explicit-statement), el valor `On` u `Off` de la instrucción invalida el valor de **Option Explicit** en la **página Compilar**.

Cuando se crea un proyecto, el valor **Option Explicit** de la **página Compilar** se establece en el valor de la opción **Option Explicit** del cuadro de diálogo **Opciones**. Para ver o cambiar el valor en este cuadro de diálogo, haga clic en **Opciones** en el menú **Herramientas**. En el cuadro de diálogo **Opciones**, expanda **Proyectos y soluciones** y, después, haga clic en **Valores predeterminados de VB**. El valor predeterminado inicial de **Option Explicit** en **Valores predeterminados de VB** es **On**.

Establecer **Option Explicit** en `Off` no suele ser una buena práctica. Podría escribir mal un nombre de variable en una o varias ubicaciones, lo que provocaría resultados inesperados cuando se ejecuta el programa.

**Option Strict**

Especifica si se debe aplicar la semántica estricta de tipos. Cuando **Option Strict** es **On**, las condiciones siguientes producen un error en tiempo de compilación:

- Conversiones de restricción implícitas

- Enlace en tiempo de ejecución

- Tipos implícitos que dan como resultado un tipo `Object`

Los errores de conversión de restricción implícita se producen cuando existe una conversión de tipos de datos implícita que es una conversión de restricción. Para más información, vea [Option Strict (instrucción)](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Conversiones implícitas y explícitas](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) y [Conversiones de ampliación y de restricción](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions).

Un objeto se enlaza en tiempo de ejecución cuando se asigna a una propiedad o un método de una variable que se declara como variable de tipo `Object`. Para más información, vea [Option Strict (instrucción)](/dotnet/visual-basic/language-reference/statements/option-strict-statement) y [Enlace en tiempo de compilación y en tiempo de ejecución](/dotnet/visual-basic/programming-guide/language-features/early-late-binding).

Los errores de tipo de objeto implícito se producen cuando no se puede inferir un tipo adecuado para una variable declarada, por lo que se infiere un tipo de `Object`. Esto se produce principalmente cuando se usa una instrucción `Dim` para declarar una variable sin usar una cláusula `As` y `Option Infer` está desactivado. Para más información, vea [Option Strict (instrucción)](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Option Infer (instrucción)](/dotnet/visual-basic/language-reference/statements/option-infer-statement) y la [Especificación del lenguaje Visual Basic](/dotnet/visual-basic/reference/language-specification).

La opción **Option Strict** corresponde a la opción del compilador [/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).

Si un archivo de código fuente contiene una [instrucción Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement), el valor `On` u `Off` de la instrucción invalida el valor de **Option Strict** en la **página Compilar**.

Cuando se crea un proyecto, el valor **Option Strict** de la **página Compilar** se establece en el valor de la opción **Option Strict** del cuadro de diálogo **Opciones**. Para ver o cambiar el valor en este cuadro de diálogo, haga clic en **Opciones** en el menú **Herramientas**. En el cuadro de diálogo **Opciones**, expanda **Proyectos y soluciones** y, después, haga clic en **Valores predeterminados de VB**. El valor predeterminado inicial de **Option Strict** en **Valores predeterminados de VB** es **Off**.

**Advertencias individuales de Option Strict**

En la sección **Configuraciones de advertencias** de la **página Compilar** se incluyen valores que se corresponden con las tres condiciones que producen un error en tiempo de compilación cuando `Option Strict` está activado. Estas opciones son las siguientes:

- **Conversión implícita**

- **Enlace en tiempo de ejecución; la llamada podría generar un error en tiempo de ejecución**

- **Tipo implícito; se supone el objeto**

Al establecer **Option Strict** en **On**, estos tres valores de configuración de advertencias se establecen en **Error**. Al establecer **Option Strict** en **Off**, las tres opciones se establecen en **None**.

Puede cambiar individualmente cada valor de configuración de advertencia por **None**, **Warning** o **Error**. Si se establecen las tres opciones de configuración de advertencia en **Error**, `On` aparece en el cuadro `Option strict`. Si se establecen las tres en **None**, `Off` aparece en este cuadro. Para cualquier otra combinación de estas opciones, aparece **(personalizado)** .

**Option Compare**

Especifica el tipo de comparación de cadena que se va a usar. Seleccione **Binario** para indicar al compilador que use comparaciones de cadenas binarias que distingan mayúsculas de minúsculas. Seleccione **Texto** para usar comparaciones de cadenas de texto que no distingan mayúsculas de minúsculas específicas de la configuración regional.

Esta opción corresponde a la opción del compilador [/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).

Si un archivo de código fuente contiene una [instrucción Option Compare](/dotnet/visual-basic/language-reference/statements/option-compare-statement), el valor `Binary` u `Text` de la instrucción invalida el valor de **Option Compare** en la **página Compilar**.

Cuando se crea un proyecto, el valor **Option Compare** de la **página Compilar** se establece en el valor de la opción **Option Compare** del cuadro de diálogo **Opciones**. Para ver o cambiar el valor en este cuadro de diálogo, haga clic en **Opciones** en el menú **Herramientas**. En el cuadro de diálogo **Opciones**, expanda **Proyectos y soluciones** y, después, haga clic en **Valores predeterminados de VB**. El valor predeterminado inicial de **Option Compare** en **Valores predeterminados de VB** es **Binario**.

**Option Infer**

Especifica si se permite la inferencia de tipo de variable local en las declaraciones de variables. Seleccione **On** para permitir el uso de la inferencia de tipo de variable local. Seleccione **Off** para bloquear la inferencia de tipo de variable local.

Esta opción corresponde a la opción del compilador [/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).

Si un archivo de código fuente contiene una [instrucción Option Infer](/dotnet/visual-basic/language-reference/statements/option-infer-statement), el valor `On` u `Off` de la instrucción invalida el valor de **Option Infer** en la **página Compilar**.

Cuando se crea un proyecto, el valor **Option Infer** de la **página Compilar** se establece en el valor de la opción **Option Infer** del cuadro de diálogo **Opciones**. Para ver o cambiar el valor en este cuadro de diálogo, haga clic en **Opciones** en el menú **Herramientas**. En el cuadro de diálogo **Opciones**, expanda **Proyectos y soluciones** y, después, haga clic en **Valores predeterminados de VB**. El valor predeterminado inicial de **Option Infer** en **Valores predeterminados de VB** es **On**.

**CPU de destino**

Especifica el procesador que será el destino del archivo de salida. Especifique **x86** para cualquier procesador compatible con Intel de 32 bits, **x64** para cualquier procesador compatible con Intel de 64 bits, **ARM** para procesadores ARM o **Cualquier CPU** para especificar que se aceptan todos los procesadores. **Cualquier CPU** es el valor predeterminado para los proyectos nuevos, ya que permite que la aplicación se ejecute en el mayor número de tipos de hardware.

Para más información, vea [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

**Preferencia de 32 bits**

Si está seleccionada la casilla **Preferencia de 32 bits**, la aplicación se ejecuta como una aplicación de 32 bits en versiones de 32 bits y 64 bits de Windows. En caso contrario, la aplicación se ejecuta como una aplicación de 32 bits en versiones de 32 bits de Windows, y como una aplicación de 64 bits en versiones de 64 bits de Windows.

Ejecutar una aplicación como de 64 bits duplica el tamaño de puntero, y puede provocar problemas de compatibilidad con las bibliotecas que son exclusivamente de 32 bits. Tiene sentido ejecutar una aplicación como de 64 bits solo si se ejecuta significativamente más rápido o necesita más de 4 GB de memoria.

Esta casilla solo está disponible si se cumplen todas las condiciones siguientes:

- En la **página Compilar**, la lista **CPU de destino** se establece en **Cualquier CPU**.

- En la **Página de aplicación**, la lista **Tipo de aplicación** especifica que el proyecto es una aplicación.

- En la **Página de aplicación**, la lista **Marco de trabajo de destino** especifica .NET Framework 4.5.

**Configuraciones de advertencias**

En esta tabla se enumeran las condiciones de compilación y el correspondiente nivel de notificación de **Ninguno**, **Advertencia** o **Error** para cada una.

De forma predeterminada, todas las advertencias del compilador se agregan a la lista de tareas durante la compilación. Seleccione **Deshabilitar todas las advertencias** para indicar al compilador que no emita advertencias ni errores. Seleccione **Tratar todas las advertencias como errores** si quiere que el compilador trate las advertencias como errores que se deben corregir.

**Deshabilitar todas las advertencias**

Especifica si se debe permitir que el compilador emita notificaciones como se especifica en la tabla **Condición y notificación** descrita anteriormente en este documento. Esta casilla se encuentra desactivada de forma predeterminada. Active esta casilla para indicar al compilador que no emita advertencias ni errores.

Esta opción corresponde a la opción del compilador [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).

**Tratar todas las advertencias como errores**

Especifica cómo tratar las advertencias. De forma predeterminada, esta casilla está desactivada, por lo que todas las notificaciones de advertencias permanecen establecidas en **Advertencia**. Active esta casilla para cambiar todas las notificaciones de advertencia a **Error**.

Esta opción solo está disponible si **Deshabilitar todas las advertencias** está desactivada.

**Generar archivo de documentación XML**

Especifica si se debe generar o no información de documentación. De forma predeterminada, esta casilla está activada para indicar al compilador que genere información de documentación y la incluya en un archivo XML. Desactive esta casilla para indicar al compilador que no cree la documentación.

Esta opción corresponde a la opción del compilador [/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).

**Registrar para interoperabilidad COM**

Especifica si la aplicación administrada expondrá un objeto COM (un contenedor CCW) que permite a un objeto COM interactuar con la aplicación.

De forma predeterminada, esta casilla está desactivada, lo que especifica que la aplicación no permitirá la interoperabilidad COM. Active esta casilla para permitir la interoperabilidad COM.

Esta opción no está disponible para los proyectos de aplicación Windows o de aplicación de consola.

**Eventos de compilación**

Haga clic en este botón para tener acceso al cuadro de diálogo **Eventos de compilación**. Use este cuadro de diálogo para especificar las instrucciones de configuración anteriores y posteriores a la compilación para el proyecto. Este cuadro de diálogo solo se aplica a proyectos de Visual Basic. Para más información, vea [Eventos de compilación (Cuadro de diálogo) (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md).

**Opciones de compilación avanzadas**

Haga clic en este botón para tener acceso al cuadro de diálogo **Configuración de compilador avanzada**. Use el cuadro de diálogo **Configuración de compilador avanzada** para especificar las propiedades de configuración de compilación avanzada del proyecto. Este cuadro de diálogo solo se aplica a proyectos de Visual Basic. Para más información, vea [Configuración de compilador avanzada (Cuadro de diálogo, Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).

## <a name="see-also"></a>Vea también

- [Cómo: Especificar eventos de compilación (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Compilador de línea de comandos de Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Cómo: Crear y editar configuraciones](../../ide/how-to-create-and-edit-configurations.md)