---
title: Principales de Interfaces | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33f2d4fda2fe7981863d65b17fc6dba53355dbeb
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56702283"
---
# <a name="core-interfaces"></a>Interfaces básicas
Las interfaces siguientes son las interfaces principales para ampliar el depurador mediante el uso de la [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].

## <a name="discussion"></a>Discusión
 Estas interfaces se utilizan principalmente para crear el motor de depuración (DE). Aquí están organizados por categorías:

- [Puntos de interrupción](#Breakpoints)

- [Contextos](#Contexts)

- [Core Server](#CoreServer)

- [Motores de depuración](#DebugEngines)

- [Documentos](#Documents)

- [Eventos](#Events)

- [Expresiones](#Expressions)

- [Memoria](#Memory)

- [Módulos](#Modules)

- [Puertos](#Ports)

- [Procesos](#Processes)

- [Programas](#Programs)

- [Propiedades](#Properties)

- [Marcos de pila](#StackFrames)

- [Subprocesos](#Threads)

- [Visualizadores de tipo](#TypeVisualizers)

  Las entidades que pueden implementar las interfaces son:

- (DE) del motor de depuración

- Proveedor del puerto (PS)

- Evaluador de expresiones (EE)

- Visual Studio (VS)

##  <a name="Breakpoints"></a> Puntos de interrupción
 Estas interfaces están relacionados con la implementación y realizar un seguimiento de los puntos de interrupción.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Representa un punto de interrupción enlazado a una ubicación de memoria.|
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Enviado por la DE cuando un punto de interrupción se enlaza a una ubicación de memoria.|
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Representa una suma de comprobación de documento para una solicitud de punto de interrupción.|
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Enviado por la DE cuando se produce un error en un punto de interrupción se enlace a una ubicación de memoria.|
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Enviado por la DE cuando se alcanza un punto de interrupción.|
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Representa una solicitud para un punto de interrupción; se utiliza para crear un punto de interrupción pendiente.|
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Representa una solicitud para un punto de interrupción; se utiliza para crear un punto de interrupción pendiente.|
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Representa la información que se usa para enlazar un punto de interrupción.|
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Enviado por la DE cuando un punto de interrupción es independiente de una ubicación de memoria.|
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Representa un punto de interrupción no válido (devuelto por `IDebugBreakpointErrorEvent2`).|
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Representa la información de resolución de un punto de interrupción no válido.|
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Representa una posición en una función donde se establece un punto de interrupción.|
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Representa un punto de interrupción que se enlaza; se utiliza para crear un punto de interrupción enlazado.|
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Representa una enumeración a través de un conjunto de puntos de interrupción enlazados.|
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Representa una enumeración a través de un conjunto de puntos de interrupción que no se pudo enlazar a una ubicación de memoria.|

##  <a name="Contexts"></a> Contextos
 Estas interfaces representan distintos tipos de contextos dentro del programa que se está depurando.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Representa la posición inicial de una instrucción de código.|
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Extiende la [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) interfaz para habilitar la recuperación de las interfaces de módulo y el proceso.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Representa una posición en un documento.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Representa el contexto en el que se va a evaluar una expresión.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Representa la ubicación inicial de una colección de bytes en memoria.|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Representa un contexto del marco de pila en un punto de interrupción o una excepción.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Representa un contexto del marco de pila en un punto de interrupción o una excepción.|
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Representa una enumeración a través de un conjunto de contextos de código.|

##  <a name="CoreServer"></a> Server Core
 Estas interfaces representan la máquina en la que se está depurando un programa. Estos elementos se implementan mediante [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] , pero puede llamar en los motores de depuración.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Proporciona acceso a los puertos y proveedores de puertos, así como información sobre el equipo.|
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Representa un [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) que admite la depuración remota.|

##  <a name="DebugEngines"></a> Motores de depuración
 Estas interfaces representan los motores de depuración y los eventos asociados.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Representa un motor de depuración.|
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Representa un motor de depuración personalizado que admite la carga de símbolos, JustMyCode y excepciones.|
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Enviado por cada nueva instancia de la DE para indicar que está preparado para controlar las tareas de depuración.|
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Representa un motor de depuración que es compatible con programas de inicio.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Representa un nodo de programa que controla varios motores de depuración.|
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Proporciona una forma para el SDM obtener una interfaz para el motor de depuración desde un subproceso, el programa o el marco de pila.|

##  <a name="Documents"></a> Documentos
 Estas interfaces representan documentos (archivos de origen) y sus elementos asociados.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Enviado por la DE para solicitar un documento que se abrirá.|
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Representa una secuencia de instrucciones desensambladas de un documento.|
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|Representa un documento proporcionado por la DE, especificando un nombre y un identificador de clase (CLSID).|
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|Representa una suma de comprobación para un documento de depuración y permite pasar la suma de comprobación entre los componentes.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Representa un contexto de documento, una posición dentro de un documento correspondiente a un determinado contexto de instrucción y el código.|
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|Representa una posición general dentro de un documento.|
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Representa una posición en un archivo de código fuente como un desplazamiento de caracteres.|
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|Representa un documento de texto proporcionado por la DE (derivado de [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), proporcionando el texto real.|
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Enviado por el DE especificar cambios en un archivo de origen que está en la memoria.|

##  <a name="Events"></a> Eventos
 Estas interfaces representan todos los eventos que se envían entre la DE y el Administrador de depuración de la sesión (SDM).


| Interfaz | Implementado por | Descripción |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | DE | Enviado por la DE para solicitar un documento que se abrirá. |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | DE | El motor de depuración (DE) envía esta interfaz para el Administrador de depuración (SDM) para establecer el estado de sesión mensaje barra durante las cargas de símbolos. |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | DE | Enviado por la DE cuando se haya completado una interrupción en el programa. |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | DE | Enviado por la DE cuando se enlaza a un punto de interrupción. |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | DE | Enviado por la DE cuando un punto de interrupción no se puede enlazar. |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | DE | Enviado por la DE cuando se alcanza un punto de interrupción. |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | DE | Enviado por la DE cuando se desenlaza un punto de interrupción. |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | DE | Enviado por la DE para determinar si se detiene en una ubicación concreta. |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | DE | Enviado por el DE especificar cambios en un archivo de origen que está en la memoria. |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | DE | Enviado por cada nueva instancia de la DE para indicar que está preparado para controlar las tareas de depuración. |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | DE | Enviado por la DE para indicar el programa que se está depurando está listo para ejecutar la primera instrucción. |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | DE | Interfaz que otras interfaces de eventos, que pueden devolver un error, se usa para proporcionar mensajes de error legible. |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | DE, PS | Interfaz base que todos los otros eventos interfaces se derivan. |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | VS | Representa una interfaz implementada por el SDM al que se envían los eventos (expresados como objetos que implementan una interfaz de evento determinado). |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | DE | Enviado por la DE cuando se ha producido una excepción en el programa que se está depurando. |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | DE | Enviado por la DE una vez completada una evaluación de expresión asincrónica. |
| IDebugFindSymbolEvent2 | | OBSOLETO. NO USE. |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | DE | Enviado por la DE cuando se haya completado el procesamiento de una excepción interceptada. |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | DE | Enviado por la DE un programa una vez finalizada la carga. |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | DE | Enviado por la DE tener la presentación IDE un mensaje informativo para el usuario. |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | DE | Enviado por la DE cuando se carga o descarga un módulo. |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | DE | Las señales del [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] la interfaz de usuario para advertir al usuario que no se encontró para el ejecutable iniciado los símbolos del depurador. |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | DE | Enviado por la DE tener la presentación IDE una cadena arbitraria. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | VS, DE | Enviado por un puerto para comunicar los eventos de puerto a cualquier agente de escucha. |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | DE, PS | Enviado por el puerto o DE cuando se ha creado un proceso. |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | DE, PS | Enviado por el puerto o DE cuando se destruye un proceso. |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | DE, PS | Enviado por el puerto o DE cuando se ha creado un programa. |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | DE, PS | Enviado por el puerto o DE cuando se destruye un programa. |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | DE | Permite que un motor de depuración invalidar el comportamiento predeterminado de la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] al finalizar una sesión de depuración de interfaz de usuario. |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | DE | Se envían desde el motor de depuración (DE) el Administrador de depuración de la sesión (SDM) cuando cambia el nombre de un programa. |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | DE | Enviado por la DE cuando una nueva propiedad (representado por la `IDebugProperty2` interfaz) se ha creado. |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | DE | Enviado por la DE cuando se destruye una propiedad. |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | DE | Enviado por la DE cuando la ejecución paso a paso fuera de o a través de una función para que el valor devuelto pueda mostrarse correctamente. |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | VS | Habilita los motores para leer la configuración de métrica de depuración remota. |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | DE | Enviado por la DE cuando se haya completado un paso en o a través o fuera de una instrucción. |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | DE | Enviado por la DE para indicar el éxito o fracaso de la carga de símbolos para un módulo. |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | DE | Enviado por la DE cuando un subproceso se ha creado. |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | DE | Enviado por la DE cuando un subproceso se ha destruido. |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | DE | Enviado por la DE cuando un subproceso ha cambiado su nombre. |

##  <a name="Expressions"></a> Expresiones
 Estas interfaces representan las expresiones se evalúan en un contexto determinado.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Representa una expresión que se va a evaluar. Obtenida la [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Representa un contexto en el que se evalúa una expresión. Obtenida la [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interfaz.|
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Enviado por la DE una vez completada una evaluación de expresión asincrónica.|

##  <a name="Memory"></a> Memoria
 Estas interfaces representan secuencias de bytes en memoria.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Representa una secuencia de bytes de memoria que puede leer o escribir en.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Representa una ubicación de memoria de una secuencia de bytes.|

##  <a name="Modules"></a> Módulos
 Estas interfaces representan un módulo, que corresponde a un archivo ejecutable o. Archivo DLL.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Representa un único archivo ejecutable o DLL.|
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Representa un [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) que admite los símbolos.|
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Enviado por la DE cuando se carga o descarga un módulo.|
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Representa la información del servidor de origen que se encuentra en un archivo PDB.|
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Representa una enumeración a través de un conjunto de módulos que se conocen por un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|

##  <a name="Ports"></a> Puertos
 Estas interfaces representan los puertos y los proveedores de puertos.


| Interfaz | Implementado por | Descripción |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | VS, PS | Representa el puerto predeterminado en el equipo local. |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | VS | Permite que un motor de depuración que se utiliza DCOM para pedir el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] la interfaz de usuario para asegurarse de que el firewall no bloquee la depuración remota. |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | VS, PS | Representa un puerto. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | Enviado por un puerto para comunicar los eventos de puerto a cualquier agente de escucha. |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | Representa un puerto que se puede iniciar y finalizar los procesos. |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | Usa para registrar y anular el registro de programas con un puerto; permite que el puerto realizar un seguimiento de los programas que se está depurados actualmente. |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | Representa una interfaz de usuario personalizada para seleccionar el puerto. |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | VS | Representa una solicitud para un puerto desde el que se creará o encuentra un nuevo puerto. |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | Representa un proveedor de puertos. |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | Representa un proveedor de puertos que puede conservar (guardar en disco) información sobre los puertos en que creó. |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | Habilita la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] la interfaz de usuario para mostrar el texto dentro de la **información de transporte** sección de la **asociar al proceso** cuadro de diálogo. |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | VS | Permite consultar para obtener información sobre el equipo de destino. |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | VS, PS | Representa una enumeración a través de un conjunto de puertos. |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | VS | Representa una enumeración a través de un conjunto de proveedores de puertos. |

##  <a name="Processes"></a> Procesos
 Estas interfaces representan los procesos, un único archivo ejecutable que contiene uno o más programas.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Representa un proceso que se ejecuta en un equipo.|
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Representa un proceso que apoya activamente depuración (se utiliza para reemplazar el paso, continuar y ejecutar métodos en el [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz).|
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Enviado por el puerto o DE cuando se ha creado un proceso.|
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Enviado por el puerto o DE cuando se destruye un proceso.|
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Representa un proceso que debe realizar un seguimiento de qué sesión está asociado a él.|
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Representa una enumeración de un conjunto de procesos en un puerto.|

##  <a name="Programs"></a> Programas
 Estas interfaces representan programas, las unidades lógicas de ejecución que no corresponden necesariamente a un archivo ejecutable físico o un módulo.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Representa un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que necesita para trabajar junto con otros programas que se está depurados al mismo tiempo.|
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Representa una unidad lógica de ejecución.|
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Enviado por el puerto o DE cuando se ha creado un programa.|
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Enviado por el puerto o DE cuando se destruye un programa.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Representa un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que pueden controlarse mediante varios motores de depuración.|
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Representa un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que deban ser capaces de realizar un seguimiento de qué sesión está asociado a él.|
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Representa un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que puede devolver información sobre el proceso en el que se está ejecutando.|
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Representa un programa que se puede depurar.|
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Permite que un nodo de programa recibir una notificación de un intento para adjuntar al programa.|
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Proporciona una forma para el SDM consultar un DE acerca de los programas controlados por esa DE.|
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Usa DEs para registrar programas con el SDM para mostrar que se están depurando.|
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Representa un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interfaces que puede serializar a través de límites de proceso o subproceso.|
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Representa una enumeración de un conjunto de programas.|

##  <a name="Properties"></a> Propiedades
 Estas interfaces representan las propiedades de un valor asociado a un contexto determinado, normalmente es el resultado de evaluación de una expresión.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Representa un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que puede mostrar su valor de una manera personalizada.|
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Representa un valor de un marco de pila, documento o el resultado de evaluación de una expresión.|
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Representa un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que admite cadenas largas arbitrariamente.|
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Enviado por la DE cuando una nueva propiedad (representado por la [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfaz) se ha creado.|
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Enviado por la DE cuando se destruye una propiedad.|
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Representa una referencia a una propiedad que puede existir fuera de cualquier marco de pila determinado.|
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Representa una enumeración a través de un conjunto de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estructuras que describen las variables, registros, parámetros y expresiones.|
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Representa una enumeración a través de un conjunto de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estructuras.|

##  <a name="StackFrames"></a> Marcos de pila
 Estas interfaces representan un marco de pila, un contexto en que se ha producido un punto de interrupción o excepción.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Representa un contexto en que se ha producido un punto de interrupción o excepción.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Representa un [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) que puede controlar intercepta las excepciones.|
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Representa una enumeración en el conjunto de [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) estructuras que especifican la función de llamar a la secuencia que se utiliza para llegar a un marco de pila determinado.|
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Representa una enumeración a través de un conjunto de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estructuras, donde se describen los marcos de pila.|

##  <a name="Threads"></a> Subprocesos
 Estas interfaces representan los subprocesos y los eventos asociados.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Representa un subproceso de ejecución.|
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Enviado por la DE cuando un subproceso se ha creado.|
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Enviado por la DE cuando un subproceso se ha destruido.|
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Enviado por la DE cuando un subproceso ha cambiado su nombre.|
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Representa una enumeración a través de un conjunto de subprocesos.|

##  <a name="TypeVisualizers"></a> Visualizadores de tipo
 Estas interfaces proporcionan compatibilidad con los visualizadores de tipo. Estas interfaces se implementan normalmente mediante un evaluador de expresiones.

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Representa una matriz de bytes que se presentará en un visualizador de tipo.|
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Proporciona métodos para obtener acceso a los datos que se pasará a un visualizador de tipo.|
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Representa una propiedad que proporciona acceso a [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) implementaciones.|

## <a name="see-also"></a>Vea también
- [Referencia de API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Creación de un motor de depuración personalizado](../../../extensibility/debugger/creating-a-custom-debug-engine.md)