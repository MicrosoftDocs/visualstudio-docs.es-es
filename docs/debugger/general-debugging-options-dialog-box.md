---
title: General, Depuración, Cuadro de diálogo Opciones (Opciones) Microsoft Docs
ms.date: 11/12/2019
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
ms.openlocfilehash: 98bbd65d11b26d9b35000e4acbe4d28a585f8ddc
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472687"
---
# <a name="general-debugging-options"></a>Opciones generales de depuración

Para establecer las opciones del depurador de Visual Studio, **seleccione** > **Opciones**de herramientas y, en **Depuración,** seleccione o anule la selección de las casillas situadas junto a **Opciones generales.** Puede restaurar todos los ajustes predeterminados con **Herramientas** > **Importar y Exportar configuración** > **Restablecer todos los ajustes**. Para restablecer un subconjunto de configuraciones, guarde la configuración con el **Asistente para importar y exportar configuraciones** antes de realizar los cambios que desea probar y, a continuación, importe la configuración guardada después.

Puede configurar las siguientes opciones **generales:**

Preguntar antes de **eliminar todos los puntos**de interrupción : Requiere confirmación antes de completar el comando Eliminar todos los puntos de **interrupción.**

**Interrumpir todos los procesos cuando se interrumpe un proceso:** interrumpe simultáneamente todos los procesos a los que está asociado el depurador, cuando se produce una interrupción.

Interrumpir cuando las **excepciones cruzan appDomain o los límites administrados/nativos:** en la depuración administrada o en modo mixto, Common Language Runtime puede detectar excepciones que cruzan los límites del dominio de aplicación o los límites administrados/nativos cuando se cumplen las condiciones siguientes:

1. Cuando el código nativo llama al código administrado utilizando la interoperabilidad COM y el código administrado produce una excepción. Consulte Introducción a la [interoperabilidad COM](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Cuando el código administrado que se ejecuta en el dominio de aplicación 1 llama al código administrado en el dominio de aplicación 2 y este último produce una excepción. Consulte [Programar con dominios de aplicación](/dotnet/articles/framework/app-domains/index).

3. Cuando el código llama a una función mediante la reflexión y esa función produce una excepción. Consulte [Reflexión](/dotnet/framework/reflection-and-codedom/reflection).

En las condiciones 2 y 3, el `mscorlib` código administrado a veces detecta la excepción en lugar de por Common Language Runtime. Esta opción no afecta a la interrupción en excepciones detectadas por `mscorlib`.

**Habilitar depuración de nivel de dirección:** habilita las características avanzadas para la depuración en el nivel de dirección (la ventana **Desensamblado,** la ventana Registros y los **puntos** de interrupción de direcciones).

- **Mostrar desensamblado si el origen no está disponible:** muestra automáticamente la ventana **Desensamblado** al depurar código para el que el origen no está disponible.

Habilitar filtros de punto de **interrupción:** permite establecer filtros en puntos de interrupción para que solo afecten a procesos, subprocesos u equipos específicos.

Usar la nueva aplicación auxiliar de **excepciones:** habilita la aplicación auxiliar de excepciones que reemplaza el asistente de excepciones. (La aplicación auxiliar de excepciones se admite a partir de Visual Studio 2017)

> [!NOTE]
> Para el código administrado, esta opción se llamaba anteriormente Habilitar el asistente de **excepciones** .

**Habilitar solo mi código:** el depurador muestra y pasa únicamente al código de usuario ("Mi código"), ignorando el código del sistema y otro código optimizado o que no tiene símbolos de depuración.

- Advertir si no hay ningún código de **usuario en el inicio (solo administrado):** cuando la depuración comienza con Solo mi código habilitado, esta opción le advierte si no hay código de usuario ("Mi código").

Habilitar el paso de origen de **.NET Framework:** permite que el depurador entre en el origen de .NET Framework. Al activar esta opción, se deshabilita automáticamente Solo mi código. Los símbolos de .NET Framework se descargarán en una ubicación de caché. Cambie la ubicación de la caché con el cuadro de diálogo **Opciones,** categoría **Depuración,** página **Símbolos.**

**Paso sobre propiedades y operadores (solo administrado):** impide que el depurador entre en las propiedades y operadores en código administrado.

**Habilitar evaluación de propiedades y otras llamadas de función implícitas:** activa la evaluación automática de propiedades y llamadas de función implícitas en ventanas de variables y el cuadro de diálogo **Inspección rápida.**

- Función de conversión de cadena de **llamada en objetos en ventanas de variables (solo C- y JavaScript):** ejecuta una llamada de conversión de cadena implícita al evaluar objetos en ventanas de variables. El resultado se muestra como una cadena en lugar del nombre de tipo. Solo se aplica mientras se lleva a cabo la depuración en código C#. Esta configuración se puede invalidar mediante el atributo DebuggerDisplay (consulte [Uso del atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).

**Habilitar compatibilidad con el servidor**de origen: indica al depurador de Visual Studio`srcsrv.dll`que obtenga los archivos de origen de los servidores de origen que implementan el protocolo SrcSrv ( ). Team Foundation Server y las herramientas de depuración para Windows son dos servidores de origen que implementan el protocolo. Para obtener más información acerca de la instalación de SrcSrv, consulte la documentación de [SrcSrv.](/windows-hardware/drivers/debugger/srcsrv) Además, consulte [Especificar símbolo (.pdb) y archivos](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)de origen .

> [!IMPORTANT]
> Dado que la lectura de archivos *.pdb* puede ejecutar código arbitrario en los archivos, asegúrese de que el servidor es de confianza.

- Imprimir mensajes de diagnóstico del servidor de origen en **la ventana Salida:** cuando la compatibilidad con el servidor de origen está habilitada, esta configuración activa la visualización de diagnóstico.

- Permitir el servidor de origen para ensamblados de **confianza parcial (solo administrados):** cuando la compatibilidad con el servidor de origen está habilitada, esta configuración invalida el comportamiento predeterminado de no recuperar orígenes para ensamblados de confianza parcial.

- Ejecute siempre comandos de servidor de origen que no sean de **confianza sin preguntar:** cuando se habilita la compatibilidad con el servidor de origen, esta configuración invalida el comportamiento predeterminado de la solicitud al ejecutar un comando que no es de confianza.

**Habilitar compatibilidad con vínculos**de origen: indica al depurador de Visual Studio que descargue los archivos de origen de los archivos *.pdb* que contienen información de vínculo de origen. Para obtener más información acerca del vínculo de origen, consulte la [especificación](/dotnet/standard/library-guidance/sourcelink)de vínculo de origen .

> [!IMPORTANT]
> Dado que Source Link descargará archivos mediante http o https, asegúrese de confiar en el archivo *.pdb.*

- Vuelva a la autenticación de Administrador de credenciales de **Git para todas las solicitudes**de vínculo de origen: cuando se habilita la compatibilidad con vínculos de origen y una solicitud de vínculo de origen produce un error en la autenticación, Visual Studio llama al Administrador de credenciales de Git.

**Resaltar toda la línea para los puntos de interrupción y la instrucción actual (solo C+):** cuando el depurador resalta un punto de interrupción o una instrucción actual, resalta toda la línea.

Requerir que los archivos de **origen coincidan exactamente con la versión original:** indica al depurador que compruebe que un archivo de origen coincide con la versión del código fuente utilizado para compilar el ejecutable que está depurando. Cuando la versión no coincide, se le pedirá que busque un origen coincidente. Si no se encuentra este archivo, el código fuente no se mostrará durante la depuración.

**Redireccionar todo**el texto de la ventana De salida a la ventana Inmediato: envía todos los mensajes del depurador que normalmente aparecen en la ventana **Salida** a la ventana **Inmediato** en su lugar.

**Mostrar estructura sin procesar de objetos en ventanas de variables:** desactiva todas las personalizaciones de la vista de estructura de objetos. Para obtener más información acerca de las personalizaciones de vista, vea [Crear vistas personalizadas de objetos administrados.](../debugger/create-custom-views-of-managed-objects.md)

**Suprimir la optimización JIT en**la carga del módulo (solo administrado): deshabilita la optimización JIT del código administrado cuando se carga un módulo y se compila JIT mientras se adjunta el depurador. Al deshabilitar la optimización se puede simplificar la depuración de algunos problemas, aunque el rendimiento se verá afectado. Si se utiliza Solo mi código, suprimir la optimización JIT puede hacer que el código que no sea de usuario aparezca como código de usuario ("Mi código"). Para obtener más información, consulte [Optimización y depuración de JIT.](../debugger/jit-optimization-and-debugging.md)

Habilitar la **depuración de JavaScript para ASP.NET (Chrome, Microsoft Edge e IE):** habilita el depurador de scripts para ASP.NET aplicaciones. En el primer uso de Chrome, es posible que debas iniciar sesión en el navegador para habilitar las extensiones de Chrome que hayas instalado. Deshabilite esta opción para volver al comportamiento heredado.

Habilitar herramientas de desarrollo perimetral para aplicaciones JavaScript para **UWP (experimentales):** habilita las herramientas de desarrollador para aplicaciones JavaScript para UWP en Microsoft Edge.

Habilitar el depurador de JavaScript de **Chrome heredado para ASP.NET:** habilita el depurador de scripts de JavaScript de Chrome heredado para ASP.NET aplicaciones. En el primer uso de Chrome, es posible que debas iniciar sesión en el navegador para habilitar las extensiones de Chrome que hayas instalado.

Use una forma experimental de iniciar la depuración de JavaScript de **Chrome al ejecutar Visual Studio como administrador:** indica a Visual Studio que pruebe una nueva forma de iniciar Chrome durante la depuración de JavaScript.

**Cargar exportaciones de dll (solo nativas):** carga tablas de exportación de dll. La información de símbolos de las tablas de exportación de archivos DLL puede resultar útil si se trabaja con mensajes de Windows, procedimientos de Windows (WindowProc), objetos COM, cálculo de referencias o cualquier archivo DLL para el que no disponga de símbolos. La lectura de la información de exportación de archivos DLL implica cierta sobrecarga. Por lo tanto, esta funcionalidad está desactivada de forma predeterminada.

Para ver los símbolos que están disponibles en la tabla de exportación de un archivo DLL, utilice `dumpbin /exports`. Los símbolos están disponibles para cualquier archivo DLL de sistema de 32 bits. Si lee el resultado de `dumpbin /exports` , podrá ver el nombre exacto de la función, incluidos los caracteres no alfanuméricos. Esto resulta útil para establecer un punto de interrupción en una función. Los nombres de función procedentes de tablas de exportación de archivos DLL pueden aparecer truncados en otras partes del depurador. Las llamadas se muestran en una lista según el orden de llamada, y la función actual (la que está anidada a mayor profundidad) aparece en la parte superior. Para obtener más información, vea [dumpbin /exports](/cpp/build/reference/dash-exports).

Mostrar diagrama de **pilas paralelas de abajo hacia arriba:** Controla la dirección en la que se muestran las pilas en la ventana **Pilas paralelas.**

Ignorar las excepciones de acceso a la **memoria de GPU si los datos escritos no cambiaron el valor:** Omite las condiciones de carrera que se detectaron durante la depuración si los datos no cambiaron. Para obtener más información, consulte [Depuración de código de GPU](../debugger/debugging-gpu-code.md).

Usar modo de **compatibilidad administrada:** reemplaza el motor de depuración predeterminado por una versión heredada para habilitar estos escenarios:

- Está utilizando un lenguaje .NET que no sea C, Visual Basic o F, que proporciona su propio evaluador de expresiones (esto incluye C++/CLI).

- Desea habilitar Editar y continuar para proyectos C++ durante la depuración en modo mixto.

> [!NOTE]
> La elección del modo de compatibilidad administrada deshabilita algunas características que se implementan solo en el motor de depuración predeterminado. El motor de depuración heredado se reemplaza en Visual Studio 2012.

**Usar los evaluadores de expresiones de VB y C heredados:** el depurador usará los evaluadores de expresiones de Visual Studio 2013 c o Visual Basic en lugar de los evaluadores de expresiones basados en Roslyn de Visual Studio 2015.

**Advertir al usar visualizadores de depurador personalizados contra procesos potencialmente no seguros (solo administrados):** Visual Studio le advierte cuando se usa un visualizador de depurador personalizado que ejecuta código en el proceso depurado, porque podría estar ejecutando código no seguro.

Habilitar el asignador de montón de depuración de **Windows (solo nativo):** habilita el montón de depuración de Windows para mejorar el diagnóstico del montón. Habilitar esta opción afectará al rendimiento de la depuración.

**Habilitar herramientas de depuración**de interfaz de usuario para XAML: las ventanas Live Visual Tree y Live Property Explore aparecerán al iniciar la depuración (**F5**) un tipo de proyecto compatible. Para obtener más información, vea Inspeccionar propiedades XAML durante la [depuración.](../xaml-tools/inspect-xaml-properties-while-debugging.md)

- Vista previa de **los elementos seleccionados en el árbol visual**activo: el elemento XAML cuyo contexto está seleccionado también se selecciona en la ventana del árbol visual en **vivo.**

- **Mostrar herramientas en tiempo**de ejecución en la aplicación: muestra los comandos de **Live Visual Tree** en una barra de herramientas en la ventana principal de la aplicación XAML que se está depurando. Esta opción se introdujo en Visual Studio 2015 Update 2.

- **Habilitar recarga en caliente XAML:** permite usar la característica de recarga en caliente XAML con código XAML cuando se ejecuta la aplicación. (Esta característica se llamaba anteriormente "XAML Edit and Continue")

::: moniker range=">= vs-2019" 
- **Habilitar solo mi XAML:** a partir de Visual Studio 2019 versión 16.4, el **árbol visual** en vivo muestra de forma predeterminada solo XAML que se clasifica como código de usuario. Si deshabilitas esta opción, todo el código XAML generado se muestra en la herramienta.

- **Desactive el modo de selección cuando se seleccione un elemento** A partir de Visual Studio 2019 versión 16.4, el botón selector de elementos de la barra de herramientas en la aplicación (**Habilitar selección**) se desactiva cuando se selecciona un elemento. Si deshabilita esta opción, la selección de elementos permanecerá activada hasta que vuelva a hacer clic en el botón de la barra de herramientas de la aplicación.
::: moniker-end

Habilitar herramientas de diagnóstico durante la **depuración:** aparece la ventana Herramientas de **diagnóstico** mientras se está depurando.

**Mostrar tiempo transcurrido PerfTip durante la depuración:** la ventana de código muestra el tiempo transcurrido de una llamada al método determinado al depurar.

**Habilitar editar y continuar:** habilita la funcionalidad Editar y continuar durante la depuración.

- **Habilitar edición nativa y continuar:** puede usar la funcionalidad Editar y continuar al depurar código C++ nativo. Para obtener más información, consulte [Editar y continuar (C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Aplicar cambios en continuar (solo nativo):** Visual Studio compila y aplica automáticamente los cambios de código pendientes que haya realizado al continuar el proceso desde un estado de interrupción. Si no está seleccionado, puede optar por aplicar cambios mediante el **elemento Aplicar cambios** de código en el menú **Depurar.**

- **Advertir sobre código obsoleto (solo nativo):** obtenga advertencias sobre el código obsoleto.

**Mostrar botón Ejecutar para hacer clic en**el editor durante la depuración: cuando se selecciona esta opción, se mostrará el botón Ejecutar para hacer [clic](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) durante la depuración.

**Cerrar automáticamente la consola cuando se detiene la depuración:** indica a Visual Studio que cierre la consola al final de una sesión de depuración.

::: moniker range=">= vs-2019"
**Habilitar la evaluación rápida de expresiones (solo administrado):** permite al depurador intentar una evaluación más rápida simulando la ejecución de propiedades y métodos simples.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>Opciones disponibles en versiones anteriores de Visual Studio

Si usa una versión anterior de Visual Studio, es posible que haya algunas opciones adicionales.

Habilitar el asistente de **excepciones:** para el código administrado, habilita el asistente de excepciones. A partir de Visual Studio 2017, la aplicación auxiliar de excepciones reemplazó el asistente de excepciones.

**Desenredar la pila de llamadas en excepciones no controladas:** hace que la ventana **Pila** de llamadas revierta la pila de llamadas al punto antes de que se produjera la excepción no controlada.

**Advertir si no hay símbolos en el inicio (solo nativo):** muestra un cuadro de diálogo de advertencia al depurar un programa para el que el depurador no tiene información de símbolos.

Advertir si la depuración de **scripts está deshabilitada al iniciar:** muestra un cuadro de diálogo de advertencia cuando se inicia el depurador con la depuración de scripts deshabilitada.

Usar modo de **compatibilidad nativo:** cuando se selecciona esta opción, el depurador usa el depurador nativo de Visual Studio 2010 en lugar del nuevo depurador nativo.

- Utilice esta opción al depurar código De .NET C++, ya que el nuevo motor de depuración no admite la evaluación de expresiones C++. Sin embargo, habilitar el modo de compatibilidad nativa deshabilita muchas características que dependen de la implementación actual del depurador para funcionar. Por ejemplo, el motor heredado carece de muchos visualizadores para tipos integrados como `std::string` en proyectos de Visual Studio 2015.   Use proyectos de Visual Studio 2013 para obtener la experiencia de depuración óptima en estos casos.

## <a name="see-also"></a>Vea también

- [Depuración en Visual Studio](../debugger/index.yml)
- [Primero mire el depurador](../debugger/debugger-feature-tour.md)
