---
title: General, depuración, cuadro de diálogo Opciones | Microsoft Docs
ms.date: 11/09/2018
ms.topic: reference
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0347e2948538b8d4149ce6228656d190c5f972a6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689309"
---
# <a name="general-debugging-options"></a>Opciones generales de depuración

Para establecer las opciones del depurador de Visual Studio, seleccione **herramientas** > **opciones**y en **depuración** Active o desactive las casillas junto a la  **General** opciones. Puede restaurar toda la configuración predeterminada con **herramientas** > **importar y exportar configuraciones** > **restablecer todas las configuraciones**. Para restablecer un subconjunto de valores, guarde la configuración con la **importar y exportar configuraciones** antes de realizar los cambios que se va a probar, a continuación, importar la configuración guardada más adelante.

Puede establecer las siguientes **General** opciones:

**Preguntar antes de eliminar todos los puntos de interrupción**: requiere una confirmación antes de completar la **eliminar todos los puntos de interrupción** comando.

**Interrumpir todos los procesos cuando se interrumpa uno**: interrumpe simultáneamente todos los procesos al que está asociado el depurador cuando se produce una interrupción.

**Interrumpir cuando las excepciones crucen AppDomain o los límites administrados o nativos**: en la depuración administrada o en modo mixto, common language runtime puede capturar excepciones que atraviesen los límites del dominio de aplicación o los límites administrados o nativos cuando lo siguiente las condiciones son verdaderas:

1. Cuando el código nativo llama al código administrado utilizando la interoperabilidad COM y el código administrado produce una excepción. Consulte [Introducción a la interoperabilidad COM](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Cuando el código administrado que se ejecuta en el dominio de aplicación 1 llama al código administrado en el dominio de aplicación 2 y este último produce una excepción. Consulte [Programar con dominios de aplicación](/dotnet/articles/framework/app-domains/index).

3. Cuando el código llama una función mediante la reflexión y que la función produce una excepción. Consulte [reflexión](/dotnet/framework/reflection-and-codedom/reflection).

En condiciones de 2 y 3, a veces detecta la excepción mediante código administrado en `mscorlib` en lugar de por common language runtime. Esta opción no afecta a la interrupción en excepciones detectadas por `mscorlib`.

**Habilitar la depuración de nivel de dirección**: habilita las características avanzadas para la depuración en el nivel de dirección (el **desensamblado** ventana, el **registra** ventana y los puntos de interrupción de dirección).

- **Mostrar desensamblado si el origen no está disponible**: muestra automáticamente el **desensamblado** ventana cuando se depura código para el que el origen está disponible.

**Habilitar filtros de punto de interrupción**: le permite establecer filtros en los puntos de interrupción, por lo que afectará solo procesos específicos, subprocesos o equipos.

**Usar la nueva aplicación auxiliar de excepciones**: permite que la aplicación auxiliar de excepciones (Visual Studio 2017) que reemplaza el Asistente de excepciones.

> [!NOTE]
> Para código administrado, esta opción se denominaba anteriormente **habilitar el Asistente de excepciones** .

**Habilitar Solo mi código**: el depurador muestra y los pasos en el código de usuario ("mi código"), omitiendo el código del sistema y otro código optimizado o que no tenga símbolos de depuración.

- **Advertir si no hay código de usuario al iniciar (solo administrado)**: cuando se inicia la depuración con sólo mi código habilitada, esta opción le advierte si no hay ningún código de usuario ("mi código").

**Habilitar .NET Framework del origen de ejecución paso a paso**: permite al depurador paso a paso por el código fuente de .NET Framework. Al habilitar esta opción deshabilita automáticamente solo mi código. Símbolos de .NET framework se descargarán a una ubicación de caché. Cambiar la ubicación de caché con la **opciones** cuadro de diálogo, **depuración** categoría, **símbolos** página.

**Saltar propiedades y operadores (solo administrado)**: evita que el depurador entre en las propiedades y operadores en código administrado.

**Habilitar evaluación de propiedades y otras llamadas a función implícitas**: llama activa la evaluación automática de propiedades y funciones implícitas en ventanas de variables y **Inspección rápida** cuadro de diálogo.

- **Llamar a la función de conversión de cadenas en objetos en ventanas de variables (C# y solo JavaScript)**: ejecuta una llamada de conversión implícita de cadena al evaluar objetos en ventanas de variables. El resultado se muestra como una cadena en lugar del nombre de tipo. Solo se aplica mientras se lleva a cabo la depuración en código C#. Este valor puede reemplazarse por el atributo DebuggerDisplay (consulte [utilizando el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).

**Habilitar compatibilidad de servidor de origen**: indica al depurador de Visual Studio para obtener archivos de origen de los servidores de origen que implementan la SrcSrv (`srcsrv.dll`) protocol. Team Foundation Server y las herramientas de depuración para Windows son dos servidores de origen que implementan el protocolo. Para obtener más información sobre la configuración de SrcSrv, vea el [SrcSrv](/windows-hardware/drivers/debugger/srcsrv) documentación. Además, consulte [especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Dado que la lectura de archivos *.pdb* puede ejecutar código arbitrario en los archivos, asegúrese de que el servidor es de confianza.

- **Imprimir los mensajes de diagnóstico del servidor de origen a la ventana de salida**: cuando está habilitada la compatibilidad con servidor de origen, esta configuración activa la presentación de diagnóstico.

- **Permitir servidor de origen para ensamblados de confianza parcial (solo administrado)**: cuando está habilitada la compatibilidad con servidor de origen, esta configuración invalida el comportamiento predeterminado de no recuperar los orígenes para los ensamblados de confianza parcial.

- **Siempre se ejecutan comandos de servidor de origen de confianza sin preguntar**: cuando se habilita la compatibilidad del servidor de origen, esta configuración invalida el comportamiento predeterminado de preguntar al ejecutar un comando que no se confía.

**Habilitar la compatibilidad con Sourcelink**: indica al depurador de Visual Studio para descargar los archivos de origen para *.pdb* archivos que contienen información de vínculo de origen. Para obtener más información sobre el vínculo de origen, consulte el [especificación de vinculación de código fuente](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

> [!IMPORTANT]
>  Como origen de vínculo descargará los archivos mediante http o https, asegúrese de que confía el *.pdb* archivo.

- **Retroceso a autenticación de Git Credential Manager para todas las solicitudes de Source Link**: compatibilidad de vínculo de origen cuando está habilitada, y una solicitud de vínculo de origen se produce un error de autenticación, Visual Studio, a continuación, llama al administrador de credenciales de Git.

**Resaltar la línea de puntos de interrupción y la instrucción actual (solo C++)**: cuando el depurador resalta un punto de interrupción o la instrucción actual, resalta toda la línea.

**Requieren archivos de origen para ajustarse exactamente a la versión original**: indica al depurador que compruebe que un archivo de origen coincide con la versión del código fuente utilizado para generar el archivo ejecutable que se está depurando. Cuando la versión no coincide, se le pedirá que busque un origen correspondiente. Si no se encuentra este archivo, el código fuente no se mostrará durante la depuración.

**Redirigir el texto de la ventana de salida a la ventana Inmediato**: envía todos los mensajes del depurador que normalmente la **salida** ventana a la **inmediato** ventana en su lugar.

**Mostrar la estructura de los objetos en ventanas de variables**: desactiva todas las personalizaciones de la vista de estructura de objeto. Para obtener más información acerca de las personalizaciones de vistas, consulte [crear vistas personalizadas de objetos administrados](../debugger/create-custom-views-of-dot-managed-objects.md).

**Suprimir optimización JIT al cargar el módulo (solo administrado)**: deshabilita la optimización JIT de código administrado cuando se carga un módulo JIT mientras el depurador está conectado. Al deshabilitar la optimización se puede simplificar la depuración de algunos problemas, aunque el rendimiento se verá afectado. Si se utiliza Solo mi código, suprimir la optimización JIT puede hacer que el código que no sea de usuario aparezca como código de usuario ("Mi código"). Para obtener más información, consulte [JIT optimización y depuración](../debugger/jit-optimization-and-debugging.md).

**Habilitar la depuración de JavaScript para ASP.NET (IE, Edge y Chrome)**: permite al depurador de script para las aplicaciones ASP.NET. En el primer uso en Chrome, debe iniciar sesión en el explorador para habilitar las extensiones de Chrome que ha instalado. Deshabilitar esta opción para revertir al comportamiento heredado.

**Habilitar herramientas de desarrollador de Microsoft Edge para las aplicaciones JavaScript UWP (Experimental)**: habilita las herramientas de desarrollador para aplicaciones UWP JavaScript en Edge.

**Habilitar el depurador de JavaScript de Chrome heredado para ASP.NET**: permite al depurador de script de JavaScript de Chrome heredado para las aplicaciones ASP.NET. En el primer uso en Chrome, debe iniciar sesión en el explorador para habilitar las extensiones de Chrome que ha instalado.

**Usar modo experimental para iniciar la depuración de JavaScript de Chrome al ejecutar Visual Studio como administrador**: indica a Visual Studio para probar una nueva forma de iniciar Chrome durante la depuración de JavaScript.

**Cargar exportaciones de dll (solo nativo)**: carga las tablas de exportación de dll. La información de símbolos de las tablas de exportación de archivos DLL puede resultar útil si se trabaja con mensajes de Windows, procedimientos de Windows (WindowProc), objetos COM, cálculo de referencias o cualquier archivo DLL para el que no disponga de símbolos. La lectura de la información de exportación de archivos DLL implica cierta sobrecarga. Por lo tanto, esta funcionalidad está desactivada de forma predeterminada.

Para ver los símbolos que están disponibles en la tabla de exportación de un archivo DLL, utilice `dumpbin /exports`. Los símbolos están disponibles para cualquier archivo DLL de sistema de 32 bits. Si lee el resultado de `dumpbin /exports` , podrá ver el nombre exacto de la función, incluidos los caracteres no alfanuméricos. Esto resulta útil para establecer un punto de interrupción en una función. Los nombres de función procedentes de tablas de exportación de archivos DLL pueden aparecer truncados en otras partes del depurador. Las llamadas se muestran en una lista según el orden de llamada, y la función actual (la que está anidada a mayor profundidad) aparece en la parte superior. Para obtener más información, vea [dumpbin /exports](/cpp/build/reference/dash-exports).

**Mostrar pilas paralelas ascendente diagrama**: controla la dirección en que se muestran las pilas en la **pilas paralelas** ventana.

**Omitir las excepciones de acceso de memoria GPU si los datos escritos no modificaron el valor**: omite las condiciones de carrera que se detectaron durante la depuración si no ha cambiado los datos. Para obtener más información, consulte [depurar código de GPU](../debugger/debugging-gpu-code.md).

**Usar el modo de compatibilidad administrado**: reemplaza el motor con una versión heredada para habilitar estos escenarios de depuración predeterminado:

- Se utiliza un lenguaje .NET Framework distinto de C#, Visual Basic, o F# que proporciona su propio evaluador de expresiones (incluido C++ / c++ / CLI).

- Desea habilitar editar y continuar para proyectos de C++ durante la depuración en modo mixto.

> [!NOTE]
> Elección de compatibilidad administrado modo deshabilitan algunas características que solo están implementadas en el motor de depuración predeterminado. El motor de depuración heredado se ha sustituido en Visual Studio 2012.

**Usar heredado C# y evaluadores de expresión de VB**: el depurador utilizará Visual Studio 2013 C# o evaluadores de expresión de Visual Basic en lugar de los evaluadores de expresión basados en Roslyn de Visual Studio 2015.

**Advertir al usar visualizadores del depurador personalizados procesos potencialmente no seguros (solo administrado)**: Visual Studio le advierte cuando se usa un visualizador del depurador personalizados que se está ejecutando código en el proceso depurado, ya que podría ejecutar código no seguro.

**Habilitar asignador de montón de depuración de Windows (solo nativo)**: habilita el montón de depuración de windows mejorar el diagnóstico de montón. Habilitar esta opción afectará al rendimiento de la depuración.

**Habilitar herramientas de depuración de interfaz de usuario para XAML**: Live Visual Tree y las ventanas del explorador de propiedades dinámico se mostrarán al iniciar la depuración (**F5**) un tipo de proyecto compatible. Para obtener más información, consulte [propiedades XAML inspeccionar durante la depuración](../debugger/inspect-xaml-properties-while-debugging.md).

- **Obtener una vista previa de los elementos seleccionados en el árbol Visual dinámico**: también se selecciona el elemento de la XAML cuyo contexto está seleccionado en el **Live Visual Tree** ventana.

- **Mostrar herramientas de tiempo de ejecución en la aplicación**: muestra el **Live Visual Tree** comandos en una barra de herramientas en la ventana principal de la aplicación XAML que se está depurando. Esta opción se introdujo en Visual Studio 2015 Update 2.

- **Habilitar la edición de XAML y continuar**: le permite usar la edición y seguir la función con el código XAML.

**Habilitar herramientas de diagnóstico durante la depuración**: el **herramientas de diagnóstico** ventana aparece durante la depuración.

**Mostrar PerfTip de tiempo transcurrido durante la depuración**: la ventana de código muestra el tiempo transcurrido de una llamada al método especificado cuando se depura.

**Habilitar Editar y continuar**: habilita la funcionalidad de editar y continuar durante la depuración.

- **Habilitar Editar y continuar nativa**: puede usar la edición y continuar con la funcionalidad mientras se depura código C++ nativo. Para obtener más información, consulte [editar y continuar (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Aplicar cambios al continuar (solo nativo)**: Visual Studio compila automáticamente y aplica los cambios de código pendientes realizados al continuar el proceso de un estado de interrupción. Si no está seleccionada, puede aplicar los cambios con el elemento **Aplicar cambios en el código** en el menú **Depurar**.

- **Advertir sobre código obsoleto (solo nativo)**: Obtenga advertencias sobre código obsoleto.

**Mostrar la ejecución, haga clic en botón en el editor mientras se depura**: cuando se selecciona esta opción, el [hacer clic y ejecutar](debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) botón se mostrará durante la depuración.

**Cerrar automáticamente la consola cuando se detiene la depuración**: indica a Visual Studio para cerrar la consola al final de una sesión de depuración.

## <a name="options-available-in-older-versions-of-visual-studio"></a>Opciones disponibles en versiones anteriores de Visual Studio

Si usa una versión anterior de Visual Studio, podrían encontrarse con algunas opciones adicionales.

**Habilitar el Asistente de excepciones**: para código administrado, permite que el Asistente de excepciones. En Visual Studio 2017, la aplicación auxiliar de excepciones reemplaza al Asistente de excepciones.

**Desenredar la pila de llamadas en las excepciones no controladas**: hace que el **pila de llamadas** ventana para revertir la pila de llamadas al punto antes de que se produjo la excepción no controlada.

**Advertir si no hay símbolos al iniciar (solo nativo)**: muestra un cuadro de diálogo de advertencia cuando se depura un programa para que el depurador no tiene ninguna información de símbolos.

**Advertir si la depuración de scripts está deshabilitada al inicio**: muestra un cuadro de diálogo de advertencia cuando el depurador se inicia con la depuración de scripts deshabilitada.

**Usar el modo de compatibilidad nativa**: cuando se selecciona esta opción, el depurador usa el depurador nativo de Visual Studio 2010, en lugar del nuevo depurador nativo.

- Use esta opción cuando esté depurando código C++. NET, ya que el nuevo motor de depuración no admite evaluar expresiones de C++. NET. Sin embargo, habilitar el modo de compatibilidad nativa deshabilita muchas características que dependen de la implementación actual del depurador para funcionar. Por ejemplo, el motor heredado carece de muchos visualizadores para tipos integrados como `std::string` en proyectos de Visual Studio 2015.   Usar proyectos de Visual Studio 2013 para la experiencia de depuración óptima en estos casos.

## <a name="see-also"></a>Vea también

- [Depurar en Visual Studio](../debugger/index.md)
- [Guía de características del depurador](../debugger/debugger-feature-tour.md)