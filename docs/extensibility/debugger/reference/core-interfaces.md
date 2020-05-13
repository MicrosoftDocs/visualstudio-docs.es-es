---
title: Interfaces de núcleo ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bf01ffceb122ad99d5ecca8fabfaa102a8fc505
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737580"
---
# <a name="core-interfaces"></a>Interfaces básicas
Las siguientes interfaces son las interfaces principales [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]para extender el depurador mediante el archivo .

## <a name="discussion"></a>Discusión
 Estas interfaces se utilizan principalmente para crear el motor de depuración (DE). Se organizan aquí por categorías:

- [Interrupción](#Breakpoints)

- [Contextos](#Contexts)

- [Servidor principal](#CoreServer)

- [Motores de depuración](#DebugEngines)

- [Documentos](#Documents)

- [Eventos](#Events)

- [Expresiones](#Expressions)

- [Memoria](#Memory)

- [Módulos](#Modules)

- [Puertos](#Ports)

- [Procesos](#Processes)

- [Programs](#Programs)

- [Propiedades](#Properties)

- [Marcos de pila](#StackFrames)

- [Hilos](#Threads)

- [Visualizadores de tipo](#TypeVisualizers)

  Las entidades que pueden implementar las interfaces son:

- Motor de depuración (DE)

- Proveedor de puertos (PS)

- Evaluador de expresiones (EE)

- Visual Studio (VS)

## <a name="breakpoints"></a><a name="Breakpoints"></a>Interrupción
 Estas interfaces están relacionadas con la implementación y el seguimiento de puntos de interrupción.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Representa un punto de interrupción enlazado a una ubicación de memoria.|
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Enviado por el DE cuando un punto de interrupción está enlazado a una ubicación de memoria.|
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Representa una suma de comprobación de documento para una solicitud de punto de interrupción.|
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Enviado por el DE cuando un punto de interrupción no se puede enlazar a una ubicación de memoria.|
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Enviado por el DE cuando se alcanza un punto de interrupción.|
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Representa una solicitud de un punto de interrupción; utilizado en la creación de un punto de interrupción pendiente.|
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Representa una solicitud de un punto de interrupción; utilizado en la creación de un punto de interrupción pendiente.|
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Representa la información utilizada para enlazar un punto de interrupción.|
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Enviado por el DE cuando un punto de interrupción no está enlazado desde una ubicación de memoria.|
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Representa un punto de interrupción no válido (devuelta por `IDebugBreakpointErrorEvent2`).|
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Representa la información de resolución sobre un punto de interrupción no válido.|
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Representa una posición en una función donde se establece un punto de interrupción.|
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Representa un punto de interrupción que se va a enlazar; utilizado en la creación de un punto de interrupción enlazado.|
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Representa una enumeración sobre un conjunto de puntos de interrupción enlazados.|
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Representa una enumeración sobre un conjunto de puntos de interrupción que no se pudo enlazar a una ubicación de memoria.|

## <a name="contexts"></a><a name="Contexts"></a>Contextos
 Estas interfaces representan varios tipos de contextos dentro del programa que se está depurando.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Representa la posición inicial de una instrucción de código.|
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Extiende el [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) interfaz para habilitar la recuperación de interfaces de módulo y proceso.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Representa una posición en un documento.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Representa el contexto en el que se evalúa una expresión.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Representa la ubicación inicial en memoria de una colección de bytes.|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Representa un contexto de marco de pila en un punto de interrupción o excepción.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Representa un contexto de marco de pila en un punto de interrupción o excepción.|
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Representa una enumeración sobre un conjunto de contextos de código.|

## <a name="core-server"></a><a name="CoreServer"></a>Servidor principal
 Estas interfaces representan la máquina en la que se está depurando un programa. Estos son implementados por [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] pero pueden ser llamados por los motores de depuración.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Proporciona acceso a puertos y proveedores de puertos, así como información sobre el equipo.|
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Representa un [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) que admite la depuración remota.|

## <a name="debug-engines"></a><a name="DebugEngines"></a>Motores de depuración
 Estas interfaces representan los motores de depuración y sus eventos asociados.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Representa un motor de depuración personalizado.|
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Representa un motor de depuración personalizado que admite la carga de símbolos, JustMyCode y excepciones.|
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Enviado por cada nueva instancia de la DE para indicar que está listo para controlar las tareas de depuración.|
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Representa un motor de depuración personalizado que admite el inicio de programas.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Representa un nodo de programa que controla varios motores de depuración.|
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Proporciona una manera para que el SDM obtenga una interfaz al motor de depuración desde un subproceso, programa o marco de pila.|

## <a name="documents"></a><a name="Documents"></a>Documentos
 Estas interfaces representan documentos (archivos de origen) y sus elementos asociados.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Enviado por el DE para solicitar la apertura de un documento.|
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Representa una secuencia de instrucciones desensambladas de un documento.|
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|Representa un documento proporcionado por el DE, especificando un nombre y un identificador de clase (CLSID).|
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE.|Representa una suma de comprobación para un documento de depuración y permite pasar la suma de comprobación entre componentes.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Representa un contexto de documento, una posición dentro de un documento correspondiente a una instrucción determinada y contexto de código.|
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|Representa una posición general dentro de un documento.|
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Representa una posición en un archivo de origen como un desplazamiento de caracteres.|
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|Representa un documento de texto proporcionado por el DE (derivado de [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), que proporciona el texto real.|
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Enviado por el DE para especificar los cambios en un archivo de origen que está en memoria.|

## <a name="events"></a><a name="Events"></a>Eventos
 Estas interfaces representan todos los eventos que se envían entre el DE y el administrador del debug de la sesión (SDM).

| Interfaz | Implementado por | Descripción |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | DE | Enviado por el DE para solicitar la apertura de un documento. |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | DE | El motor de depuración (DE) envía esta interfaz al administrador de depuración de sesión (SDM) para establecer el mensaje de la barra de estado durante las cargas de símbolos. |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | DE | Enviado por el DE cuando se ha completado una interrupción en el programa. |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | DE | Enviado por el DE cuando se enlaza un punto de interrupción. |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | DE | Enviado por el DE cuando un punto de interrupción no se puede enlazar. |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | DE | Enviado por el DE cuando se alcanza un punto de interrupción. |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | DE | Enviado por el DE cuando un punto de interrupción no está enlazado. |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | DE | Enviado por el DE para determinar si debe detenerse en una ubicación determinada. |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | DE | Enviado por el DE para especificar los cambios en un archivo de origen que está en memoria. |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | DE | Enviado por cada nueva instancia de la DE para indicar que está listo para controlar las tareas de depuración. |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | DE | Enviado por el DE para indicar que el programa que se está depurando está listo para ejecutar la primera instrucción. |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | DE | Interfaz que es utilizada por otras interfaces de eventos, que podrían devolver un error, para proporcionar mensajes de error legibles por el usuario. |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | DE, PS | Interfaz base de la que se derivan todas las demás interfaces de eventos. |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | VS | Representa una interfaz implementada por el SDM a la que se envían eventos (expresados como objetos que implementan una interfaz de eventos determinada). |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | DE | Enviado por la DE cuando se ha producido una excepción en el programa que se está depurando. |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | DE | Enviado por la DE cuando se completa una evaluación de expresiones asincrónicas. |
| IDebugFindSymbolEvent2 | | OBSOLETO. NO USAR. |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | DE | Enviado por el DE cuando se ha completado el procesamiento de una excepción interceptada. |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | DE | Enviado por el DE cuando un programa ha completado la carga. |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | DE | Enviado por el DE para que el IDE muestre un mensaje informativo al usuario. |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | DE | Enviado por el DE cuando se carga o descarga un módulo. |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | DE | Indica a [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] la interfaz de usuario del depurador que advierta al usuario de que no se podían encontrar símbolos para el ejecutable iniciado. |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | DE | Enviado por el DE para que el IDE muestre una cadena arbitraria. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | VS, DE | Enviado por un puerto para comunicar eventos de puerto a cualquier agente de escucha. |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | DE, PS | Enviado por la DE o el puerto cuando se ha creado un proceso. |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | DE, PS | Enviado por el DE o el puerto cuando se ha destruido un proceso. |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | DE, PS | Enviado por la DE o el puerto cuando se ha creado un programa. |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | DE, PS | Enviado por el DE o puerto cuando un programa ha sido destruido. |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | DE | Permite que un motor de depuración invalide el comportamiento predeterminado de la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfaz de usuario al finalizar una sesión de depuración. |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | DE | Enviado desde el motor de depuración (DE) al administrador de depuración de sesión (SDM) cuando cambia el nombre de un programa. |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | DE | Enviado por el DE cuando se ha `IDebugProperty2` creado una nueva propiedad (representada por la interfaz). |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | DE | Enviado por el DE cuando una propiedad ha sido destruida. |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | DE | Enviado por el DE al salir de o sobre una función para que el valor devuelto se pueda mostrar correctamente. |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | VS | Permite que los motores de depuración lean la configuración de métricas de forma remota. |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | DE | Enviado por el DE cuando se ha completado un paso dentro, encima o fuera de una instrucción. |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | DE | Enviado por el DE para indicar el éxito o el error de cargar símbolos para un módulo. |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | DE | Enviado por la DE cuando se ha creado un subproceso. |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | DE | Enviado por el DE cuando se ha destruido un subproceso. |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | DE | Enviado por la DE cuando un subproceso ha cambiado su nombre. |

## <a name="expressions"></a>Expresiones <a name="Expressions"></a>
 Estas interfaces representan expresiones que se evaluarán en un contexto determinado.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Representa una expresión que se va a evaluar. Obtenido de la [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Representa un contexto en el que se evalúa una expresión. Obtenido de la [Interfaz IDebugStackFrame2.](../../../extensibility/debugger/reference/idebugstackframe2.md)|
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Enviado por la DE cuando se completa una evaluación de expresiones asincrónicas.|

## <a name="memory"></a><a name="Memory"></a>Memoria
 Estas interfaces representan secuencias de bytes en la memoria.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Representa una secuencia de bytes en memoria que se pueden leer o escribir en.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Representa una ubicación en memoria de una secuencia de bytes.|

## <a name="modules"></a><a name="Modules"></a>Módulos
 Estas interfaces representan un módulo, que corresponde a un ejecutable o . DLL.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Representa un único archivo ejecutable o DLL.|
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Representa un [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) que admite símbolos.|
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Enviado por el DE cuando se carga o descarga un módulo.|
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Representa la información del servidor de origen contenida en un archivo PDB.|
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Representa una enumeración sobre un conjunto de módulos conocidos por un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|

## <a name="ports"></a><a name="Ports"></a>Puertos
 Estas interfaces representan puertos y proveedores de puertos.

| Interfaz | Implementado por | Descripción |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | VS, PS | Representa el puerto predeterminado en el equipo local. |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | VS | Habilita un motor de depuración [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] que usa DCOM para pedir a la interfaz de usuario que se asegure de que el firewall no bloqueará la depuración remota. |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | VS, PS | Representa un puerto. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | Enviado por un puerto para comunicar eventos de puerto a cualquier agente de escucha. |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | Representa un puerto que puede iniciar y finalizar procesos. |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | Se utiliza para registrar y anular el registro de programas con un puerto; permite que el puerto realice un seguimiento de los programas que se están depurando actualmente. |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | Representa una interfaz de usuario personalizada para seleccionar el puerto. |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | VS | Representa una solicitud de un puerto desde el que se creará o ubicará un nuevo puerto. |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | Representa a un proveedor de puertos. |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | Representa un proveedor de puertos que pueden conservar (guardar en disco) información sobre los puertos que creó. |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | Permite [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] que la interfaz de usuario muestre texto dentro de la sección Información de **transporte** del cuadro de diálogo **Adjuntar al proceso.** |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | VS | Permite consultar información sobre el equipo de destino. |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | VS, PS | Representa una enumeración sobre un conjunto de puertos. |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | VS | Representa una enumeración sobre un conjunto de proveedores de puertos. |

## <a name="processes"></a><a name="Processes"></a>Procesos
 Estas interfaces representan procesos, un único ejecutable que contiene uno o más programas.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Representa un proceso que se ejecuta en un equipo.|
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Representa un proceso que admite activamente la depuración (se usa para reemplazar Step, Continue, y Execute métodos en el [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz).|
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Enviado por la DE o el puerto cuando se ha creado un proceso.|
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Enviado por el DE o el puerto cuando se ha destruido un proceso.|
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Representa un proceso que debe realizar un seguimiento de qué sesión está asociada a ella.|
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Representa una enumeración de un conjunto de procesos en un puerto.|

## <a name="programs"></a><a name="Programs"></a>Programas
 Estas interfaces representan programas, unidades lógicas de ejecución que no necesariamente corresponden a un ejecutable o módulo físico.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Representa un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que debe trabajar en conjunto con otros programas que se depuran al mismo tiempo.|
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Representa una unidad lógica de ejecución.|
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Enviado por la DE o el puerto cuando se ha creado un programa.|
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Enviado por el DE o puerto cuando un programa ha sido destruido.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Representa un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que se puede controlar mediante varios motores de depuración.|
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Representa un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que debe ser capaz de realizar un seguimiento de qué sesión está asociada a él.|
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Representa un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que puede devolver información sobre el proceso en el que se ejecuta.|
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Representa un programa que se puede depurar.|
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Permite que un nodo de programa reciba una notificación de un intento de adjuntar al programa asociado.|
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Proporciona una manera para que el SDM consulte un DE sobre los programas controlados por esa DE.|
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Utilizado por los DE para registrar los programas con el SDM para mostrar que se están depurando.|
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Representa un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que puede calcular referencias de interfaces a través de los límites de subprocesoo o proceso.|
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Representa una enumeración de un conjunto de programas.|

## <a name="properties"></a>Propiedades de <a name="Properties"></a>
 Estas interfaces representan propiedades, un valor asociado a un contexto determinado, normalmente el resultado de una evaluación de expresión.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Representa un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que puede mostrar su valor de una manera personalizada.|
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Representa un valor de un marco de pila, documento o el resultado de una evaluación de expresión.|
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Representa un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que admite cadenas arbitrariamente largas.|
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Enviado por el DE cuando se ha creado una nueva propiedad (representada por el [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfaz).|
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Enviado por el DE cuando una propiedad ha sido destruida.|
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Representa una referencia a una propiedad que puede existir fuera de cualquier marco de pila determinado.|
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Representa una enumeración sobre un conjunto de [estructuras DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) que describen variables, registros, parámetros y expresiones.|
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Representa una enumeración sobre un conjunto de [estructuras DEBUG_REFERENCE_INFO.](../../../extensibility/debugger/reference/debug-reference-info.md)|

## <a name="stack-frames"></a><a name="StackFrames"></a>Marcos de pila
 Estas interfaces representan un marco de pila, un contexto en el que se ha producido un punto de interrupción o una excepción.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Representa un contexto en el que se ha producido un punto de interrupción o una excepción.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Representa un [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) que puede controlar las excepciones interceptadas.|
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Representa una enumeración sobre el conjunto de [estructuras CODE_PATH](../../../extensibility/debugger/reference/code-path.md) que especifican la secuencia de llamada de función utilizada para llegar a un marco de pila determinado.|
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Representa una enumeración sobre un conjunto de estructuras [FRAMEINFO,](../../../extensibility/debugger/reference/frameinfo.md) que describen los marcos de pila.|

## <a name="threads"></a><a name="Threads"></a>Hilos
 Estas interfaces representan subprocesos y sus eventos asociados.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Representa un subproceso de ejecución.|
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Enviado por la DE cuando se ha creado un subproceso.|
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Enviado por el DE cuando se ha destruido un subproceso.|
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Enviado por la DE cuando un subproceso ha cambiado su nombre.|
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Representa una enumeración sobre un conjunto de subprocesos.|

## <a name="type-visualizers"></a><a name="TypeVisualizers"></a>Visualizadores de tipo
 Estas interfaces proporcionan compatibilidad con visualizadores de tipos. Estas interfaces normalmente las implementa un evaluador de expresiones.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Representa una matriz de bytes que se presentarán a un visualizador de tipos.|
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Proporciona métodos para obtener acceso a los datos que se pasarán a un visualizador de tipos.|
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Representa una propiedad que proporciona acceso a las implementaciones de [IPropertyProxyEESide.](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|

## <a name="see-also"></a>Vea también
- [Referencia de API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Creación de un motor de depuración personalizado](../../../extensibility/debugger/creating-a-custom-debug-engine.md)
