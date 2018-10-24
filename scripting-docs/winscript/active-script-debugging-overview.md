---
title: Información general acerca de la depuración de Active Script | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Active Script Debugging overview
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 447a8faf6e62448e7e8ce9ee8d7d8097fba2dd7b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919369"
---
# <a name="active-script-debugging-overview"></a>Información general acerca de la depuración de Active Script
Las interfaces de depuración de Active Script permiten la depuración independiente del idioma y del host, y admiten una amplia variedad de entornos de desarrollo.  
  
 ![Proceso de host de scripts](../winscript/media/scp56activdbgarchgif.gif "Scp56ActivDbgArchgif")  
Figura 1  
  
 Un entorno de depuración independiente del idioma puede admitir cualquier lenguaje de programación o una combinación de lenguajes de programación, sin necesidad de tener conocimientos específicos sobre cualquiera de estos lenguajes. El entorno de depuración también admite ejecutar instrucciones paso a paso entre lenguajes, así como puntos de interrupción. Esta información general se centra principalmente en la compatibilidad con lenguajes de scripting, como VBScript y [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
 Un depurador independiente del host se puede utilizar automáticamente con cualquier host de Active Scripting, como Internet Explorer o un host personalizado. El host controla lo que el depurador presenta al usuario, desde la estructura del árbol del documento hasta el contenido y el color de la sintaxis de los documentos de depuración. Esto permite que el código fuente depurado se muestre en el contexto del documento host. Por ejemplo, Internet Explorer puede mostrar un script en una página HTML.  
  
 En las subsecciones siguientes, se describen los componentes clave de la depuración activa y sus interfaces asociadas. Sin embargo, antes de continuar, se deben definir varios conceptos clave de la depuración activa:  
  
 aplicación host  
 La aplicación que hospeda los motores de script y que proporciona un conjunto de objetos (o "modelo de objetos") que permiten ejecutar scripts.  
  
 motor de lenguaje  
 Un componente que proporciona abstracciones de análisis, ejecución y depuración para un lenguaje determinado.  
  
 IDE del depurador  
 La aplicación que proporciona la interfaz de usuario de depuración mediante la comunicación con la aplicación host y los motores de lenguaje.  
  
 administrador de depuración de la máquina  
 Un componente que mantiene un registro de los procesos de aplicaciones que se pueden depurar.  
  
 administrador de depuración del proceso  
 Un componente que mantiene el árbol de documentos que se pueden depurar para una aplicación concreta, realiza un seguimiento de los subprocesos en ejecución, etcétera.  
  
 contexto de documento  
 Un contexto de documento es una abstracción que representa un intervalo específico en el código fuente de un documento host.  
  
 contexto de código  
 Un contexto de código representa una ubicación determinada en el código de ejecución de un motor de lenguaje (un "puntero de instrucción virtual").  
  
 contexto de expresión  
 Un contexto determinado (por ejemplo, un marco de pila) en el que un motor de lenguaje puede evaluar expresiones.  
  
 exploración de objetos  
 Una representación estructurada, e independiente del lenguaje, del nombre, el tipo, el valor y los subobjetos de un objeto, adecuada para implementar una interfaz de usuario "ventana de inspección".  
  
 A continuación se ofrece información general sobre cada uno de los componentes clave de la depuración activa y sus interfaces correspondientes y asociadas, seguido de los detalles de dichas interfaces.  
  
## <a name="language-engine"></a>Motor de lenguaje  
 El motor de lenguaje proporciona:  
  
- Análisis y ejecución del lenguaje.  
  
- Compatibilidad con la depuración (puntos de interrupción, etcétera).  
  
- Evaluación de expresiones.  
  
- Colores de la sintaxis.  
  
- Exploración de objetos.  
  
- Enumeración de pila y análisis.  
  
  A continuación se muestran las interfaces que un motor de scripts debe admitir para proporcionar depuración, evaluación de expresiones y exploración de objetos. La aplicación host utiliza estas interfaces para asignarlas entre su contexto de documento y los contextos de código del motor; la interfaz de usuario del depurador también las usa para llevar a cabo la evaluación de expresiones, la enumeración de pila y la exploración de objetos.  
  
  [IActiveScriptDebug (Interfaz)](../winscript/reference/iactivescriptdebug-interface.md)  
  Proporciona el color de la sintaxis y la enumeración del contexto de código.  
  
  [IActiveScriptErrorDebug (Interfaz)](../winscript/reference/iactivescripterrordebug-interface.md)  
  Devuelve contextos de documento y marcos de pila con errores.  
  
  [IActiveScriptSiteDebug (Interfaz)](../winscript/reference/iactivescriptsitedebug-interface.md)  
  Vínculo que el host proporciona desde el motor de scripts al depurador.  
  
  [IDebugCodeContext (Interfaz)](../winscript/reference/idebugcodecontext-interface.md)  
  Proporciona un "puntero de instrucción" virtual en un subproceso.  
  
  [IEnumDebugCodeContexts (Interfaz)](../winscript/reference/ienumdebugcodecontexts-interface.md)  
  Enumera los contextos de código que corresponden a un contexto de documento.  
  
  [IDebugStackFrame (Interfaz)](../winscript/reference/idebugstackframe-interface.md)  
  Representa un marco de pila lógico en la pila de subprocesos.  
  
  [IDebugExpressionContext (Interfaz)](../winscript/reference/idebugexpressioncontext-interface.md)  
  Proporciona el contexto en el que se pueden evaluar expresiones.  
  
  [IDebugStackFrameSniffer (Interfaz)](../winscript/reference/idebugstackframesniffer-interface.md)  
  Proporciona una manera para enumerar los marcos de pila lógicos.  
  
  [IDebugExpression (Interfaz)](../winscript/reference/idebugexpression-interface.md)  
  Representa una expresión evaluada de forma asincrónica.  
  
  [IDebugSyncOperation (Interfaz)](../winscript/reference/idebugsyncoperation-interface.md)  
  Permite que un motor de scripts realice una abstracción de una operación que debe llevarse a cabo mientras esté anidada en un determinado subproceso bloqueado.  
  
  [IDebugAsyncOperation (Interfaz)](../winscript/reference/idebugasyncoperation-interface.md)  
  Proporciona acceso asincrónico a una operación de depuración sincrónica.  
  
  [IDebugAsyncOperationCallBack (Interfaz)](../winscript/reference/idebugasyncoperationcallback-interface.md)  
  Proporciona eventos de estado relacionados con el progreso de la evaluación de una interfaz `IDebugAsyncOperation`.  
  
  [IEnumDebugExpressionContexts (Interfaz)](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  Enumera una colección de objetos `IDebugExpressionContexts`.  
  
  [IProvideExpressionContexts (Interfaz)](../winscript/reference/iprovideexpressioncontexts-interface.md)  
  Proporciona una manera de enumerar los contextos de expresión que un componente determinado conoce.  
  
  [IDebugFormatter (Interfaz)](../winscript/reference/idebugformatter-interface.md)  
  Permite que un lenguaje o el IDE personalice la conversión entre valores VARIANT o tipos VARTYPE y cadenas.  
  
  [IDebugStackFrameSnifferEx (Interfaz)](../winscript/reference/idebugstackframesnifferex-interface.md)  
  Enumera los marcos de pila lógicos para el PDM.  
  
## <a name="hosts"></a>Hosts  
 El host:  
  
- Hospeda los motores de lenguaje.  
  
- Proporciona un modelo de objetos (conjunto de objetos que pueden incluirse en scripts).  
  
- Define un árbol de documentos que se pueden depurar y su contenido.  
  
- Organiza los scripts en aplicaciones virtuales.  
  
  Existen dos tipos de hosts:  
  
- Un host no inteligente solo admite las interfaces básicas de Active Scripting. No tiene ningún control sobre la estructura del documento ni las organizaciones; los scripts que proporcionan los motores de lenguaje determinan por completo dicho control.  
  
- Un host inteligente admite un conjunto mayor de interfaces que le permiten definir el árbol del documento, el contenido del documento y el color de la sintaxis. Existe un conjunto de interfaces del asistente, descritas en la subsección siguiente, que facilitan que un host sea inteligente.  
  
### <a name="smart-host-helper-interfaces"></a>Interfaces del asistente para hosts inteligentes  
 Los métodos `IDebugDocumentHelper` proporcionan un conjunto muy simplificado de interfaces que un host puede utilizar para obtener las ventajas del hospedaje inteligente sin tener que controlar la complejidad (y la eficacia) completa de las interfaces de host completas.  
  
 Por supuesto, no es necesario que un host utilice estas interfaces. Sin embargo, con ellas puede evitar implementar o usar una serie de interfaces más complicadas.  
  
 [IDebugDocumentHelper (Interfaz)](../winscript/reference/idebugdocumenthelper-interface.md)  
 Implementada por PDM, proporciona implementaciones para muchas interfaces necesarias para el hospedaje inteligente.  
  
 [IDebugDocumentHost (Interfaz)](../winscript/reference/idebugdocumenthost-interface.md)  
 El host la implementa (opcionalmente) para exponer la funcionalidad específica del host, como el color de la sintaxis, al depurador.  
  
 Para obtener más información, consulte [Implementación de interfaces del asistente para hosts inteligentes](../winscript/implementing-smart-host-helper-interfaces.md).  
  
### <a name="full-smart-host-interfaces"></a>Interfaces completas para hosts inteligentes  
 A continuación se incluye el conjunto completo de interfaces que un host inteligente debe implementar o utilizar si no está usando las interfaces del asistente.  
  
 Interfaces que implementa el host:  
  
 [IDebugDocumentInfo (Interfaz)](../winscript/reference/idebugdocumentinfo-interface.md)  
 Proporciona información sobre un documento, del que se puede, o no, crear una instancia.  
  
 [IDebugDocumentProvider (Interfaz)](../winscript/reference/idebugdocumentprovider-interface.md)  
 Proporciona los medios para crear instancias de un documento a petición.  
  
 [IDebugDocument (Interfaz)](../winscript/reference/idebugdocument-interface.md)  
 Interfaz base para todos los documentos de depuración.  
  
 [IDebugDocumentText (Interfaz)](../winscript/reference/idebugdocumenttext-interface.md)  
 Proporciona acceso a una versión de solo texto del documento de depuración.  
  
 [IDebugDocumentTextAuthor (Interfaz)](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 Permite editar una versión de solo texto del documento de depuración.  
  
 [IDebugDocumentContext (Interfaz)](../winscript/reference/idebugdocumentcontext-interface.md)  
 Proporciona una representación abstracta de una parte del documento que se está depurando.  
  
 Interfaces que PDM implementa en nombre del host:  
  
 [IDebugApplicationNode (Interfaz)](../winscript/reference/idebugapplicationnode-interface.md)  
 Proporciona un contexto dentro de un árbol de proyectos para extender la funcionalidad de la interfaz `IDebugDocumentProvider`.  
  
## <a name="debugger-ide"></a>IDE del depurador  
 El IDE es una interfaz de usuario de depuración independiente del lenguaje. Proporciona lo siguiente:  
  
- Visores o editores de documentos.  
  
- Administración de puntos de interrupción.  
  
- Evaluación de expresiones y ventanas de inspección.  
  
- Examinación de marcos de pila.  
  
- Examinación de objetos o clases.  
  
- Examinación de la estructura de aplicaciones virtuales.  
  
  Interfaces que implementa el depurador:  
  
  [IApplicationDebugger (Interfaz)](../winscript/reference/iapplicationdebugger-interface.md)  
  La interfaz principal que una sesión IDE del depurador expone.  
  
  [IApplicationDebuggerUI (Interfaz)](../winscript/reference/iapplicationdebuggerui-interface.md)  
  Proporciona a un componente externo mayor control sobre la interfaz de usuario (UI) del depurador.  
  
  [IDebugExpressionCallBack (Interfaz)](../winscript/reference/idebugexpressioncallback-interface.md)  
  Proporciona eventos de estado para el progreso de la evaluación de `IDebugExpression`.  
  
  [IDebugDocumentTextEvents (Interfaz)](../winscript/reference/idebugdocumenttextevents-interface.md)  
  Proporciona eventos que indican los cambios realizados en el documento de texto asociado.  
  
  [IDebugApplicationNodeEvents (Interfaz)](../winscript/reference/idebugapplicationnodeevents-interface.md)  
  Proporciona la interfaz de eventos para la interfaz `IDebugApplicationNode`.  
  
### <a name="machine-debug-manager"></a>Administrador de depuración de la máquina  
 El administrador de depuración de la máquina mantiene y enumera una lista de aplicaciones virtuales activas para proporcionar el punto de enlace entre las aplicaciones virtuales y los depuradores.  
  
 [IDebugSessionProvider (Interfaz)](../winscript/reference/idebugsessionprovider-interface.md)  
 Establece una sesión de depuración para una aplicación en ejecución.  
  
 [IMachineDebugManager (Interfaz)](../winscript/reference/imachinedebugmanager-interface.md)  
 Interfaz principal del administrador de depuración de la máquina.  
  
 [IMachineDebugManagerCookie (Interfaz)](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 Es similar a la interfaz `IMachineDebugManager`, pero esta admite cookies de depuración.  
  
 [IMachineDebugManagerEvents (Interfaz)](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 Indica los cambios aplicados a la lista de aplicaciones en ejecución que mantiene el administrador de depuración de la máquina.  
  
 [IEnumRemoteDebugApplications (Interfaz)](../winscript/reference/ienumremotedebugapplications-interface.md)  
 Enumera las aplicaciones en ejecución en una máquina.  
  
### <a name="process-debug-manager"></a>Administrador de depuración del proceso  
 El PDM hace lo siguiente:  
  
- Sincroniza la depuración de varios motores de lenguaje.  
  
- Mantiene un árbol de documentos que se pueden depurar.  
  
- Combina marcos de pila.  
  
- Coordina los puntos de interrupción y la ejecución de instrucciones paso a paso a través de motores de lenguaje.  
  
- Hace un seguimiento de los subprocesos.  
  
- Mantiene un subproceso del depurador para el procesamiento asincrónico.  
  
- Se comunica con el administrador de depuración de la máquina y el IDE del depurador.  
  
  A continuación se indican las interfaces que proporciona el administrador de depuración del proceso.  
  
  [IProcessDebugManager (Interfaz)](../winscript/reference/iprocessdebugmanager-interface.md)  
  Interfaz principal del administrador de depuración del proceso. Esta interfaz puede crear, agregar o quitar una aplicación virtual de un proceso.  
  
  [IRemoteDebugApplication (Interfaz)](../winscript/reference/iremotedebugapplication-interface.md)  
  Representa una aplicación en ejecución.  
  
  [IDebugApplication (Interfaz)](../winscript/reference/idebugapplication-interface.md)  
  Expone métodos de depuración no remotos para que los utilicen hosts y motores de lenguaje.  
  
  [IRemoteDebugApplicationThread (Interfaz)](../winscript/reference/iremotedebugapplicationthread-interface.md)  
  Representa un subproceso de ejecución dentro de una aplicación determinada.  
  
  [IDebugApplicationThread (Interfaz)](../winscript/reference/idebugapplicationthread-interface.md)  
  Permite que los motores de lenguaje y los hosts proporcionen la sincronización de subprocesos y mantengan la información de estado de depuración específica de un subproceso.  
  
  [IEnumRemoteDebugApplicationThreads (Interfaz)](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  Enumera los subprocesos en ejecución en una aplicación.  
  
  [IDebugThreadCall (Interfaz)](../winscript/reference/idebugthreadcall-interface.md)  
  Envía las llamadas serializadas.  
  
  [IDebugApplicationNode (Interfaz)](../winscript/reference/idebugapplicationnode-interface.md)  
  Mantiene la posición de un documento en la jerarquía.  
  
  [IEnumDebugApplicationNodes (Interfaz)](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  Enumera los nodos secundarios de un nodo asociado a una aplicación.  
  
  [IEnumDebugStackFrames (Interfaz)](../winscript/reference/ienumdebugstackframes-interface.md)  
  Enumera los marcos de pila correspondientes a un subproceso, combinado a partir de los motores.  
  
  [IDebugCookie (Interfaz)](../winscript/reference/idebugcookie-interface.md)  
  Permite que la cookie de depuración se establezca en los depuradores de scripts.  
  
  [IDebugHelper (Interfaz)](../winscript/reference/idebughelper-interface.md)  
  Actúa para los motores de script como una fábrica para los exploradores de objetos y los puntos de conexión simples.  
  
  [ISimpleConnectionPoint (Interfaz)](../winscript/reference/isimpleconnectionpoint-interface.md)  
  Proporciona a los motores de script una manera sencilla de describir y enumerar los eventos que se desencadenan en un punto de conexión determinado.  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Interfaces)](../winscript/reference/active-script-debugger-interfaces.md)