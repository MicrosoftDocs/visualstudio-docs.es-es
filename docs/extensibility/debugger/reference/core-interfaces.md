---
title: Principales Interfaces | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 54ecbe034f4fa7054be2725205a013e5899849e7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="core-interfaces"></a>Interfaces de núcleo
Las interfaces siguientes son las interfaces principales para ampliar el depurador mediante el [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="discussion"></a>Explicación  
 Estas interfaces se utilizan principalmente para crear el motor de depuración (Alemania). Se organizan aquí por categorías:  
  
-   [Puntos de interrupción](#Breakpoints)  
  
-   [Contextos](#Contexts)  
  
-   [Server Core](#CoreServer)  
  
-   [Motores de depuración](#DebugEngines)  
  
-   [Documentos](#Documents)  
  
-   [Eventos](#Events)  
  
-   [Expresiones](#Expressions)  
  
-   [Memoria](#Memory)  
  
-   [Módulos](#Modules)  
  
-   [Puertos](#Ports)  
  
-   [Procesos](#Processes)  
  
-   [Programas](#Programs)  
  
-   [Propiedades](#Properties)  
  
-   [Marcos de pila](#StackFrames)  
  
-   [Subprocesos](#Threads)  
  
-   [Visualizadores de tipo](#TypeVisualizers)  
  
 Las entidades que pueden implementar las interfaces son:  
  
-   Depurar motor (Alemania)  
  
-   Proveedor del puerto (PS)  
  
-   Evaluador de expresiones (EE)  
  
-   Visual Studio (VS)  
  
##  <a name="Breakpoints"></a>Puntos de interrupción  
 Estas interfaces están relacionados con la implementación y el seguimiento de los puntos de interrupción.  
  
|Interfaz|Implementado por|Descripción|  
|---------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Representa un punto de interrupción enlazado a una ubicación de memoria.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Enviados por el DE cuando un punto de interrupción se enlaza a una ubicación de memoria.|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Representa una suma de comprobación de documento para una solicitud de punto de interrupción.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Enviados por el DE cuando se produce un error en un punto de interrupción se puede enlazar a una ubicación de memoria.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Enviados por el DE cuando se alcanza un punto de interrupción.|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Representa una solicitud para un punto de interrupción; se utiliza para crear un punto de interrupción pendiente.|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Representa una solicitud para un punto de interrupción; se utiliza para crear un punto de interrupción pendiente.|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Representa la información utilizada para enlazar un punto de interrupción.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Enviados por el DE cuando un punto de interrupción es independiente de una ubicación de memoria.|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Representa un punto de interrupción no válido (devuelto por `IDebugBreakpointErrorEvent2`).|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Representa la información de resolución sobre un punto de interrupción no válido.|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Representa una posición en una función donde se establece un punto de interrupción.|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Representa un punto de interrupción que se puede enlazar; se utiliza para crear un punto de interrupción enlazado.|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Representa una enumeración a través de un conjunto de puntos de interrupción enlazados.|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Representa una enumeración a través de un conjunto de puntos de interrupción que no se pudo enlazar a una ubicación de memoria.|  
  
##  <a name="Contexts"></a>Contextos  
 Estas interfaces representan varios tipos de contextos dentro del programa que se está depurando.  
  
|Interfaz|Implementado por|Descripción|  
|---------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Representa la posición inicial de una instrucción de código.|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Extiende la [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) interfaz para habilitar la recuperación de las interfaces de módulo y proceso.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, ALEMANIA|Representa una posición en un documento.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Representa el contexto en el que se va a evaluar una expresión.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Representa la ubicación inicial en la memoria de una colección de bytes.|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Representa un contexto de marco de pila en un punto de interrupción o una excepción.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Representa un contexto de marco de pila en un punto de interrupción o una excepción.|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Representa una enumeración a través de un conjunto de contextos de código.|  
  
##  <a name="CoreServer"></a>Server Core  
 Estas interfaces representan la máquina en la que se está depurando un programa. Estos elementos se implementan por [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] pero puede llamarse en mediante motores de depuración.  
  
|Interfaz|Implementado por|Descripción|  
|---------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Proporciona acceso a los puertos y proveedores de puertos, así como información sobre el equipo.|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Representa un [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) que admite la depuración remota.|  
  
##  <a name="DebugEngines"></a>Motores de depuración  
 Estas interfaces representan como sus eventos asociados y los motores de depuración.  
  
|Interfaz|Implementado por|Descripción|  
|---------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Representa un motor de depuración personalizadas.|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Representa un motor de depuración personalizadas que admite la carga de símbolos, JustMyCode y excepciones.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Enviado por cada nueva instancia de la DE para indicar que está listo para controlar las tareas de depuración.|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Representa un motor de depuración personalizadas que permite iniciar programas.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|ALEMANIA, PS|Representa un nodo de programa que controla varios motores de depuración.|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Proporciona una manera para que el SDM obtener una interfaz para el motor de depuración de un subproceso, el programa o el marco de pila.|  
  
##  <a name="Documents"></a>Documentos  
 Estas interfaces representan documentos (archivos de origen) y sus elementos asociados.  
  
|Interfaz|Implementado por|Descripción|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Enviado por el DE para solicitar un documento que se abran.|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Representa una secuencia de instrucciones desensambladas de un documento.|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, ALEMANIA|Representa un documento proporcionado por el Alemania, especificando un nombre y un identificador de clase (CLSID).|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|ALEMANIA, EE|Representa una suma de comprobación para un documento de depuración y permite pasar la suma de comprobación entre los componentes.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, ALEMANIA|Representa un contexto de documento, una posición dentro de un documento correspondiente a un determinado contexto de instrucción y el código.|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, ALEMANIA|Representa una posición general dentro de un documento.|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Representa una posición en un archivo de código fuente como un desplazamiento de caracteres.|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, ALEMANIA|Representa un documento de texto proporcionado por el Alemania (derivado de [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), proporcionando el texto real.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Enviado por el DE especificar cambios en un archivo de origen que está en la memoria.|  
  
##  <a name="Events"></a> Eventos  
 Estas interfaces representan todos los eventos que se envían entre el Alemania y el Administrador de sesión de depuración (SDM).  
  
|Interfaz|Implementado por|Descripción|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Enviado por el DE para solicitar un documento que se abran.|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|El motor de depuración (Alemania) envía esta interfaz para el Administrador de sesión de depuración (SDM) para establecer el estado de mensaje en la barra durante la carga de símbolos.|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|Enviados por el DE cuando se ha completado una interrupción en el programa.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Enviados por el DE cuando se enlaza a un punto de interrupción.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Enviados por el DE cuando se produce un error en un punto de interrupción que enlazarse.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Enviados por el DE cuando se alcanza un punto de interrupción.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Enviados por el DE cuando un punto de interrupción no está enlazado.|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|Envía la DE para determinar si debe detenerse en una ubicación concreta.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Enviado por el DE especificar cambios en un archivo de origen que está en la memoria.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Enviado por cada nueva instancia de la DE para indicar que está listo para controlar las tareas de depuración.|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|Se envía por la DE para indicar el programa que se está depurando esté listo para ejecutar la primera instrucción.|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|Una interfaz que otras interfaces de eventos, que pueden devolver un error, se utiliza para proporcionar mensajes de error legible para el usuario.|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|ALEMANIA, PS|Interfaz base que todos los eventos otras interfaces se derivan.|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|VS|Representa una interfaz implementada por el SDM al que se envían eventos (expresados como objetos que implementan una interfaz de evento determinado).|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|Enviados por el DE cuándo se ha producido una excepción en el programa que se está depurando.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Enviados por el DE una vez completada una evaluación de expresiones asincrónica.|  
|IDebugFindSymbolEvent2||OBSOLETO. NO UTILICE.|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|Enviados por el DE cuando se haya completado el procesamiento de una excepción interceptada.|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|Enviados por el DE cuando un programa ha terminado de cargarse.|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|Enviados por la DE para que el IDE muestre un mensaje informativo al usuario.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Enviados por el DE cuando se carga o descarga un módulo.|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|Las señales de la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfaz de usuario para advertir al usuario que no se encuentra para el ejecutable iniciado símbolos del depurador.|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|Envía la DE para que el IDE muestre una cadena arbitraria.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|VS, ALEMANIA|Enviado por un puerto para comunicar eventos de puerto a cualquier agente de escucha.|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|ALEMANIA, PS|Enviados por el puerto o Alemania cuando se ha creado un proceso.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|ALEMANIA, PS|Enviados por el puerto o Alemania cuando se destruye un proceso.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|ALEMANIA, PS|Enviados por el puerto o Alemania cuando se ha creado un programa.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|ALEMANIA, PS|Enviados por el puerto o Alemania cuando se destruye un programa.|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|Permite que un motor de depuración invalidar el comportamiento predeterminado de la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfaz de usuario al finalizar una sesión de depuración.|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|Envía desde el motor de depuración (Alemania) para el Administrador de sesión de depuración (SDM) cuando cambia el nombre de un programa.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Enviando la Alemania cuando una nueva propiedad (representado por la `IDebugProperty2` interfaz) se ha creado.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Enviados por el DE cuando se destruye una propiedad.|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|Envía el Alemania cuando ejecución paso a paso fuera de o a través de una función de forma que el valor devuelto se puede mostrar correctamente.|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|VS|Habilita el motores para leer la configuración de la métrica de depuración remota.|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|Enviados por el DE cuando se ha completado un paso en, en o fuera de una instrucción.|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|Se envía por la DE para indicar el éxito o fracaso de la carga de símbolos para un módulo.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Enviados por el DE cuando se ha creado un subproceso.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Enviados por el DE cuando un subproceso se ha destruido.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Enviados por el DE cuando un subproceso ha cambiado su nombre.|  
  
##  <a name="Expressions"></a>Expresiones  
 Estas interfaces representan las expresiones se evalúan en un contexto determinado.  
  
|Interfaz|Implementado por|Descripción|  
|---------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Representa una expresión que se debe evaluar. Obtenido de la [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Representa un contexto en el que se evalúa una expresión. Obtenido de la [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interfaz.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Enviados por el DE una vez completada una evaluación de expresiones asincrónica.|  
  
##  <a name="Memory"></a>Memoria  
 Estas interfaces representan secuencias de bytes en memoria.  
  
|Interfaz|Implementado por|Descripción|  
|---------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Representa una secuencia de bytes de memoria que puede leer o escribir en.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Representa una ubicación de memoria de una secuencia de bytes.|  
  
##  <a name="Modules"></a> Módulos  
 Estas interfaces representan un módulo, que corresponde a un archivo ejecutable o. Archivo DLL.  
  
|Interfaz|Implementado por|Descripción|  
|---------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Representa un único ejecutable o DLL.|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Representa un [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) que admite los símbolos.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Enviados por el DE cuando se carga o descarga un módulo.|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Representa la información del servidor de origen que se encuentra en un archivo PDB.|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Representa una enumeración a través de un conjunto de módulos que se conocen por un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|  
  
##  <a name="Ports"></a>Puertos  
 Estas interfaces representan puertos y proveedores de puertos.  
  
|Interfaz|Implementado por|Descripción|  
|---------------|--------------------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VS, PS|Representa el puerto predeterminado en el equipo local.|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|VS|Permite que un motor de depuración que usa DCOM para pedir la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfaz de usuario para asegurarse de que el firewall no bloquee la depuración remota.|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VS, PS|Representa un puerto.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|Enviado por un puerto para comunicar eventos de puerto a cualquier agente de escucha.|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|Representa un puerto que se puede iniciar y finalizar procesos.|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|Usa para registrar y anular el registro de programas con un puerto; permite que el puerto realizar un seguimiento de los programas que se está depurados.|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|Representa una interfaz de usuario personalizada para seleccionar el puerto.|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|VS|Representa una solicitud para un puerto desde el que se creará o encuentra un nuevo puerto.|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|Representa un proveedor de puertos.|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|Representa un proveedor de puertos que puede hacer persistir (guardar en el disco) información sobre los puertos que creó.|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|Habilita la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfaz de usuario para mostrar el texto dentro de la **información de transporte** sección de la **adjuntar al proceso** cuadro de diálogo.|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|VS|Permite consultar para obtener información sobre el equipo de destino.|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VS, PS|Representa una enumeración a través de un conjunto de puertos.|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|VS|Representa una enumeración a través de un conjunto de proveedores de puertos.|  
  
##  <a name="Processes"></a>Procesos  
 Estas interfaces representan procesos, un único archivo ejecutable que contiene uno o más programas.  
  
|Interfaz|Implementado por|Descripción|  
|---------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, ALEMANIA|Representa un proceso que se ejecuta en un equipo.|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, ALEMANIA|Representa un proceso que admite activamente depuración (se utiliza para reemplazar el paso, continuar y ejecutar métodos en el [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz).|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|ALEMANIA, PS|Enviados por el puerto o Alemania cuando se ha creado un proceso.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|ALEMANIA, PS|Enviados por el puerto o Alemania cuando se destruye un proceso.|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Representa un proceso que debe realizar un seguimiento de qué sesión está asociada a él.|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Representa una enumeración de un conjunto de procesos en un puerto.|  
  
##  <a name="Programs"></a>Programas  
 Estas interfaces representan programas, unidades lógicas de ejecución que no corresponden necesariamente a un archivo ejecutable físico o un módulo.  
  
|Interfaz|Implementado por|Descripción|  
|---------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Representa un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que necesita trabajar junto con otros programas que se está depurados al mismo tiempo.|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|ALEMANIA, PS|Representa una unidad lógica de ejecución.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|ALEMANIA, PS|Enviados por el puerto o Alemania cuando se ha creado un programa.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|ALEMANIA, PS|Enviados por el puerto o Alemania cuando se destruye un programa.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|ALEMANIA, PS|Representa un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que pueda ser controlada por varios motores de depuración.|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Representa un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que debe ser capaz de realizar un seguimiento de qué sesión está asociada a él.|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|ALEMANIA, PS|Representa un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que puede devolver información sobre el proceso en el que se está ejecutando.|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|ALEMANIA, PS|Representa un programa que se puede depurar.|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|ALEMANIA, PS|Permite a un nodo de programa recibir una notificación de un intento para adjuntar al programa.|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Proporciona una manera para que el SDM consultar un Alemania acerca de los programas controlados por esa Alemania.|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Utiliza DEs para registrar programas con el SDM para mostrar que se están depurando.|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|ALEMANIA, PS|Representa un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que puede calcular las referencias de interfaces en los límites del proceso o subproceso.|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|ALEMANIA, PS|Representa una enumeración de un conjunto de programas.|  
  
##  <a name="Properties"></a> Propiedades  
 Estas interfaces representan las propiedades, un valor asociado a un contexto determinado, normalmente es el resultado de evaluación de una expresión.  
  
|Interfaz|Implementado por|Descripción|  
|---------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Representa un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que puede mostrar su valor de una manera personalizada.|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Representa un valor de un marco de pila, documento o el resultado de evaluación de una expresión.|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Representa un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que admite cadenas largas arbitrariamente.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Enviando la Alemania cuando una nueva propiedad (representado por la [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfaz) se ha creado.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Enviados por el DE cuando se destruye una propiedad.|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Representa una referencia a una propiedad que puede existir fuera de cualquier marco de pila determinado.|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Representa una enumeración a través de un conjunto de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estructuras que describen las variables, registros, parámetros y expresiones.|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Representa una enumeración a través de un conjunto de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estructuras.|  
  
##  <a name="StackFrames"></a>Marcos de pila  
 Estas interfaces representan un marco de pila y un contexto en que se ha producido un punto de interrupción o la excepción.  
  
|Interfaz|Implementado por|Descripción|  
|---------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Representa un contexto en que se ha producido un punto de interrupción o la excepción.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Representa un [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) que puede controlar intercepta excepciones.|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Representa una enumeración sobre el conjunto de [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) estructuras que especifican la función llamar a la secuencia que se utiliza para llegar a un marco de pila determinado.|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Representa una enumeración a través de un conjunto de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) las estructuras, que se describen los marcos de pila.|  
  
##  <a name="Threads"></a> Subprocesos  
 Estas interfaces representan los subprocesos y los eventos asociados.  
  
|Interfaz|Implementado por|Descripción|  
|---------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Representa un subproceso de ejecución.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Enviados por el DE cuando se ha creado un subproceso.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Enviados por el DE cuando un subproceso se ha destruido.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Enviados por el DE cuando un subproceso ha cambiado su nombre.|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Representa una enumeración a través de un conjunto de subprocesos.|  
  
##  <a name="TypeVisualizers"></a>Visualizadores de tipo  
 Estas interfaces proporcionan compatibilidad para los visualizadores de tipo. Estas interfaces se implementan normalmente mediante un evaluador de expresiones.  
  
|Interfaz|Implementado por|Descripción|  
|---------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Representa una matriz de bytes que se pueden presentar en un visualizador de tipo.|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Proporciona métodos para obtener acceso a los datos que se pasan a un visualizador de tipo.|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Representa una propiedad que proporciona acceso a [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) implementaciones.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Creación de un motor de depuración personalizado](../../../extensibility/debugger/creating-a-custom-debug-engine.md)