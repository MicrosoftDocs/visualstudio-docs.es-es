---
title: General, Depuración, Opciones (Cuadro de diálogo) | Microsoft Docs
description: Establezca las opciones del depurador de Visual Studio para satisfacer las necesidades de depuración. Puede configurar el comportamiento de interrupción, los niveles de depuración, el comportamiento de visualización y mucho más.
ms.custom: SEO-VS-2020
ms.date: 06/04/2020
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
ms.openlocfilehash: 1b052c2cce3d396debb4fbaf8ce688ede3effb98
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96863015"
---
# <a name="general-debugging-options"></a>Opciones generales de depuración

Para establecer las opciones del depurador de Visual Studio, seleccione **Herramientas** > **Opciones** y, en **Depuración**, active o desactive las casillas situadas junto a las opciones **Generales**. Puede restaurar toda la configuración predeterminada con **Herramientas** > **Configuración de importación y exportación** > **Restablecer todas las configuraciones**. Para restablecer un subconjunto de valores, guarde la configuración con el **Asistente para importar y exportar configuraciones** antes de realizar los cambios que quiera probar y, a continuación, importe la configuración guardada más adelante.

Puede establecer las siguientes opciones **Generales**:

**Preguntar antes de eliminar todos los puntos de interrupción**: Requiere confirmación antes de ejecutar el comando **Eliminar todos los puntos de interrupción**.

**Interrumpir todos los procesos cuando se interrumpa uno**: Interrumpe simultáneamente todos los procesos a los que está asociado el depurador cuando se produce una interrupción.

**Interrumpir cuando las excepciones crucen AppDomain o los límites administrados o nativos**: En la depuración administrada o en modo mixto, Common Language Runtime puede capturar excepciones que atraviesen los límites del dominio de aplicación o los límites administrados o nativos, cuando se cumplen las siguientes condiciones:

1. Cuando el código nativo llama al código administrado utilizando la interoperabilidad COM y el código administrado produce una excepción. Consulte [Información general sobre la interoperabilidad COM](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Cuando el código administrado que se ejecuta en el dominio de aplicación 1 llama al código administrado en el dominio de aplicación 2 y este último produce una excepción. Consulte [Programar con dominios de aplicación](/dotnet/articles/framework/app-domains/index).

3. Cuando el código llama a una función utilizando la reflexión y esa función produce una excepción. Consulte [Reflexión](/dotnet/framework/reflection-and-codedom/reflection).

En las condiciones 2 y 3, el código administrado de `mscorlib` a veces detecta la excepción, en lugar de Common Language Runtime. Esta opción no afecta a la interrupción en excepciones detectadas por `mscorlib`.

**Habilitar la depuración de nivel de dirección**: Habilita las características avanzadas para la depuración en el nivel de dirección (ventana **Desensamblado**, ventana **Registros** y puntos de interrupción de dirección).

- **Mostrar desensamblado si el código fuente no está disponible**:   La ventana **Desensamblado** aparece automáticamente cuando depura código cuyo código fuente no está disponible.

**Habilitar filtros de puntos de interrupción**: Permite establecer filtros en puntos de interrupción, de manera que solo afecten a procesos, subprocesos o equipos concretos.

**Usar el nuevo asistente de excepciones**: Habilita el Asistente de excepciones que reemplaza al asistente de excepciones. La aplicación Asistente de excepciones se admite a partir de Visual Studio 2017.

> [!NOTE]
> En el caso del código administrado, esta opción anteriormente se denominaba **Habilitar el asistente de excepciones**.

**Habilite Solo mi código**: El depurador solo muestra y accede al código de usuario ("Mi código"), y pasa por alto el código de sistema u otro código optimizado o que no tenga símbolos de depuración.

- **Advertir de la inexistencia de código de usuario al iniciar (solo administrado)** :   Cuando se inicia la depuración con la opción Solo mi código habilitada, esta opción le advierte si no hay código de usuario ("Mi código").

**Habilitar ejecución paso a paso de código fuente de .NET Framework**: Permite al depurador ejecutar paso a paso el código fuente de .NET Framework. Al habilitar esta opción, se deshabilita automáticamente la opción Solo mi código. Los símbolos de .NET Framework se descargarán en una ubicación de caché. Cambie la ubicación en caché con el cuadro de diálogo **Opciones**, categoría **Depuración**, página **Símbolos**.

**Saltar propiedades y operadores (solo administrado)** : Impide que el depurador ejecute paso a paso las propiedades y operadores en código administrado.

**Habilitar evaluación de propiedades y otras llamadas a función implícitas**: Activa la evaluación automática de propiedades y de llamadas a funciones implícitas en ventanas de variables y en el cuadro de diálogo **Inspección rápida**.

- **Llamar a la función de conversión de cadenas en objetos de ventanas de variables (solo C# y JavaScript)** : Ejecuta una llamada de conversión de cadena implícita al evaluar objetos en ventanas de variables. El resultado se muestra como una cadena en lugar del nombre de tipo. Solo se aplica mientras se lleva a cabo la depuración en código C#. El atributo DebuggerDisplay puede invalidar esta configuración (consulte [Uso del atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).

**Habilitar compatibilidad de servidor de origen**: Indica al depurador de Visual Studio que obtenga los archivos de código fuente de los servidores de origen que implementan el protocolo SrcSrv (`srcsrv.dll`). Team Foundation Server y las herramientas de depuración para Windows son dos servidores de origen que implementan el protocolo. Para obtener más información sobre la configuración de SrcSrv, consulte la documentación de [SrcSrv](/windows-hardware/drivers/debugger/srcsrv). Asimismo, consulte [Especificación del símbolo (.pdb) y archivos de origen](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Dado que la lectura de archivos *.pdb* puede ejecutar código arbitrario en los archivos, asegúrese de que el servidor es de confianza.

- **Imprimir los mensajes de diagnóstico del servidor de origen en la ventana de salida**:   Cuando se habilita la compatibilidad del servidor de origen, esta configuración activa la presentación de información de diagnóstico.

- **Permitir servidor de origen para ensamblados de confianza parcial (solo administrado)** :   Cuando la compatibilidad del servidor de origen está habilitada, esta configuración invalida el comportamiento predeterminado de no recuperar los orígenes de los ensamblados de confianza parcial.

- **Ejecutar siempre los comandos del servidor de origen que no sean de confianza sin preguntar**:   Cuando la compatibilidad del servidor de origen está habilitada, esta configuración invalida el comportamiento predeterminado de preguntar al ejecutar un comando que no es de confianza.

**Habilitar compatibilidad con vínculos de origen**: Indica al depurador de Visual Studio que descargue los archivos de origen de los archivos *.pdb* que contienen información de vínculos de origen. Para obtener más información sobre los vínculos de origen, consulte la [especificación de vínculos de origen](/dotnet/standard/library-guidance/sourcelink).

> [!IMPORTANT]
> Dado que los vínculos de origen descargarán los archivos mediante http o https, asegúrese de que confía en el archivo *.pdb*.

- **Recurrir a la autenticación del Administrador de credenciales de GIT para todas las solicitudes de vínculos de origen**:   Cuando se habilita la compatibilidad con vínculos de origen y se produce un error en la autenticación de una solicitud de vínculos de origen, Visual Studio llama al Administrador de credenciales de GIT.

**Resaltar la línea de código fuente entera para los puntos de interrupción y la instrucción actual (solo C++)** : Cuando el depurador resalta un punto de interrupción o la instrucción actual, resalta toda la línea.

**Es necesario que los archivos de código fuente coincidan con la versión original**: Indica al depurador que compruebe que un archivo de código fuente coincide con la versión del código fuente utilizada para compilar el archivo ejecutable que se está depurando. Cuando la versión no coincide, se le solicita que busque el archivo de código fuente correspondiente. Si no se encuentra este archivo, el código fuente no se mostrará durante la depuración.

**Redirigir el texto de la ventana de salida a la ventana Inmediato**: Envía a la ventana **Inmediato** todos los mensajes del depurador que normalmente irían a la ventana **Salida**.

**Mostrar la estructura de los objetos en ventanas de variables**: Desactiva todas las personalizaciones de vistas de estructuras de objetos. Para obtener más información sobre las personalizaciones de vistas, consulte [Creación de vistas personalizadas de objetos administrados](../debugger/create-custom-views-of-managed-objects.md).

**Suprimir optimización JIT al cargar el módulo (únicamente administrado)** : Deshabilita la optimización JIT de código administrado cuando se carga un módulo con compilación JIT mientras se asocia el depurador. Al deshabilitar la optimización se puede simplificar la depuración de algunos problemas, aunque el rendimiento se verá afectado. Si se utiliza Solo mi código, suprimir la optimización JIT puede hacer que el código que no sea de usuario aparezca como código de usuario ("Mi código"). Para obtener más información, consulte [Optimización y depuración de JIT](../debugger/jit-optimization-and-debugging.md).

**Habilitar depuración de JavaScript para ASP.NET (IE, Microsoft Edge y Chrome)** : Habilita el depurador de script para las aplicaciones de ASP.NET. Al usarse por primera vez en Chrome, es posible que tenga que iniciar sesión en el explorador para habilitar las extensiones de Chrome que ha instalado. Deshabilite esta opción para volver al comportamiento heredado.

::: moniker range=">= vs-2019"
**Habilitar el uso del depurador de JavaScript de varios destinos para depurar JavaScript en destinos aplicables (requiere el reinicio de la depuración)** : habilita la conexión con el explorador y el back-end simultáneamente, lo que le permite depurar el código que se ejecuta en el cliente y el servidor directamente desde el editor.
::: moniker-end

**Cargar exportaciones de dll (solo nativas)** : Carga las tablas de exportación de archivos DLL. La información de símbolos de las tablas de exportación de archivos DLL puede resultar útil si se trabaja con mensajes de Windows, procedimientos de Windows (WindowProc), objetos COM, cálculo de referencias o cualquier archivo DLL para el que no disponga de símbolos. La lectura de la información de exportación de archivos DLL implica cierta sobrecarga. Por lo tanto, esta funcionalidad está desactivada de forma predeterminada.

Para ver los símbolos que están disponibles en la tabla de exportación de un archivo DLL, utilice `dumpbin /exports`. Los símbolos están disponibles para cualquier archivo DLL de sistema de 32 bits. Si lee el resultado de `dumpbin /exports` , podrá ver el nombre exacto de la función, incluidos los caracteres no alfanuméricos. Esto resulta útil para establecer un punto de interrupción en una función. Los nombres de función procedentes de tablas de exportación de archivos DLL pueden aparecer truncados en otras partes del depurador. Las llamadas se muestran en una lista según el orden de llamada, y la función actual (la que está anidada a mayor profundidad) aparece en la parte superior. Para obtener más información, vea [dumpbin /exports](/cpp/build/reference/dash-exports).

**Mostrar diagrama de pilas paralelas en orden ascendente**: Controla la dirección en la que las pilas se muestran en la ventana **Pilas paralelas**.

**Omitir las excepciones de acceso a la memoria de GPU si los datos escritos no modificaron el valor**: Omite las condiciones de carrera que se detectaron durante la depuración si los datos no cambiaron. Para obtener más información, consulte [Depurar código GPU](../debugger/debugging-gpu-code.md).

**Usar modo de compatibilidad administrado**: Reemplaza el motor de depuración predeterminado por una versión heredada para habilitar estos escenarios:

- Cuando se usa un lenguaje .NET distinto de C#, Visual Basic o F#, que proporciona su propio evaluador de expresiones (incluido C++/CLI).

- Cuando se quiere habilitar Editar y Continuar para los proyectos de C++ durante la depuración en modo mixto.

> [!NOTE]
> Al elegir el Modo de compatibilidad administrado se deshabilitan algunas características que solo están implementadas en el motor de depuración predeterminado. El motor de depuración heredado se reemplazó en Visual Studio 2012.

::: moniker range="vs-2017"
**Usar los evaluadores de expresiones de C# y VB heredados**: El depurador usará los evaluadores de expresión de C# o Visual Basic de Visual Studio 2013 en lugar de los evaluadores de expresión basados en Roslyn de Visual Studio 2015.
::: moniker-end

**Al usar visualizadores del depurador personalizados, advertir de procesos potencialmente no seguros (solo administrados)** : Visual Studio le advierte cuando se usa un visualizador del depurador personalizado que ejecuta código en el proceso de depuración, dado que podría ejecutar código no seguro.

**Habilitar asignador de montón de depuración de Windows (solo nativo)** : Habilita el montón de depuración de Windows para mejorar los diagnósticos del montón. Habilitar esta opción afectará al rendimiento de la depuración.

**Habilitar las herramientas de depuración de interfaz de usuario para XAML**: Aparecerán las ventanas Árbol visual dinámico y Explorador de propiedades dinámico al iniciar la depuración (**F5**) de un tipo de proyecto compatible. Para obtener más información, consulte [Inspeccionar las propiedades XAML durante la depuración](../xaml-tools/inspect-xaml-properties-while-debugging.md).

- **Obtener una vista previa de los elementos seleccionados en el árbol visual dinámico**:   También se selecciona en el **árbol visual dinámico** el elemento XAML cuyo contexto está seleccionado.

- **Mostrar herramientas de runtime en la aplicación**: Muestra los comandos **Árbol visual activo** en una barra de herramientas de la ventana principal de la aplicación XAML que se está depurando. Esta opción se introdujo en Visual Studio 2015 Update 2.

- **Habilitar Recarga activa de XAML**: Le permite usar la característica Recarga activa de XAML con código XAML cuando se ejecuta la aplicación. (Esta característica anteriormente se denominaba "Edición y continuación de XAML")

::: moniker range=">= vs-2019" 
- **Habilitar Solo mi XAML**: A partir de la versión 16.4 de Visual Studio 2019, el **Árbol visual activo** de forma predeterminada solo muestra XAML que se clasifica como código de usuario. Si deshabilita esta opción, se muestra todo el código XAML generado en la herramienta.

- **Desactivar el modo de selección cuando se selecciona un elemento** A partir de la versión 16.4 de Visual Studio 2019, el botón del selector de elementos de la barra de herramientas de la aplicación (**Habilitar selección**) se desactiva cuando se selecciona un elemento. Si deshabilita esta opción, la selección de elementos permanece activada hasta que vuelve a hacer clic en el botón de la barra de herramientas de la aplicación.

- **Aplicar la Recarga activa de XAML al guardar el documento**: a partir de Visual Studio 2019 16.6, aplica la Recarga activa de XAML al guardar el documento.

::: moniker-end

**Habilitar herramientas de diagnóstico durante la depuración**: Durante la depuración, se abre la ventana de **Herramientas de diagnóstico**.

**Mostrar PerfTip de tiempo transcurrido durante la depuración**: La ventana de código muestra el tiempo transcurrido de una determinada llamada de método durante la depuración.

**Habilitar Editar y continuar**: Habilita la función Editar y continuar la durante la depuración.

- **Habilitar la opción Editar y continuar nativa**: Puede usar la función Editar y continuar durante la depuración de código nativo de C++. Para obtener más información, consulte [Editar y continuar (C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Aplicar cambios al continuar (solo nativo)** : Al continuar el proceso desde un estado de interrupción, Visual Studio compila y aplica los cambios de código pendientes realizados automáticamente. Si no está seleccionada, puede aplicar los cambios con el elemento **Aplicar cambios en el código** en el menú **Depurar**.

- **Advertir sobre el código obsoleto (solo nativo)** :   Obtenga advertencias sobre código obsoleto.

**Mostrar el botón Ejecutar para hacer clic en el editor durante la depuración**: Si se selecciona esta opción, el botón [Ejecutar para hacer clic](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) se mostrará durante la depuración.

**Cerrar la consola automáticamente al detenerse la depuración**: Indica a Visual Studio que cierre la consola al final de una sesión de depuración.

::: moniker range=">= vs-2019"
**Habilitar la evaluación rápida de expresiones (solo administrado)** : Permite al depurador intentar una evaluación más rápida mediante la simulación de la ejecución de métodos y propiedades simples.

**Cargar símbolos de depuración en un proceso externo (solo nativo)** : habilita esta [optimización de memoria](https://devblogs.microsoft.com/cppblog/out-of-process-debugger-for-c-in-visual-studio-2019/) durante la depuración.

**Llevar Visual Studio al primer plano cuando se interrumpe en el depurador**: cambia Visual Studio al primer plano cuando se pausa en el depurador.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>Opciones disponibles en versiones anteriores de Visual Studio

Si usa una versión anterior de Visual Studio, puede que estén presentes algunas opciones adicionales.

**Habilitar herramientas de desarrollo de Microsoft Edge para aplicaciones JavaScript UWP (experimental)** : Habilita las herramientas de desarrollo para aplicaciones JavaScript UWP en Microsoft Edge.

**Habilitar el depurador de JavaScript de Chrome heredado para ASP.NET**: Habilita el depurador de script de JavaScript de Chrome heredado para las aplicaciones ASP.NET. Al usarse por primera vez en Chrome, es posible que tenga que iniciar sesión en el explorador para habilitar las extensiones de Chrome que ha instalado.

**Habilitar el Asistente de excepciones**: En el caso del código administrado, habilita el asistente de excepciones. El Asistente de excepciones ha reemplazado al asistente de excepciones a partir de Visual Studio 2017.

**Desenredar la pila de llamadas cuando se produzcan excepciones no controladas**: Hace que la ventana **Pila de llamadas** revierta la pila de llamadas hasta el punto anterior en el que se produjo la excepción no controlada.

**Usar el modo experimental para iniciar la depuración de JavaScript de Chrome cuando se ejecuta Visual Studio como administrador**: Indica a Visual Studio que pruebe una nueva forma de iniciar Chrome durante la depuración de JavaScript.

**Advertir de la inexistencia de símbolos al iniciar (solo nativo)** : Se muestra un cuadro de diálogo de advertencia al depurar un programa para el que el depurador no tiene información de símbolos.

**Avisar si la depuración de scripts está deshabilitada al inicio**: Se muestra un cuadro de diálogo de advertencia cuando el depurador se inicia con la depuración de scripts deshabilitada.

**Usar modo de compatibilidad nativa**: Cuando se selecciona esta opción, el depurador usa el depurador nativo de Visual Studio 2010 en lugar del nuevo depurador nativo.

- Use esta opción cuando depure código de C++ de .NET, ya que el nuevo motor de depuración no admite evaluar expresiones de C++ de .NET. Sin embargo, habilitar el modo de compatibilidad nativa deshabilita muchas características que dependen de la implementación actual del depurador para funcionar. Por ejemplo, el motor heredado carece de muchos visualizadores para tipos integrados, como `std::string` en proyectos de Visual Studio 2015.   En estos casos, use los proyectos de Visual Studio 2013 para una experiencia de depuración óptima.

## <a name="see-also"></a>Vea también

- [Depurar en Visual Studio](../debugger/index.yml)
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
