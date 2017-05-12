---
title: "Informaci&#243;n general acerca de la depuraci&#243;n de Active Script | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Información general acerca de la depuración de Active Script"
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Informaci&#243;n general acerca de la depuraci&#243;n de Active Script
Las interfaces activo de la depuración de script permiten la depuración lenguaje\- neutro, host\- neutro, y admite una gran variedad de entornos de desarrollo.  
  
 ![Proceso de host de scripts](../winscript/media/scp56activdbgarchgif.png "Scp56ActivDbgArchgif")  
Tabla 1  
  
 Un entorno de depuración lenguaje\- neutro puede admitir cualquier lenguaje de programación o combinación de lenguajes de programación, sin tener un conocimiento específico de cualquiera de esos idiomas.  El entorno de depuración también admite el recorrido y los puntos de interrupción en lenguajes.  \(Esta introducción se centra principalmente en lenguajes de script compatible con, como VBScript y [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].\)  
  
 Un depurador host\- neutro puede automáticamente utilizar con cualquier host de Scripting activos, como Internet Explorer o un host personalizado.  Los controles host del depurador muestra al usuario, la estructura de árbol de documentos al contenido y el color de la sintaxis de depuración documentan.  Esto permite que el código fuente depurando es mostrado en el contexto del documento de host.  Por ejemplo, Internet Explorer puede mostrar un script en una página HTML.  
  
 En las subsecciones siguientes, se describen a cada componente clave en la depuración activa y sus interfaces asociadas.  Sin embargo, antes de progreso, varios cierre conceptos activo de depuración deben definir:  
  
 aplicación host  
 La aplicación que hospeda los motores de scripts y proporciona un conjunto que admite scripts de objetos \(o “modelo de objetos”\).  
  
 motor de lenguaje  
 Un componente que proporciona el análisis, ejecución, y abstracciones de depuración para un idioma determinado.  
  
 depurador IDE  
 La aplicación que proporciona la interfaz de usuario de depuración comunicando con motores de la aplicación host y del lenguaje.  
  
 administrador de depuración de equipo  
 Un componente que mantiene un registro de los procesos de aplicación depurables.  
  
 administrador de depuración  
 Un componente que mantiene el árbol de documentos depurables para una aplicación determinada, siga los subprocesos en ejecución, y así sucesivamente.  
  
 contexto del documento  
 Un contexto de documento es una abstracción que representa un intervalo concreto en el código fuente de un documento de host.  
  
 contexto del código  
 Un contexto de código representa una posición en el código actual de un motor del lenguaje \(un “puntero de instrucción virtual”\).  
  
 contexto de expresiones  
 Un contexto concreto \(por ejemplo, un marco de pila\) en el que las expresiones se pueden evaluar por un motor de lenguaje.  
  
 el examen de objeto  
 Una representación de un nombre de objeto, un tipo, un valor, y sub\- objetos estructurados, independientes del lenguaje, adecuadas para implementar una interfaz de usuario de “ventana inspección”.  
  
 A continuación se muestra una información general de cada uno de los componentes activo clave y de correspondiente de la depuración, las interfaces asociadas, además de los detalles de dichas interfaces.  
  
## Motor de lenguaje  
 El motor de lenguaje proporciona:  
  
-   Análisis y ejecución de lenguaje.  
  
-   Capacidad de depuración \(puntos de interrupción y así sucesivamente\).  
  
-   Evaluación de la expresión.  
  
-   Colorear la sintaxis.  
  
-   El examen del objeto.  
  
-   Enumeración y análisis de la pila.  
  
 A continuación se interfaces que un motor de script necesita permitir que proporcionan la depuración, la evaluación de expresiones, y examinar del objeto.  Estas interfaces son utilizadas por la aplicación host para asignar entre el contexto del documento y contextos de código del motor, y por la interfaz de usuario del depurador para que la evaluación de la expresión, la enumeración del montón, y examinar del objeto.  
  
 [IActiveScriptDebug \(Interfaz\)](../winscript/reference/iactivescriptdebug-interface.md)  
 Proporciona el color de la sintaxis y la enumeración del contexto del código.  
  
 [IActiveScriptErrorDebug \(Interfaz\)](../winscript/reference/iactivescripterrordebug-interface.md)  
 Devuelve contextos y marcos de pila del documento para los errores.  
  
 [IActiveScriptSiteDebug \(Interfaz\)](../winscript/reference/iactivescriptsitedebug-interface.md)  
 Vínculo proporcionado host del motor de script el depurador.  
  
 [IDebugCodeContext \(Interfaz\)](../winscript/reference/idebugcodecontext-interface.md)  
 Proporciona un “puntero de instrucción virtual” en un subproceso.  
  
 [IEnumDebugCodeContexts \(Interfaz\)](../winscript/reference/ienumdebugcodecontexts-interface.md)  
 Enumera los contextos de código que corresponden a un contexto del documento.  
  
 [IDebugStackFrame \(Interfaz\)](../winscript/reference/idebugstackframe-interface.md)  
 Representa un marco de pila lógico en la pila del subproceso.  
  
 [IDebugExpressionContext \(Interfaz\)](../winscript/reference/idebugexpressioncontext-interface.md)  
 Proporciona el contexto en el que se pueden evaluar las expresiones.  
  
 [IDebugStackFrameSniffer \(Interfaz\)](../winscript/reference/idebugstackframesniffer-interface.md)  
 Proporciona una manera de mostrar los marcos de pila lógicos.  
  
 [IDebugExpression \(Interfaz\)](../winscript/reference/idebugexpression-interface.md)  
 Representa una expresión de forma asincrónica evaluada.  
  
 [IDebugSyncOperation \(Interfaz\)](../winscript/reference/idebugsyncoperation-interface.md)  
 Permite que un motor de script abstracto una operación que necesite realizar mientras está anidada en un subproceso bloqueado determinado.  
  
 [IDebugAsyncOperation \(Interfaz\)](../winscript/reference/idebugasyncoperation-interface.md)  
 Proporciona acceso asincrónico a una operación sincrónica de depuración.  
  
 [IDebugAsyncOperationCallBack \(Interfaz\)](../winscript/reference/idebugasyncoperationcallback-interface.md)  
 Proporciona eventos de estado relacionados con el progreso de una evaluación de la interfaz de `IDebugAsyncOperation`.  
  
 [IEnumDebugExpressionContexts \(Interfaz\)](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
 Enumera una colección de objetos `IDebugExpressionContexts`.  
  
 [IProvideExpressionContexts \(Interfaz\)](../winscript/reference/iprovideexpressioncontexts-interface.md)  
 Proporciona una manera de mostrar los contextos de expresión conocidos por un componente.  
  
 [IDebugFormatter \(Interfaz\)](../winscript/reference/idebugformatter-interface.md)  
 Permite que un idioma o el IDE personalizar la conversión entre los valores VARIANT o los tipos y las cadenas de VARTYPE.  
  
 [IDebugStackFrameSnifferEx \(Interfaz\)](../winscript/reference/idebugstackframesnifferex-interface.md)  
 Enumera los marcos de pila lógicos para el PDM.  
  
## Hosts  
 El host:  
  
-   Hospedar los motores del lenguaje.  
  
-   Proporciona un modelo de objetos \(conjunto de objetos que pueden ser con guión\).  
  
-   Define un árbol de documentos que pueden ser depurados y su contenido.  
  
-   Organiza los scripts en aplicaciones virtuales.  
  
 Hay dos tipos de host:  
  
-   Un host mudo admite solamente las interfaces básicas de Scripting activo.  No tiene ningún control sobre la estructura o la organización del documento; esto viene determinada por completo de scripts proporcionados a motores de lenguaje.  
  
-   Un host inteligente admite un conjunto mayor de interfaces que defina el árbol de documentos, el contenido del documento, y el color de la sintaxis.  Hay un conjunto de interfaces de aplicación auxiliar, describe en la siguiente subsección, que hacen que sea mucho más sencillo que un host sea un host inteligente.  
  
### Interfaces auxiliar host inteligente  
 Los métodos de `IDebugDocumentHelper` proporcionan un conjunto considerablemente simplificado de interfaces que un host puede utilizar para aprovechar las ventajas de SMART\- hospedar sin administrar la complejidad completa \(y eficacia\) de las interfaces completas del host.  
  
 No es necesario que un host utilizar estas interfaces, por supuesto.  Sin embargo mediante estas interfaces pueden evitar la implementación o utilizar varias interfaces más complejas.  
  
 [IDebugDocumentHelper \(Interfaz\)](../winscript/reference/idebugdocumenthelper-interface.md)  
 Implementado por PDM y proporciona implementaciones para las interfaces necesarias para hospedar inteligente.  
  
 [IDebugDocumentHost \(Interfaz\)](../winscript/reference/idebugdocumenthost-interface.md)  
 Implementado \(opcionalmente\) por el host para exponer la funcionalidad host\- específica, como colorear la sintaxis, el depurador.  
  
 Para obtener más información, vea [Implementar interfaces Smart Host Helper](../winscript/implementing-smart-host-helper-interfaces.md).  
  
### Interfaces completas host inteligente  
 A continuación se muestra el conjunto completo de interfaces que un host inteligente debe implementar o utilizar si no está utilizando las interfaces de la aplicación auxiliar.  
  
 Interfaces implementadas por el host:  
  
 [IDebugDocumentInfo \(Interfaz\)](../winscript/reference/idebugdocumentinfo-interface.md)  
 Proporciona información en un documento, que puede o no puede crear instancias.  
  
 [IDebugDocumentProvider \(Interfaz\)](../winscript/reference/idebugdocumentprovider-interface.md)  
 Proporciona un medio para crear instancias de un documento a petición.  
  
 [IDebugDocument \(Interfaz\)](../winscript/reference/idebugdocument-interface.md)  
 La interfaz base para todos los documentos de depuración.  
  
 [IDebugDocumentText \(Interfaz\)](../winscript/reference/idebugdocumenttext-interface.md)  
 Proporciona acceso a una versión de texto \- sólo de depuración.  
  
 [IDebugDocumentTextAuthor \(Interfaz\)](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 Permite la edición de la versión de texto\) sólo de depuración.  
  
 [IDebugDocumentContext \(Interfaz\)](../winscript/reference/idebugdocumentcontext-interface.md)  
 Proporciona una representación abstracta de una parte del documento que se está depurando.  
  
 Interfaces implementadas por PDM en nombre de host:  
  
 [IDebugApplicationNode \(Interfaz\)](../winscript/reference/idebugapplicationnode-interface.md)  
 Extiende la funcionalidad de la interfaz de `IDebugDocumentProvider` proporcionando un contexto dentro de un árbol de proyecto.  
  
## Depurador IDE  
 El IDE es una interfaz de usuario independiente del lenguaje de depuración.  Proporciona:  
  
-   Visores de documentos y editores.  
  
-   Administración de punto de interrupción.  
  
-   Evaluación y ventanas inspección de la expresión.  
  
-   El examen del marco de pila.  
  
-   El examen de objeto o de la clase.  
  
-   Examinar la estructura virtual de la aplicación.  
  
 Interfaces implementadas por el depurador:  
  
 [IApplicationDebugger \(Interfaz\)](../winscript/reference/iapplicationdebugger-interface.md)  
 La interfaz principal expuesta por una sesión del IDE del depurador.  
  
 [IApplicationDebuggerUI \(Interfaz\)](../winscript/reference/iapplicationdebuggerui-interface.md)  
 Proporciona a un componente externo más control sobre la interfaz de usuario \(UI\) del depurador.  
  
 [IDebugExpressionCallBack \(Interfaz\)](../winscript/reference/idebugexpressioncallback-interface.md)  
 Proporciona eventos de estado del progreso de la evaluación de `IDebugExpression`.  
  
 [IDebugDocumentTextEvents \(Interfaz\)](../winscript/reference/idebugdocumenttextevents-interface.md)  
 Proporciona eventos que indican cambios en el documento de texto asociado.  
  
 [IDebugApplicationNodeEvents \(Interfaz\)](../winscript/reference/idebugapplicationnodeevents-interface.md)  
 Proporciona la interfaz de eventos de la interfaz de `IDebugApplicationNode`.  
  
### Administrador de depuración de equipos  
 El administrador de depuración de equipo proporciona el punto de vinculación entre las aplicaciones y los depuradores virtuales manteniendo y enumerar una lista de aplicaciones virtuales activos.  
  
 [IDebugSessionProvider \(Interfaz\)](../winscript/reference/idebugsessionprovider-interface.md)  
 Establece una sesión de depuración para una aplicación en ejecución.  
  
 [IMachineDebugManager \(Interfaz\)](../winscript/reference/imachinedebugmanager-interface.md)  
 La interfaz principal al administrador de depuración de equipo.  
  
 [IMachineDebugManagerCookie \(Interfaz\)](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 Similar a la interfaz de `IMachineDebugManager`, pero a esta interfaz admite cookies de depuración.  
  
 [IMachineDebugManagerEvents \(Interfaz\)](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 Cambios de paso en la lista actual de la aplicación mantenida por el administrador de depuración de equipo.  
  
 [IEnumRemoteDebugApplications \(Interfaz\)](../winscript/reference/ienumremotedebugapplications-interface.md)  
 Muestra las aplicaciones en ejecución en un equipo.  
  
### Administrador de depuración  
 El PDM hace lo siguiente:  
  
-   Sincroniza la depuración de los motores de varios idiomas.  
  
-   Mantiene un árbol de documentos depurables.  
  
-   Combina los marcos de pila.  
  
-   Puntos de interrupción de las coordenadas y paso a través de los motores del lenguaje.  
  
-   Siga los subprocesos.  
  
-   Mantiene un subproceso del depurador para el procesamiento asincrónico.  
  
-   Se comunica con el administrador de depuración de equipo y el depurador el IDE.  
  
 Los siguientes son las interfaces proporcionadas por el administrador de la depuración.  
  
 [IProcessDebugManager \(Interfaz\)](../winscript/reference/iprocessdebugmanager-interface.md)  
 Interfaz principal al administrador de la depuración.  Esta interfaz puede crear, agregar, o quitar una aplicación virtual de un proceso.  
  
 [IRemoteDebugApplication \(Interfaz\)](../winscript/reference/iremotedebugapplication-interface.md)  
 Representa una aplicación en ejecución.  
  
 [IDebugApplication \(Interfaz\)](../winscript/reference/idebugapplication-interface.md)  
 Métodos no remotos de depuración de expone que los motores y hosts del lenguaje.  
  
 [IRemoteDebugApplicationThread \(Interfaz\)](../winscript/reference/iremotedebugapplicationthread-interface.md)  
 Representa un subproceso de ejecución dentro de una aplicación determinada.  
  
 [IDebugApplicationThread \(Interfaz\)](../winscript/reference/idebugapplicationthread-interface.md)  
 Permite que los motores y hosts de lenguaje proporcionan la sincronización de subprocesos y mantener subproceso\- concreto, información de la depuración\- provincia.  
  
 [IEnumRemoteDebugApplicationThreads \(Interfaz\)](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
 Enumera los subprocesos en ejecución en una aplicación.  
  
 [IDebugThreadCall \(Interfaz\)](../winscript/reference/idebugthreadcall-interface.md)  
 Llamadas formadas envíos.  
  
 [IDebugApplicationNode \(Interfaz\)](../winscript/reference/idebugapplicationnode-interface.md)  
 Mantiene una posición de un documento en la jerarquía.  
  
 [IEnumDebugApplicationNodes \(Interfaz\)](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
 Enumera los nodos secundarios de un nodo asociado a una aplicación.  
  
 [IEnumDebugStackFrames \(Interfaz\)](../winscript/reference/ienumdebugstackframes-interface.md)  
 Enumera los marcos de pila correspondiente a un subproceso, combinado de los motores.  
  
 [IDebugCookie \(Interfaz\)](../winscript/reference/idebugcookie-interface.md)  
 Permite que la cookie de depuración se establezca en depuradores del archivo de comandos.  
  
 [IDebugHelper \(Interfaz\)](../winscript/reference/idebughelper-interface.md)  
 Actúa como un generador para los examinadores de objetos y los puntos de conexión simples para los motores de scripts.  
  
 [ISimpleConnectionPoint \(Interfaz\)](../winscript/reference/isimpleconnectionpoint-interface.md)  
 Proporciona una manera sencilla para describir y enumerar los eventos desencadenados en un punto de conexión determinado, para los motores de scripts.  
  
## Vea también  
 [Active Script Debugger \(Interfaces\)](../winscript/reference/active-script-debugger-interfaces.md)