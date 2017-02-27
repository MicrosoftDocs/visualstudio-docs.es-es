---
title: "Interfaces de n&#250;cleo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], interfaces de núcleo"
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Interfaces de n&#250;cleo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Las interfaces siguientes son las interfaces básicas para el depurador que extiende mediante [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## Explicación  
 Estas interfaces se utilizan principalmente para crear el motor de depuración \(DE\).  Se organizan aquí por categorías:  
  
-   [Puntos de interrupción](#Breakpoints)  
  
-   [contextos](#Contexts)  
  
-   [Servidor básico](#CoreServer)  
  
-   [Los motores de depuración](#DebugEngines)  
  
-   [Documentos](#Documents)  
  
-   [Eventos](#Events)  
  
-   [expresiones](#Expressions)  
  
-   [Memoria](#Memory)  
  
-   [Módulos](#Modules)  
  
-   [puertos](#Ports)  
  
-   [Procesos](#Processes)  
  
-   [Programas](#Programs)  
  
-   [Propiedades](#Properties)  
  
-   [marcos de pila](#StackFrames)  
  
-   [Subprocesos](#Threads)  
  
-   [Visualizadores de tipo](#TypeVisualizers)  
  
 Entidades que se pueden implementar las interfaces son:  
  
-   Motor de depuración \(DE\)  
  
-   Proveedor de puerto \(PS\)  
  
-   Evaluador de expresiones \(EE\)  
  
-   Visual Studio \(VS\)  
  
##  <a name="Breakpoints"></a> Puntos de interrupción  
 Estas interfaces están relacionados con la implementación y el seguimiento de puntos de interrupción.  
  
|Interfaz|Implementa por|Descripción|  
|--------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|representa un punto de interrupción enlazado a una ubicación de memoria.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Enviado por el OF cuando un punto de interrupción se enlaza a una ubicación de memoria.|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Representa una suma de comprobación del documento para una solicitud de punto de interrupción.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Enviado por el OF cuando un punto de interrupción no se debe enlazar a una ubicación de memoria.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Enviado por el OF cuando se alcanza un punto de interrupción.|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Representa una solicitud de un punto de interrupción; utilizado en crear un punto de interrupción pendiente.|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Representa una solicitud de un punto de interrupción; utilizado en crear un punto de interrupción pendiente.|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|representa la información utilizada para enlazar un punto de interrupción.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Enviado por el OF cuando un punto de interrupción se desenlaza de una ubicación de memoria.|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Representa un punto de interrupción no válido \(devuelto por `IDebugBreakpointErrorEvent2`\).|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Representa la información de resolución sobre un punto de interrupción no válido.|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|representa una posición en una función donde se establece un punto de interrupción.|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Representa un punto de interrupción que debe enlazarse; utilizado en crear un punto de interrupción enlazado.|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|representa una enumeración sobre un conjunto de puntos de interrupción enlazados.|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Representa una enumeración sobre un conjunto de puntos que no se puede enlazar a una ubicación de memoria.|  
  
##  <a name="Contexts"></a> contextos  
 Estas interfaces representan diversas clases de contextos dentro del programa que se depura.  
  
|Interfaz|Implementa por|Descripción|  
|--------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Representa la posición inicial de una instrucción de código.|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Extiende la interfaz de [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) para habilitar la recuperación del módulo y de interfaces de proceso.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, OF|representa una posición en un documento.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Representa el contexto en el que evaluar una expresión.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Representa la ubicación inicial en memoria de una colección de bytes.|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Representa un contexto del marco de pila en un punto de interrupción o una excepción.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Representa un contexto del marco de pila en un punto de interrupción o una excepción.|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Representa una enumeración sobre un conjunto de contextos de código.|  
  
##  <a name="CoreServer"></a> Servidor básico  
 Estas interfaces representan el equipo en el que se está depurando un programa.  Éstos son implementados por [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] pero se pueden llamar a por los motores de depuración.  
  
|Interfaz|Implementa por|Descripción|  
|--------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Proporciona acceso a los puertos y proveedores de puerto así como la información del equipo.|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Representa [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) que admite la depuración remota.|  
  
##  <a name="DebugEngines"></a> Los motores de depuración  
 Estas interfaces representan los motores de depuración y sus eventos asociado.  
  
|Interfaz|Implementa por|Descripción|  
|--------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Representa un motor de depuración.|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Representa un motor de depuración que admite la carga de símbolos, de JustMyCode, y de excepciones.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Enviado por cada nueva instancia de para indicar está listo para controlar las tareas de depuración.|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Representa un motor de depuración que admita iniciar programas.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|OF, PS|Representa un nodo de programa que controle los motores varias de depuración.|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Proporciona una manera para que el SDM obtenga una interfaz al motor de depuración de un subproceso, un programa, o de un marco de pila.|  
  
##  <a name="Documents"></a> Documentos  
 Estas interfaces representan los documentos \(archivos de código fuente\) y sus elementos asociados.  
  
|Interfaz|Implementa por|Descripción|  
|--------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Enviado por el OF para solicitar un documento que se abrirá.|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|representa una secuencia de instrucciones desensambladas de un documento.|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, OF|Representa un documento proporcionado por el OF, especificando un nombre y un identificador de clase \(CLSID\).|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|OF, EE|Representa una suma de comprobación para un documento de depuración y permite pasar la suma de comprobación entre los componentes.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, OF|Representa un contexto del documento, una posición dentro de un documento correspondiente en un contexto determinado de la instrucción y el código.|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, OF|representa una posición general dentro de un documento.|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Representa una posición en un archivo de código fuente como desplazamiento de caracteres.|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, OF|Representa un documento de texto proporcionado por el OF \(derivado de [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)\), proporcionando el texto real.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Enviado por el OF para especificar los cambios en un archivo de código fuente que está en memoria.|  
  
##  <a name="Events"></a> Eventos  
 Estas interfaces representan todos los eventos que se envían entre el OF y el administrador de depuración de la sesión \(SDM\).  
  
|Interfaz|Implementa por|Descripción|  
|--------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Enviado por el OF para solicitar un documento que se abrirá.|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|El motor de depuración \(DE\) envía esta interfaz al administrador \(SDM\) de depuración de la sesión para establecer el mensaje de la barra de estado durante carga de símbolos.|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|Enviado por el OF cuando una interrupción del programa se ha completado.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Enviado por el OF cuando se enlaza un punto de interrupción.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Enviado por el OF cuando un punto de interrupción no puede para el enlace.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Enviado por el OF cuando se alcanza un punto de interrupción.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Enviado por el OF cuando un punto de interrupción es independiente.|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|Enviado por el OF para determinar si debe detener en una ubicación determinada.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Enviado por el OF para especificar los cambios en un archivo de código fuente que está en memoria.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Enviado por cada nueva instancia de para indicar está listo para controlar las tareas de depuración.|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|Enviado por el OF para indicar el programa que se depura está lista para ejecutar la primera instrucción.|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|Una interfaz utilizada por otras interfaces de eventos, que pueden devolver un error, proporcionar mensajes de error legibles.|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|OF, PS|Interfaz base de la que el resto de las interfaces de eventos son derivadas.|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|VS|Representa una interfaz implementada por el SDM al que los eventos \(expresados como objetos que implementan una interfaz determinada de eventos\) se envían.|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|Enviado por el OF cuando se ha producido una excepción en el programa que se depura.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Enviado por el OF cuando se completa una evaluación asincrónica de la expresión.|  
|IDebugFindSymbolEvent2||OBSOLETO.  NOT UTILICE.|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|Enviado por el OF cuando el procesamiento para una excepción intercepta ha finalizado.|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|Enviado por el OF cuando un programa ha completado la carga.|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|Enviado por el OF para tener la presentación del IDE un mensaje informativo al usuario.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Enviado por el OF cuando se carga un módulo o descargar.|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|Señala la interfaz de usuario del depurador de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] de advertir al usuario que los símbolos no se puede encontrar para el ejecutable iniciada.|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|Enviado por el OF para tener la presentación del IDE una cadena arbitraria.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|VS, OF|Enviado por un puerto para comunicar eventos de puerto a cualquier agente de escucha.|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|OF, PS|Enviado por el OF o puerto cuando se ha creado un proceso.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|OF, PS|Enviado por el OF o puerto cuando se ha destruido un proceso.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|OF, PS|Enviado por el OF o puerto cuando se ha creado un programa.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|OF, PS|Enviado por el OF o puerto cuando se ha destruido un programa.|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|Permite a un motor de depuración para invalidar el comportamiento predeterminado de la interfaz de usuario de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]al finalizar una sesión de depuración.|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|Enviado del motor de \(DE\) depuración al administrador de depuración de \(SDM\) sesión al nombre de un programa.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Enviado por el OF cuando una nueva propiedad \(representada por la interfaz de `IDebugProperty2` \) se ha creado.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Enviado por el OF cuando se ha destruido una propiedad.|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|Enviado por el OF cuando la entrada o acerca de una función para que el valor devuelto puede correctamente mostrar.|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|VS|Los motores de depuración de los permisos para leer valores métrica de forma remota.|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|Enviado por el OF cuando un paso en, en, o fuera de una instrucción ha finalizado.|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|Enviado por el OF para indicar el éxito o error de cargar símbolos para un módulo.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Enviado por el OF cuando se ha creado un subproceso.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Enviado por el OF cuando se ha destruido un subproceso.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Enviado por el OF cuando un subproceso ha cambiado el nombre.|  
  
##  <a name="Expressions"></a> expresiones  
 estas interfaces representan las expresiones que se evaluarán en un contexto determinado.  
  
|Interfaz|Implementa por|Descripción|  
|--------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Representa una expresión que se evalúe.  obtenido de la interfaz de [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) .|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Representa un contexto en el que se evalúa una expresión.  obtenido de la interfaz de [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) .|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Enviado por el OF cuando se completa una evaluación asincrónica de la expresión.|  
  
##  <a name="Memory"></a> Memoria  
 estas interfaces representan secuencias de bytes en memoria.  
  
|Interfaz|Implementa por|Descripción|  
|--------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Representa una secuencia de bytes en memoria de la que pueda leer o escribir en él.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|representa una ubicación en memoria de una secuencia de bytes.|  
  
##  <a name="Modules"></a> Módulos  
 Estas interfaces representan un módulo, que corresponde a un ejecutable o el archivo .DLL.  
  
|Interfaz|Implementa por|Descripción|  
|--------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Representa una única aplicación ejecutable o DLL.|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|representa [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) que admite símbolos.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Enviado por el OF cuando se carga un módulo o descargar.|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Representa la información del servidor de origen que contenga un archivo PDB.|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Representa una enumeración sobre un conjunto de módulos que son conocidos por [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|  
  
##  <a name="Ports"></a> puertos  
 Estas interfaces representan puertos y los proveedores de puerto.  
  
|Interfaz|Implementa por|Descripción|  
|--------------|--------------------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VS, PS|representa el puerto predeterminado en el equipo local.|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|VS|Habilita un motor de depuración que usa DCOM para solicitar la interfaz de usuario de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] para asegurarse de que un firewall no bloquee la depuración remota.|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VS, PS|representa un puerto.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|Enviado por un puerto para comunicar eventos de puerto a cualquier agente de escucha.|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|Representa un puerto que pueda iniciar y finalizar procesos.|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|Se utiliza para registrar y programas de registro con un puerto; permite que el puerto siga los programas que se están depurando actualmente.|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|representa una interfaz de usuario personalizada para seleccionar el puerto.|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|VS|Representa una solicitud de un puerto de que un nuevo puerto se crea o encuentra.|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|representa un proveedor de puertos.|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|Representa un proveedor de los puertos que pueden conservarse \(guardar en disco\) información sobre los puertos que creó.|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|Permite que la interfaz de usuario de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] para mostrar texto dentro de la sección de **Información de transporte** del cuadro de diálogo de **Adjuntar a procesar** .|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|VS|Permite el consultar información sobre el equipo de destino.|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VS, PS|representa una enumeración sobre un conjunto de puertos.|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|VS|Representa una enumeración sobre un conjunto de proveedores de puerto.|  
  
##  <a name="Processes"></a> Procesos  
 Estas interfaces representan los procesos, una única aplicación ejecutable que contiene uno o más programas.  
  
|Interfaz|Implementa por|Descripción|  
|--------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, OF|Representa un proceso que se está ejecutando en un equipo.|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, OF|Representa un proceso que admita activamente la depuración \(utilizada para reemplazar el paso, Continuar, y ejecuta los métodos en la interfaz de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) \).|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|OF, PS|Enviado por el OF o puerto cuando se ha creado un proceso.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|OF, PS|Enviado por el OF o puerto cuando se ha destruido un proceso.|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Representa un proceso que debe seguir asociado a la sesión en el.|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|representa una enumeración de un conjunto de procesos en un puerto.|  
  
##  <a name="Programs"></a> Programas  
 Estas interfaces representan los programas, unidades lógicas de ejecución que no se corresponden necesariamente con una aplicación ejecutable o módulo física.  
  
|Interfaz|Implementa por|Descripción|  
|--------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Representa [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que necesita trabajar en combinación con otros programas que se están depurando al mismo tiempo.|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|OF, PS|representa una unidad lógica de ejecución.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|OF, PS|Enviado por el OF o puerto cuando se ha creado un programa.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|OF, PS|Enviado por el OF o puerto cuando se ha destruido un programa.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|OF, PS|Representa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que se puede administrar por los motores varias de depuración.|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Representa [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que debe poder seguir asociado a la sesión en el.|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|OF, PS|Representa [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que puede devolver información sobre el proceso en el que se está ejecutando.|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|OF, PS|Representa un programa que puede depurar.|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|OF, PS|Permite que un nodo del programa se notifique de un intento de asociar el programa asociado.|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Proporciona una manera para que el SDM vea un OF sobre los programas dirigidos por ese OF.|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Utilizado por el DES para registrar los programas con el SDM para mostrar que se están depurando.|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|OF, PS|Representa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que pueden calcular interfaces a través de subprocesos o procesos límites.|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|OF, PS|Representa una enumeración de un conjunto de software.|  
  
##  <a name="Properties"></a> Propiedades  
 Estas interfaces representan las propiedades, un valor asociado con un contexto concreto, normalmente el resultado de una evaluación de la expresión.  
  
|Interfaz|Implementa por|Descripción|  
|--------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Representa [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que puede mostrar el valor de una manera personalizada.|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Representa un valor de un marco de pila, documentos, o el resultado de una evaluación de la expresión.|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Representa [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que admite arbitrariamente cadenas largas.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Enviado por el OF cuando una nueva propiedad \(representada por la interfaz de [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) \) se ha creado.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Enviado por el OF cuando se ha destruido una propiedad.|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Representa una referencia a una propiedad que existir fuera de cualquier marco de pila determinado.|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Representa una enumeración sobre un conjunto de estructuras de [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) que describen variables, registros, los parámetros, y las expresiones.|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|representa una enumeración sobre un conjunto de estructuras de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .|  
  
##  <a name="StackFrames"></a> marcos de pila  
 Estas interfaces representan un marco de pila, un contexto en el que un punto de interrupción o se ha producido una excepción.  
  
|Interfaz|Implementa por|Descripción|  
|--------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Representa un contexto en el que un punto de interrupción o se ha producido una excepción.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Representa [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) que puedan controlar excepciones interceptadas.|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Representa una enumeración sobre el conjunto de estructuras de [CODE\_PATH](../../../extensibility/debugger/reference/code-path.md) que especifican la secuencia de llamada de función utilizada para proteger un marco de pila determinado.|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|representa una enumeración sobre un conjunto de estructuras de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) , que describen los marcos de pila.|  
  
##  <a name="Threads"></a> Subprocesos  
 estas interfaces representan los subprocesos y sus eventos asociado.  
  
|Interfaz|Implementa por|Descripción|  
|--------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Representa un subproceso de ejecución.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Enviado por el OF cuando se ha creado un subproceso.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Enviado por el OF cuando se ha destruido un subproceso.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Enviado por el OF cuando un subproceso ha cambiado el nombre.|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Representa una enumeración sobre un grupo de subprocesos.|  
  
##  <a name="TypeVisualizers"></a> Visualizadores de tipo  
 Estas interfaces proporcionan compatibilidad para los visualizadores escritos.  Estas interfaces se implementan normalmente por un evaluador de expresiones.  
  
|Interfaz|Implementa por|Descripción|  
|--------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Representa una matriz de bytes que se mostrarán un visualizador de tipo.|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Proporciona métodos para obtener acceso a los datos que se va a pasar a un visualizador del tipo.|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Representa una propiedad que proporciona acceso a las implementaciones de [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) .|  
  
## Vea también  
 [Referencia de API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Creación de un motor de depuración](../../../extensibility/debugger/creating-a-custom-debug-engine.md)