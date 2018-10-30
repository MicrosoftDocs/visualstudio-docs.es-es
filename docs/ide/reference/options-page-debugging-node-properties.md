---
title: Página de opciones, Propiedades de nodo Depuración
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 564cc8b2-0084-420e-b560-200cc5621a7e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 261eef97d6b76d5cc793ecb34d2697abc717e0ca
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920903"
---
# <a name="options-page-debugging-node-properties"></a>Página de opciones, Propiedades de nodo Depuración
En las siguientes tablas, se describen las páginas (o colecciones de propiedades) asociadas a la categoría **Depuración**, `DTE.Properties("Debugging", <Property Page>)`, del cuadro de diálogo **Opciones**.

## <a name="general"></a>General
 `DTE.Properties("Debugging", "General")`

|Nombre de elemento de propiedad|Valor|Descripción|
| - |-----------|-----------------|
|PromptOnBreakpointDelete|Get/Set (Boolean)|Determina si el depurador pide permiso antes de eliminar todos los puntos de interrupción de un proyecto.|
|BreakAllProcesses|Get/Set (Boolean)|Determina si el depurador interrumpe todos los procesos cuando se interrumpe un único proceso.|
|BreakAtBoundaries|Get/Set (Boolean)|Determina si el depurador interrumpe la ejecución cuando una excepción cruza un borde entre AppDomains o entre código nativo y administrado.|
|EnableAddressLevelDebugging|Get/Set (Boolean)|Determina si se habilitan las características de depuración de nivel de dirección.|
|ShowDisassemblyIfNoSource|Get/Set (Boolean)|Determina si el depurador muestra el código de desensamblado cuando no está disponible el código fuente.|
|EnableBreakpointFilters|Get/Set (Boolean)|Determina si se habilita el filtrado de punto de interrupción.|
|EnableExceptionAssistant|Get/Set (Boolean)|Determina si se usa el Asistente de excepciones para las excepciones administradas.|
|UnwindCallstack|Get/Set (Boolean)|Determina si el depurador desenreda la pila de llamadas para una excepción no controlada.|
|EnableJustMyCode|Get/Set (Boolean)|Determina si está habilitado Solo mi código para código de C# y Visual Basic.|
|ShowAllMembers|Get/Set (Boolean)|Para los objetos que no son de usuario, determina si el depurador muestra todos los miembros de objeto en las ventanas de variables. Esta opción no tiene ningún efecto a menos que esté habilitado Solo mi código.|
|WarnIfNoUserCode|Get/Set (Boolean)|Determina si el depurador emite una advertencia cuando el usuario intenta asociarse a un proceso que no tiene ningún código de usuario. Esta opción no tiene ningún efecto a menos que esté habilitado Solo mi código.|
|EnablePropertyEvaluation|Get/Set (Boolean)|Determina si el depurador evalúa de forma automática las propiedades y llamadas a función implícitas en código administrado.|
|CallStringConversion|Get/Set (Boolean)|Determina si el depurador llama de forma implícita a una función de conversión de cadenas en objetos de las ventanas de variables.|
|EnableSourceServer|Get/Set (Boolean)|Determina si el depurador puede acceder al código desde un servidor de origen.|
|PrintSourceServerDiagnostics|Get/Set (Boolean)|Determina si la ventana de salida muestra mensajes de diagnóstico relacionados con el servidor de origen. Esta opción no tiene ningún efecto a menos que se habilite el acceso al servidor de origen.|
|HighlightEntireLine|Get/Set (Boolean)|Determina si el depurador resalta una línea completa para los puntos de interrupción y la instrucción actual.|
|RequireSourceToMatch|Get/Set (Boolean)|Determina si el depurador requiere que los archivos de origen coincidan con la versión original al abrir los archivos para la depuración.|
|RedirectOutputToImmediate|Get/Set (Boolean)|Determina si la ventana de salida se redirige a la ventana Inmediato.|
|ShowRawVariableStructure|Get/Set (Boolean)|Determina si los objetos de las ventanas de variables se muestran sin formato.|
|SuppressJitOptimization|Get/Set (Boolean)|Para código administrado, determina si el depurador suprime la optimización Just-In-Time.|
|WarnIfNoSymbols|Get/Set (Boolean)|Determina si el depurador muestra una advertencia si no hay símbolos de depuración disponibles cuando se inicia un proceso.|
|WarnIfScriptDisabled|Get/Set (Boolean)|Determina si el depurador muestra una advertencia si no está habilitada la depuración de script cuando se inicia un proceso.|
|ShowMarkersForAllThreads|Get/Set (Boolean)|Determina si el depurador muestra los marcadores de subprocesos.|
|StepOverPropertiesAndOperators|Get/Set (Boolean)|Especifica si se salta las propiedades y los operadores solo en código administrado.|

## <a name="edit-and-continue"></a>Editar y continuar
 `DTE.Properties("Debugging", "EditAndContinue")`

|Nombre de elemento de propiedad|Valor|Descripción|
| - |-----------|-----------------|
|EnableEditAndContinue|Get/Set (Boolean)|Determina si la opción Editar y continuar está habilitada. Esta opción se aplica a todos los lenguajes que admiten Editar y continuar.|
|InvokedByCommands|Get/Set (Boolean)|Determina si Editar y continuar aplica de forma automática los cambios de código cuando el usuario selecciona un comando de depuración como **Paso** o **Continuar**. Esta opción se aplica solo a código nativo.|
|InvokedByCommandsAskFirst|Get/Set (Boolean)|Determina si Editar y continuar pide permiso al usuario para aplicar cambios de código cuando el usuario selecciona un comando de depuración como **Paso** o **Continuar**. Esta opción se aplica solo a código nativo.|
|WarnAboutStaleCode|Get/Set (Boolean)|Determina si el depurador emite un mensaje de advertencia cuando Editar y continuar daría como resultado la ejecución de código obsoleto. Esta opción se aplica solo a código nativo.|
|RelinkChangesOnStop|Get/Set (Short)|Determina si Visual Studio vuelve a vincular cambios de código aplicados por Editar y continuar cuando se detiene la ejecución de la aplicación. Esta opción se aplica solo a código nativo.|
|AllowPrecompiling|Get/Set (Short)|Determina si Editar y continuar puede cargar los encabezados precompilados en segundo plano. Esta opción se aplica solo a código nativo.|

## <a name="just-in-time"></a>Just-In-Time
 `DTE.Properties("Debugging", "JustInTime")`

|Nombre de elemento de propiedad|Valor|Descripción|
| - |-----------|-----------------|
|JitManaged|Get/Set (Boolean)|Determina si la depuración Just-In-Time está habilitada para código administrado.|
|JitNative|Get/Set (Boolean)|Determina si la depuración Just-In-Time está habilitada para código nativo.|
|JitScript|Get/Set (Boolean)|Determina si la depuración Just-In-Time está habilitada para código de script.|

## <a name="native"></a>Nativo
 `DTE.Properties("Debugging", "Native")`

|Nombre de elemento de propiedad|Valor|Descripción|
| - |-----------|-----------------|
|LoadDllExports|Get/Set (Boolean)|Determina si el depurador carga las tablas de exportación de DLL.|
|EnableRPC|Get/Set (Boolean)|Determina si el depurador puede depurar paso a paso por instrucciones en llamadas a procedimientos remotos COM.|

## <a name="see-also"></a>Vea también

- [Control de la configuración de opciones](http://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [Determinación de los nombres de los elementos de propiedades en las páginas de opciones](http://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [Página de opciones, Propiedades de nodo Fuentes y colores](../../ide/reference/options-page-fonts-and-colors-node-properties.md)
- [Página de opciones, Propiedades de nodo Editor de texto](../../ide/reference/options-page-text-editor-node-properties.md)
- [General, Depuración, cuadro de diálogo Opciones](../../debugger/general-debugging-options-dialog-box.md)
- [Editar y continuar, Depuración, Opciones (Cuadro de diálogo)](http://msdn.microsoft.com/Library/009d225f-ef65-463f-a146-e4c518f86103)
- [Just-In-Time, Depuración, Cuadro de diálogo Opciones](../../debugger/just-in-time-debugging-options-dialog-box.md)