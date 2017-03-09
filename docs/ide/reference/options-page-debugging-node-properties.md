---
title: "P&#225;gina de opciones, Propiedades de nodo Depuraci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 564cc8b2-0084-420e-b560-200cc5621a7e
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# P&#225;gina de opciones, Propiedades de nodo Depuraci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En las tablas siguientes se describen las páginas \(o colecciones de propiedades\) asociadas a la categoría de **Debugging**, `DTE.Properties("Debugging", <Property Page>)` del cuadro de diálogo **Opciones**.  
  
## General  
 `DTE.Properties("Debugging", "General")`  
  
|Nombre de elemento de propiedad|Valor|Descripción|  
|-------------------------------------|-----------|-----------------|  
|PromptOnBreakpointDelete|Get\/Set \(Boolean\)|Determina si el depurador solicita permiso antes de eliminar todos los puntos de interrupción de un proyecto.|  
|BreakAllProcesses|Get\/Set \(Boolean\)|Determina si el depurador interrumpe todos los procesos cuando se interrumpe un único proceso.|  
|BreakAtBoundaries|Get\/Set \(Boolean\)|Determina si el depurador interrumpe la ejecución cuando una excepción cruza un límite entre AppDomains o entre código administrado y nativo.|  
|EnableAddressLevelDebugging|Get\/Set \(Boolean\)|Determina si están habilitadas las características de depuración de nivel de dirección.|  
|ShowDisassemblyIfNoSource|Get\/Set \(Boolean\)|Determina si el depurador muestra el código de desensamblado cuando no está disponible el código fuente.|  
|EnableBreakpointFilters|Get\/Set \(Boolean\)|Determina si está habilitado el filtrado de puntos de interrupción.|  
|EnableExceptionAssistant|Get\/Set \(Boolean\)|Determina si se utiliza el Asistente de excepciones para las excepciones administradas.|  
|UnwindCallstack|Get\/Set \(Boolean\)|Determina si el depurador desenreda la pila de llamadas para una excepción no controlada.|  
|EnableJustMyCode|Get\/Set \(Boolean\)|Determina si Sólo mi código está habilitado para el código de C\# y de Visual Basic.|  
|ShowAllMembers|Get\/Set \(Boolean\)|Para los objetos de no usuario, determina si el depurador muestra todos los miembros de objeto en las ventanas de variables.  Esta opción no tiene ningún efecto a menos que Sólo mi código esté habilitado.|  
|WarnIfNoUserCode|Get\/Set \(Boolean\)|Determina si el depurador emite una advertencia cuando el usuario intenta asociar a un proceso que no tiene ningún código de usuario.  Esta opción no tiene ningún efecto a menos que Sólo mi código esté habilitado.|  
|EnablePropertyEvaluation|Get\/Set \(Boolean\)|Determina si el depurador evalúa automáticamente las propiedades y las llamadas a función implícitas del código administrado.|  
|CallStringConversion|Get\/Set \(Boolean\)|Determina si el depurador llama implícitamente a una función de conversión de cadenas en objetos de las ventanas de variables.  Esta opción solo se aplica a código de C\# y JScript.|  
|EnableSourceServer|Get\/Set \(Boolean\)|Determina si el depurador puede tener acceso al código de un servidor de origen.|  
|PrintSourceServerDiagnostics|Get\/Set \(Boolean\)|Determina si la ventana de salida muestra mensajes de diagnóstico relacionados con el servidor de origen.  Esta opción no tiene ningún efecto a menos que el acceso al servidor de origen esté habilitado.|  
|HighlightEntireLine|Get\/Set \(Boolean\)|Determina si el depurador resalta una línea completa para los puntos de interrupción y la instrucción actual.|  
|RequireSourceToMatch|Get\/Set \(Boolean\)|Determina si el depurador requiere que los archivos de código fuente coincidan exactamente con la versión original al abrir los archivos para depurar.|  
|RedirectOutputToImmediate|Get\/Set \(Boolean\)|Determina si el resultado de ventana de salida se redirige a la ventana Inmediato.|  
|ShowRawVariableStructure|Get\/Set \(Boolean\)|Determina si los objetos de las ventanas de variables se muestran en formato sin procesar.|  
|SuppressJitOptimization|Get\/Set \(Boolean\)|Para el código administrado, determina si el depurador suprime la optimización Just\-In\-Time.|  
|WarnIfNoSymbols|Get\/Set \(Boolean\)|Determina si el depurador muestra una advertencia si no existe ningún símbolo de depuración disponible cuando se inicia un proceso.|  
|WarnIfScriptDisabled|Get\/Set \(Boolean\)|Determina si el depurador muestra una advertencia si la depuración del script no está habilitada cuando se inicia un proceso.|  
|ShowMarkersForAllThreads|Get\/Set \(Boolean\)|Determina si el depurador muestra los marcadores de subproceso.|  
|StepOverPropertiesAndOperators|Get\/Set \(Boolean\)|Especifica si las propiedades y los operadores se van a recorrer paso a paso por procedimientos únicamente en el código administrado.|  
  
## Editar y continuar  
 `DTE.Properties("Debugging", "EditAndContinue")`  
  
|Nombre de elemento de propiedad|Valor|Descripción|  
|-------------------------------------|-----------|-----------------|  
|EnableEditAndContinue|Get\/Set \(Boolean\)|Determina si están habilitada la función Editar y continuar.  Esta opción se aplica a todos los lenguajes que admiten Editar y continuar.|  
|InvokedByCommands|Get\/Set \(Boolean\)|Determina si Editar y continuar aplica automáticamente los cambios de código cuando el usuario selecciona un comando de depuración como **Paso** o **Continuar**.  Esta opción solo se aplica al código nativo.|  
|InvokedByCommandsAskFirst|Get\/Set \(Boolean\)|Determina si Editar y continuar solicita al usuario permiso para aplicar los cambios de código cuando el usuario selecciona un comando de depuración como **Paso** o **Continuar**.  Esta opción solo se aplica al código nativo.|  
|WarnAboutStaleCode|Get\/Set \(Boolean\)|Determina si el depurador emite un mensaje de advertencia si Editar y continuar va a dar como resultado la ejecución de código obsoleto.  Esta opción solo se aplica al código nativo.|  
|RelinkChangesOnStop|Get\/Set \(Short\)|Determina si Visual Studio vuelve a vincular los cambios de código aplicados por Editar y continuar cuando se detiene la ejecución de la aplicación.  Esta opción solo se aplica al código nativo.|  
|AllowPrecompiling|Get\/Set \(Short\)|Determina si Editar y continuar puede cargar en segundo plano los encabezados precompilados.  Esta opción solo se aplica al código nativo.|  
  
## Just\-In\-Time  
 `DTE.Properties("Debugging", "JustInTime")`  
  
|Nombre de elemento de propiedad|Valor|Descripción|  
|-------------------------------------|-----------|-----------------|  
|JitManaged|Get\/Set \(Boolean\)|Determina si la depuración Just\-In\-Time está habilitada para el código administrado.|  
|JitNative|Get\/Set \(Boolean\)|Determina si la depuración Just\-In\-Time está habilitada para el código nativo.|  
|JitScript|Get\/Set \(Boolean\)|Determina si la depuración Just\-In\-Time está habilitada para el código de script.|  
  
## Native  
 `DTE.Properties("Debugging", "Native")`  
  
|Nombre de elemento de propiedad|Valor|Descripción|  
|-------------------------------------|-----------|-----------------|  
|LoadDllExports|Get\/Set \(Boolean\)|Determina si el depurador carga las tablas de exportación de archivos DLL.|  
|EnableRPC|Get\/Set \(Boolean\)|Determina si el depurador puede avanzar paso a paso por las llamadas a procedimiento remoto COM.|  
  
## Vea también  
 [Controlar la configuración de opciones](../Topic/Controlling%20Options%20Settings.md)   
 [Determinar los nombres de los elementos de propiedades en las páginas de opciones](../Topic/Determining%20the%20Names%20of%20Property%20Items%20on%20Options%20Pages.md)   
 [Página de opciones, Propiedades de nodo Fuentes y colores](../../ide/reference/options-page-fonts-and-colors-node-properties.md)   
 [Página de opciones, Propiedades de nodo Editor de texto](../../ide/reference/options-page-text-editor-node-properties.md)   
 [General, Depuración, Opciones \(Cuadro de diálogo\)](../../debugger/general-debugging-options-dialog-box.md)   
 [Editar y continuar, Depuración, Opciones \(Cuadro de diálogo\)](../Topic/Edit%20and%20Continue,%20Debugging,%20Options%20Dialog%20Box.md)   
 [Just\-In\-Time, Depuración, Opciones \(Cuadro de diálogo\)](../../debugger/just-in-time-debugging-options-dialog-box.md)