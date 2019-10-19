---
title: General, depuración, opciones (cuadro de diálogo) | Microsoft Docs
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
ms.openlocfilehash: bbd99d260ba61d9e3ae9e877ecc1cefb1a22892e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569072"
---
# <a name="general-debugging-options"></a>Opciones generales de depuración

Para establecer las opciones del depurador de Visual Studio, seleccione **herramientas**  > **Opciones**y, en **depuración** , Active o desactive las casillas situadas junto a las opciones **generales** . Puede restaurar todas las opciones de configuración predeterminadas con **herramientas**  > **configuración de importación y exportación**  > **restablecer toda la configuración**. Para restablecer un subconjunto de opciones de configuración, guarde la configuración con el **Asistente para importar y exportar configuraciones** antes de realizar los cambios que desea probar y, a continuación, importe la configuración guardada más adelante.

Puede establecer las siguientes opciones **generales** :

**Preguntar antes de eliminar todos los puntos de interrupción**: requiere confirmación antes de completar el comando **eliminar todos los puntos de interrupción** .

**Interrumpir todos los procesos cuando se interrumpa un proceso**: interrumpe simultáneamente todos los procesos a los que está asociado el depurador cuando se produce una interrupción.

**Interrumpir cuando las excepciones crucen AppDomain o los límites administrados o nativos**: en la depuración administrada o en modo mixto, el Common Language Runtime puede detectar excepciones que atraviesan los límites del dominio de aplicación o los límites administrados o nativos cuando lo siguiente las condiciones son verdaderas:

1. Cuando el código nativo llama al código administrado utilizando la interoperabilidad COM y el código administrado produce una excepción. Vea [Introducción a la interoperabilidad com](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Cuando el código administrado que se ejecuta en el dominio de aplicación 1 llama al código administrado en el dominio de aplicación 2 y este último produce una excepción. Consulte [Programar con dominios de aplicación](/dotnet/articles/framework/app-domains/index).

3. Cuando el código llama a una función mediante reflexión, y esa función produce una excepción. Vea [reflexión](/dotnet/framework/reflection-and-codedom/reflection).

En las condiciones 2 y 3, a veces el código administrado detecta la excepción en `mscorlib` en lugar de en el Common Language Runtime. Esta opción no afecta a la interrupción en excepciones detectadas por `mscorlib`.

**Habilitar la depuración de nivel de dirección**: habilita las características avanzadas para la depuración en el nivel de dirección (la ventana **Desensamblado** , la ventana **registros** y los puntos de interrupción de dirección).

- **Mostrar desensamblado si el origen no está disponible**: muestra automáticamente la ventana **Desensamblado** al depurar el código para el que el origen no está disponible.

**Habilitar filtros de puntos de interrupción**: permite establecer filtros en puntos de interrupción para que solo afecten a procesos, subprocesos o equipos específicos.

**Use la nueva aplicación auxiliar de excepciones**: habilita la aplicación auxiliar de excepciones que reemplaza al asistente de excepciones. (La aplicación auxiliar de excepciones se admite a partir de Visual Studio 2017)

> [!NOTE]
> En el caso de código administrado, esta opción se llamaba previamente **Habilitar el Asistente de excepciones** .

**Habilitar solo mi código**: el depurador solo muestra y realiza los pasos en el código de usuario ("mi código"), omitiendo el código del sistema y otro código optimizado o que no tenga símbolos de depuración.

- **Advertir si no hay código de usuario al iniciar (solo administrado)** : cuando se inicia la depuración con solo mi código habilitado, esta opción le advierte si no hay código de usuario ("mi código").

**Habilitar la ejecución paso**a paso del código fuente de .NET Framework: permite que el depurador entre en .NET Framework origen. Al habilitar esta opción, se deshabilita automáticamente Solo mi código. .NET Framework símbolos se descargarán en una ubicación de caché. Cambie la ubicación de la memoria caché con el cuadro de diálogo **Opciones** , categoría de **depuración** , página **símbolos** .

**Saltar propiedades y operadores (solo administrado)** : impide que el depurador ejecute paso a paso las propiedades y los operadores en código administrado.

**Habilitar evaluación de propiedades y otras llamadas a función implícitas**: activa la evaluación automática de las propiedades y las llamadas a funciones implícitas en ventanas de variables y en el cuadro de diálogo **Inspección rápida** .

- **Llamar a la función de conversión de cadenas en objetosC# de ventanas de variables (y solo JavaScript)** : ejecuta una llamada de conversión de cadena implícita al evaluar objetos en ventanas de variables. El resultado se muestra como una cadena en lugar del nombre de tipo. Solo se aplica mientras se lleva a cabo la depuración en código C#. Este valor puede ser invalidado por el atributo DebuggerDisplay (vea [Using the DebuggerDisplay Attribute](../debugger/using-the-debuggerdisplay-attribute.md)).

**Habilitar la compatibilidad con el servidor de origen**: indica al depurador de Visual Studio que obtenga los archivos de origen de los servidores de origen que implementan el protocolo SrcSrv (`srcsrv.dll`). Team Foundation Server y las herramientas de depuración para Windows son dos servidores de origen que implementan el protocolo. Para obtener más información sobre la configuración de SrcSrv, consulte la documentación de [srcsrv](/windows-hardware/drivers/debugger/srcsrv) . Además, consulte [especificar archivos de código fuente y símbolos (. pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Dado que la lectura de archivos *.pdb* puede ejecutar código arbitrario en los archivos, asegúrese de que el servidor es de confianza.

- **Imprimir mensajes de diagnóstico del servidor de origen en la ventana de salida**: cuando se habilita la compatibilidad del servidor de origen, esta configuración activa la presentación de diagnóstico.

- **Permitir el servidor de origen para ensamblados de confianza parcial (solo administrado)** : cuando se habilita la compatibilidad con el servidor de origen, esta configuración invalida el comportamiento predeterminado de no recuperar orígenes para ensamblados de confianza parcial.

- **Ejecutar siempre comandos de servidor de origen que no sean de confianza sin preguntar**: cuando la compatibilidad del servidor de origen está habilitada, esta configuración invalida el comportamiento predeterminado de preguntar al ejecutar un comando que no es de confianza.

**Habilitar compatibilidad con vínculos de origen**: indica al depurador de Visual Studio que descargue los archivos de código fuente para los archivos *. pdb* que contienen información de vínculo de origen. Para obtener más información sobre el vínculo de origen, vea la [especificación de vínculo de origen](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

> [!IMPORTANT]
> Dado que el vínculo de origen descargará los archivos mediante http o https, asegúrese de que confía en el archivo *. pdb* .

- **Revertir a la autenticación del administrador de credenciales de Git para todas las solicitudes de vínculo de origen**: cuando se habilita la compatibilidad con vínculos de origen y se produce un error en la autenticación de la solicitud de vínculo de origen, Visual Studio llama entonces al administrador de credenciales de Git

**Resaltar la línea completa para los puntos de interrupciónC++ y la instrucción actual (solo)** : cuando el depurador resalta un punto de interrupción o una instrucción actual, resalta la línea completa.

**Requerir que los archivos de código fuente coincidan exactamente con la versión original**: indica al depurador que compruebe que un archivo de código fuente coincide con la versión del código fuente utilizada para compilar el archivo ejecutable que se está depurando. Cuando la versión no coincida, se le pedirá que busque un origen coincidente. Si no se encuentra este archivo, el código fuente no se mostrará durante la depuración.

**Redirigir todo el texto de la ventana de salida a la ventana inmediato**: envía todos los mensajes del depurador que normalmente aparecen en la ventana de **salida** a la ventana **inmediato** en su lugar.

**Mostrar la estructura sin procesar de los objetos en ventanas de variables**: desactiva todas las personalizaciones de la vista de estructura de objetos. Para obtener más información acerca de las personalizaciones de vistas, vea [crear vistas personalizadas de objetos administrados](../debugger/create-custom-views-of-managed-objects.md).

**Suprimir optimización JIT al cargar el módulo (solo administrado)** : deshabilita la optimización JIT de código administrado cuando se carga un módulo y se compila JIT mientras el depurador está asociado. Al deshabilitar la optimización se puede simplificar la depuración de algunos problemas, aunque el rendimiento se verá afectado. Si se utiliza Solo mi código, suprimir la optimización JIT puede hacer que el código que no sea de usuario aparezca como código de usuario ("Mi código"). Para obtener más información, vea [depuración y optimización JIT](../debugger/jit-optimization-and-debugging.md).

**Habilitación de la depuración de JavaScript para ASP.net (Chrome, Microsoft Edge e IE)** : habilita el depurador de scripts para aplicaciones de ASP.net. Al usarse por primera vez en Chrome, es posible que tenga que iniciar sesión en el explorador para habilitar las extensiones de Chrome que ha instalado. Deshabilite esta opción para revertir al comportamiento heredado.

**Habilitación de herramientas de desarrollo perimetrales para aplicaciones JavaScript para UWP (experimental)** : habilita las herramientas de desarrollo para aplicaciones de JavaScript para UWP en Microsoft Edge.

**Habilitar el depurador de JavaScript de Chrome heredado para ASP.net**: habilita el depurador de scripts de JavaScript de Chrome heredado para las aplicaciones de ASP.net. Al usarse por primera vez en Chrome, es posible que tenga que iniciar sesión en el explorador para habilitar las extensiones de Chrome que ha instalado.

**Use la manera experimental de iniciar la depuración de JavaScript de Chrome cuando ejecute Visual Studio como administrador**: indica a Visual Studio que pruebe una nueva forma de iniciar Chrome durante la depuración de JavaScript.

**Cargar exportaciones de dll (solo nativo)** : carga las tablas de exportación de archivos dll. La información de símbolos de las tablas de exportación de archivos DLL puede resultar útil si se trabaja con mensajes de Windows, procedimientos de Windows (WindowProc), objetos COM, cálculo de referencias o cualquier archivo DLL para el que no disponga de símbolos. La lectura de la información de exportación de archivos DLL implica cierta sobrecarga. Por lo tanto, esta funcionalidad está desactivada de forma predeterminada.

Para ver los símbolos que están disponibles en la tabla de exportación de un archivo DLL, utilice `dumpbin /exports`. Los símbolos están disponibles para cualquier archivo DLL de sistema de 32 bits. Si lee el resultado de `dumpbin /exports` , podrá ver el nombre exacto de la función, incluidos los caracteres no alfanuméricos. Esto resulta útil para establecer un punto de interrupción en una función. Los nombres de función procedentes de tablas de exportación de archivos DLL pueden aparecer truncados en otras partes del depurador. Las llamadas se muestran en una lista según el orden de llamada, y la función actual (la que está anidada a mayor profundidad) aparece en la parte superior. Para obtener más información, vea [dumpbin /exports](/cpp/build/reference/dash-exports).

**Mostrar diagrama de pilas paralelas ascendente**: controla la dirección en la que las pilas se muestran en la ventana **pilas paralelas** .

**Omitir las excepciones de acceso a la memoria de GPU si los datos escritos no cambiaron el valor**: omite las condiciones de carrera que se detectaron durante la depuración si los datos no han cambiado. Para obtener más información, vea [depurar código de GPU](../debugger/debugging-gpu-code.md).

**Usar el modo de compatibilidad administrada**: reemplaza el motor de depuración predeterminado por una versión heredada para habilitar estos escenarios:

- Está utilizando un lenguaje .NET distinto de C#, Visual Basic o F# que proporciona su propio evaluador de expresiones (esto incluye C++/CLI).

- Desea habilitar editar y continuar para los proyectos C++ durante la depuración en modo mixto.

> [!NOTE]
> Al elegir el modo de compatibilidad administrado se deshabilitan algunas características que solo se implementan en el motor de depuración predeterminado. El motor de depuración heredado se ha reemplazado en Visual Studio 2012.

**Usar los evaluadores de expresiones C# heredados y de VB**: el depurador usará los evaluadores de expresiones Visual Studio 2013 C# o Visual Basic en lugar de los evaluadores de expresiones basados en Roslyn de Visual Studio 2015.

**Advertir al usar visualizadores del depurador personalizados contra procesos potencialmente inseguros (solo administrados)** : Visual Studio le avisa cuando se usa un visualizador del depurador personalizado que ejecuta código en el proceso depurado, ya que podría estar ejecutando código no seguro. .

**Habilitar asignador de montón de depuración de Windows (solo nativo)** : habilita el montón de depuración de Windows para mejorar los diagnósticos del montón. Habilitar esta opción afectará al rendimiento de la depuración.

**Habilitar las herramientas de depuración de la interfaz de usuario para XAML**: el árbol visual dinámico y la propiedad dinámica explorar las ventanas aparecerán al iniciar la depuración (**F5**) un tipo de proyecto compatible. Para obtener más información, vea [inspeccionar las propiedades XAML durante la depuración](../xaml-tools/inspect-xaml-properties-while-debugging.md).

- **Vista previa de los elementos seleccionados en el árbol visual dinámico**: el elemento XAML cuyo contexto está seleccionado también se selecciona en la ventana del **árbol visual activo** .

- **Mostrar herramientas en tiempo de ejecución en la aplicación**: muestra los comandos de **árbol visual dinámico** en una barra de herramientas de la ventana principal de la aplicación XAML que se está depurando. Esta opción se presentó en Visual Studio 2015 Update 2.

- **Habilitar la recarga activa de XAML**: permite usar la característica de recarga en caliente de XAML con código XAML cuando se ejecuta la aplicación. (Esta característica se llamaba anteriormente "XAML Edit and Continue")

**Habilitar herramientas de diagnóstico durante la depuración**: la ventana de **herramientas de diagnóstico** aparece mientras se depura.

**Mostrar transcurrida de tiempo transcurrido durante la depuración**: la ventana de código muestra el tiempo transcurrido de una llamada de método determinada durante la depuración.

**Habilitar editar y continuar**: habilita la funcionalidad editar y continuar durante la depuración.

- **Habilitar editar y continuar nativo**: puede usar la funcionalidad editar y continuar durante la depuración C++ de código nativo. Para obtener más información, vea [Editar y continuarC++()](../debugger/edit-and-continue-visual-cpp.md).

- **Aplicar cambios al continuar (solo nativo)** : Visual Studio compila automáticamente y aplica los cambios de código pendientes que haya realizado al continuar el proceso desde un estado de interrupción. Si no está seleccionada, puede aplicar los cambios con el elemento **Aplicar cambios en el código** en el menú **Depurar**.

- **Advertir sobre el código obsoleto (solo nativo)** : obtener advertencias sobre el código obsoleto.

**Mostrar botón ejecutar hasta clic en el editor durante la depuración**: cuando se selecciona esta opción, el botón [ejecutar hasta clic](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) se mostrará durante la depuración.

**Cerrar automáticamente la consola cuando se detenga la depuración**: indica a Visual Studio que cierre la consola al final de una sesión de depuración.

::: moniker range=">= vs-2019"
**Habilitar la evaluación de expresiones rápidas (solo administrado)** : permite que el depurador intente realizar una evaluación más rápida mediante la simulación de la ejecución de métodos y propiedades simples.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>Opciones disponibles en versiones anteriores de Visual Studio

Si usa una versión anterior de Visual Studio, pueden existir algunas opciones adicionales.

**Habilitar el Asistente de excepciones**: para el código administrado, habilita el Asistente de excepciones. A partir de Visual Studio 2017, la aplicación auxiliar de excepciones ha reemplazado el Asistente de excepciones.

**Desenredar la pila de llamadas de las excepciones no controladas**: hace que la ventana **pila de llamadas** revierta la pila de llamadas hasta el punto anterior a la excepción no controlada.

**Advertir si no hay símbolos al iniciar (solo nativo)** : muestra un cuadro de diálogo de advertencia cuando se depura un programa para el que el depurador no tiene información de símbolos.

**Advertir si la depuración de scripts está deshabilitada en el inicio**: muestra un cuadro de diálogo de advertencia cuando el depurador se inicia con la depuración de script deshabilitada.

**Usar el modo de compatibilidad nativa**: cuando se selecciona esta opción, el depurador usa el depurador nativo de Visual Studio 2010 en lugar del nuevo depurador nativo.

- Use esta opción cuando esté depurando código C++ .net, ya que el nuevo motor de depuración no admite C++ la evaluación de expresiones .net. Sin embargo, habilitar el modo de compatibilidad nativa deshabilita muchas características que dependen de la implementación actual del depurador para funcionar. Por ejemplo, el motor heredado carece de muchos Visualizadores para tipos integrados como `std::string` en proyectos de Visual Studio 2015.   Utilice proyectos de Visual Studio 2013 para una experiencia de depuración óptima en estos casos.

## <a name="see-also"></a>Vea también

- [Depurar en Visual Studio](../debugger/index.yml)
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
