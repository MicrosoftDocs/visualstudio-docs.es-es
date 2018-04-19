---
title: Hospedaje de JavaScript en tiempo de ejecución | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30ec744e-57cc-4ef5-8fe1-d2c27b946548
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2bf213bf262ede7642e05c66e424b860238dc57f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="hosting-the-javascript-runtime"></a>Hospedar runtime de JavaScript
Las API de JavaScript Runtime (JsRT) permiten a las aplicaciones de escritorio, del lado servidor y de la Tienda Windows que se ejecutan en el sistema operativo Windows agregar funciones de scripting a una aplicación mediante el uso del motor de JavaScript Chakra basado en estándares (usado también por Microsoft Edge e Internet Explorer). Estas API están disponibles en Windows 10 y cualquier versión del sistema operativo Windows que tenga la versión 10 de Internet Explorer instalada en el equipo. Para obtener más información, consulta [Reference (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md). Para obtener información sobre el uso de JsRT en aplicaciones de la Tienda Windows, consulte [JsRT and the Universal Windows Platform](#Windows).  
  
> [!NOTE]
>  Esta documentación asume cierta familiaridad con el lenguaje JavaScript.  
  
## <a name="concepts"></a>Conceptos  
 Entender cómo hospedar el motor de JavaScript usando las API de JsRT depende de dos conceptos clave: los runtimes y los contextos de ejecución.  
  
 Un *runtime* representa un entorno completo de ejecución de JavaScript. Cada runtime creado tiene su propio montón de recolección de elementos no utilizados aislado y, de forma predeterminada, sus propios subprocesos del compilador Just-In-Time (JIT) y del recolector de elementos no utilizados (GC). Un *contexto de ejecución* representa un entorno de JavaScript que tiene su propio objeto global de JavaScript distinto del resto de contextos de ejecución. Un runtime puede contener varios contextos de ejecución, y en estos casos, todos ellos comparten el compilador JIT y el subproceso GC asociados al runtime.  
  
 Los runtimes representan un único subproceso de ejecución. Solo un runtime puede estar activo en un subproceso concreto en un determinado momento, y un runtime solo puede estar activo en un subproceso cada vez. Los tiempos de ejecución están a disposición de los subprocesos, por lo que un tiempo de ejecución que no esté activo actualmente en un subproceso (es decir, no esté ejecutando ningún código JavaScript ni respondiendo a ninguna llamada del host) se puede usar en cualquier subproceso que aún no tenga un tiempo de ejecución activo.  
  
 Los contextos de ejecución están asociados a un runtime determinado y ejecutan código dentro de dicho runtime. A diferencia de los runtimes, varios contextos de ejecución pueden estar activos en un subproceso al mismo tiempo. Por lo que un host puede llamar a un contexto de ejecución, ese contexto de ejecución devolver la llamada al host y este realizar una llamada a otro contexto de ejecución diferente.  
  
 ![Varios contextos de ejecución](../chakra-hosting/media/js-chakra-hosting.png "JS_Chakra_Hosting")  
  
 En la práctica, a menos que un host necesite ejecutar código en entornos separados, puede utilizarse un único contexto de ejecución. De igual forma, a menos que un host necesite ejecutar varios fragmentos de código simultáneamente, un único runtime es suficiente.  
  
## <a name="memory-management"></a>Administración de la memoria  
 JavaScript es un lenguaje de recolección de elementos no utilizados, por lo que hay varias consideraciones que deben tenerse en cuenta al trabajar con las API de JsRT desde otro lenguaje.  
  
 La consideración principal es que el recolector de elementos no utilizados de JavaScript solo puede ver las referencias a valores en dos lugares: el montón del entorno de ejecución y la pila. Así, el recolector de elementos no utilizados siempre verá una referencia a un valor de JavaScript almacenado dentro de otro o en una variable local en la pila. Pero no ocurrirá lo mismo con las referencias almacenadas en otras ubicaciones, como los montones administrados por el host o el sistema, que podrán dar como resultado una colección prematura de valores que todavía sigue usando el host.  
  
> [!IMPORTANT]
>  Algunos compiladores de lenguajes (como el compilador de Visual Studio C++) optimizarán las variables locales siempre que sea posible. Hay que prestar atención para asegurarse de que las variables locales que hacen referencia a valores de JavaScript están en la pila si se espera que mantengan activos esos valores.  
  
 Si una referencia a un valor de JavaScript se almacena en una ubicación no visible para el recolector de elementos no utilizados, el host debe agregar y quitar manualmente las referencias mediante las API de JsRT.  
  
## <a name="exception-handling"></a>Control de excepciones  
 Cuando se produce una excepción de JavaScript durante la ejecución de un script, el runtime contenedor se coloca en un estado de excepción. En el estado de excepción, no se puede ejecutar ningún código y todas las llamadas API producirán un error con el código `JsErrorInExceptionState` hasta que el host recupere y borre la excepción mediante la API `JsGetAndClearException` . Si el host vuelve de una devolución de llamada de JavaScript sin eliminar el estado de excepción del runtime, la excepción de JavaScript se volverá a producir tan pronto como el control vuelva al motor de JavaScript. Esto también permite a las devoluciones de llamada del host "producir" una excepción de JavaScript al colocar el entorno de ejecución en un estado de excepción y, a continuación, volver de una devolución de llamada del host.  
  
 No se permite que un host deje que se propaguen sus propias excepciones internas a través de una devolución de llamada de host; los métodos de devolución de llamada deben detectar todas las excepciones de host antes de devolver el control al runtime.  
  
## <a name="runtime-resource-usage"></a>Uso de recursos del runtime  
 Las API de JsRT exponen varias formas de supervisar y modificar la manera en la que los runtimes usan los recursos. Generalmente se dividen en las categorías siguientes:  
  
-   **Uso de subprocesos**. De forma predeterminada, cada runtime creará un subproceso del compilador JIT dedicado y un subproceso GC dedicado que dan servicio a ese runtime. Si se crea un runtime con la marca `JsRuntimeAttributeDisableBackgroundWork` , el trabajo de JIT y GC se realizará en el propio subproceso del runtime en lugar de en subprocesos en segundo plano independientes para cada uno de ellos. Un host también puede proporcionar una devolución de llamada del servicio del subproceso a la llamada a `JsCreateRuntime` , lo que permitirá al host programar el trabajo de JIT y GC de la forma que considere apropiada.  
  
-   **Uso de memoria**. Hay varias maneras de supervisar y modificar el uso de memoria de un runtime. Si el runtime se va a ejecutar durante mucho tiempo, el host puede especificar la marca `JsRuntimeAttributeEnableIdleProcessing` al crear el runtime y, a continuación, llamar a `JsIdle` cuando el host esté en estado inactivo. Esto permite al motor diferir algunos trabajos de limpieza de memoria y contabilidad hasta el tiempo de inactividad.  
  
     El host puede supervisar las recolecciones de elementos no utilizados llamando a `JsSetRuntimeBeforeCollectCallback`. También puede supervisar las asignaciones realizadas por el montón llamando a `JsSetRuntimeMemoryAllocationCallback`. Tenga en cuenta que esta API no realiza una devolución de llamada en cada asignación de JavaScript, justo en el momento en que el montón del entorno de ejecución requiere más espacio desde el que asignar. La devolución de llamada de asignación de memoria puede denegar la solicitud, lo que desencadenará una recolección de elementos no utilizados y, si no hay memoria disponible, un error de memoria insuficiente en el runtime.  
  
     El host también puede llamar a `JsSetRuntimeMemoryLimit` para establecer un límite en la cantidad de memoria que puede usar un runtime. Cuando un runtime alcanza un límite, desencadena una recolección de elementos no utilizados y, si no hay memoria disponible, producirá un error de memoria insuficiente.  
  
-   **Interrupción y evaluación de scripts**. El host puede llamar a `JsDisableRuntimeExecution` para finalizar la ejecución dentro de un runtime. Esta llamada se puede realizar en cualquier momento y desde cualquier subproceso. Dado que la finalización del script depende de que se alcancen los puntos de restricción insertados en el código, es posible que un script no finalice en el momento exacto, pero lo hará muy poco tiempo después. De forma predeterminada, los puntos de restricción de la finalización se colocan en el código generado de manera conservadora y es posible que no cubran todos los escenarios, como un bucle infinito. Si se crea el runtime con la marca `JsRuntimeAttributeAllowScriptInterrupt` , este insertará comprobaciones adicionales para los bucles infinitos, a menudo a costa de una pequeña sobrecarga de rendimiento.  
  
     Si un host desea impedir que el compilador JIT genere código nativo, puede especificar la marca `JsRuntimeAttributeDisableNativeCodeGeneration` . Un host también puede impedir que los propios scripts ejecuten scripts dinámicamente si especifica la marca `JsRuntimeAttributeDisableEval` .  
  
## <a name="debugging-and-profiling"></a>Depurar y generar perfiles  
 Las API de JsRT admiten la depuración y la generación de perfiles mediante la tecnología de Active Scripting.  
  
 A partir de Windows 10, el motor de JavaScript Chakra admite un motor heredado y el motor Microsoft Edge, y cualquiera puede ser el destino en JsRT (consulte el artículo sobre el [motor Edge como destino frente a los. motores heredados](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md) para obtener más información). La depuración de un script en Visual Studio funciona de forma diferente en el motor heredado y en el motor Edge. Con el motor heredado, el host debe proporcionar un puntero de [interfaz de IDebugApplication](../winscript/reference/idebugapplication-interface.md), que puede obtenerse de una instancia de [interfaz de IProcessDebugManager](../winscript/reference/iprocessdebugmanager-interface.md). Con el motor Edge, `IDebugApplication` ha quedado en desuso. El motor Chakra permite funcionalidades de depuración nativa y de script mediante el depurador de Visual Studio sin necesidad de que el usuario implemente `IDebugApplication` .  
  
 Para conseguir que los scripts de un contexto de ejecución se puedan depurar, el motor Chakra tiene que pasar a usar métodos menos eficaces de ejecución de código. Como tal, el código depurable se ejecuta normalmente más despacio que el no depurable. Por ello, con el motor heredado, un host puede elegir entre iniciar la depuración en un contexto de ejecución desde el principio proporcionando el puntero de `IDebugApplication` por adelantado a través de `JsCreateContext`, o esperar hasta que la depuración sea necesaria y entonces llamar a `JsStartDebugging`. Con el motor Microsoft Edge, `JsCreateContext` ya no toma un parámetro `IDebugApplication` , y como resultado el script es depurable solo después de llamar a `JsStartDebugging` . Al realizar la depuración con Visual Studio, debe habilitarse la opción del depurador "Script".  
  
 Hay dos maneras de generar un perfil del código JavaScript de un contexto de ejecución. En Windows 8.1 y versiones posteriores, se puede usar el generador de perfiles de línea de comandos de Visual Studio (vsperf.exe) con el modificador /js para generar un informe que se centre en el código JavaScript ejecutado en la aplicación. O el host puede llamar directamente a `JsStartProfiling` y `JsStopProfiling` y proporcionar una devolución de llamada para realizar la generación de perfiles él mismo. El host también puede examinar el estado del montón de recolección de elementos no utilizados llamando a `JsEnumerateHeap`. La generación de perfiles de JsRT funciona de la misma manera entre el motor heredado y el motor Microsoft Edge. Sin embargo, las API de generación de perfiles de JsRT (`JsStartProfiling`, `JsStopProfiling`, `JsEnumerateHeap`y `JsIsEnumeratingHeap`) no están disponibles para aplicaciones universales de Windows.  
  
<a name="Windows"></a>   
## <a name="jsrt-and-the-universal-windows-platform"></a>JsRT and the Universal Windows Platform  
 Puede usar las API de JsRT para agregar funcionalidades de scripting a una aplicación universal de Windows. Una aplicación universal de Windows que usa las API de JsRT tendrá como destino las API de JSRT Edge, que a su vez tienen como destino el motor Chakra de Edge. Para obtener más información, vea el artículo sobre [Microsoft Edge o motores heredados](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md). La API completa de JsRT está disponible para aplicaciones universales de Windows, excepto para la compatibilidad con enumeración de montón y generación de perfiles (no se admite`JsStartProfiling`, `JsStopProfiling`, `JsEnumerateHeap`ni `JsIsEnumeratingHeap` ).  
  
 JsRT también permite que los scripts accedan de forma nativa a cualquier [API de la Plataforma universal de Windows (UWP)](https://msdn.microsoft.com/en-us/library/windows/apps/br211377.aspx) tras exponer el espacio de nombres de la API a través del elemento `JsProjectWinRTNamespace`de la API de JsRT Edge. A diferencia de las aplicaciones universales de Windows, que no requieren ninguna configuración adicional aparte de proyectar los espacios de nombres necesarios, en las aplicaciones de Windows clásicas (Win32) hay que habilitar un mecanismo de bombeo delegado inicializado por COM a través de `JsSetProjectionEnqueueCallback` a fin de habilitar los eventos y las API asincrónicas. En el siguiente ejemplo de Win32 se usan las API asincrónicas de UWP para crear un cliente http y obtener contenido desde un Uri:  
  
```cpp  
typedef struct _jsCall {  
    JsProjectionCallback jsCallback;  
    JsProjectionCallbackContext jsContext;  
    HANDLE event;  
} jsCall;  
  
// Set up delegated pumping mechanism; not necessary in UWP applications.  
jsCall outstandingCall = {};  
CoInitializeEx(nullptr, COINIT_MULTITHREADED);  
JsSetProjectionEnqueueCallback([](JsProjectionCallback jsCallback,   
JsProjectionCallbackContext jsContext, void *callbackState) {  
    jsCall* call = (jsCall*)callbackState;  
    call->jsCallback = jsCallback;  
    call->jsContext = jsContext;  
    SetEvent(call->event);  
    },  
&outstandingCall);  
HANDLE event = CreateEventEx(NULL, NULL, CREATE_EVENT_MANUAL_RESET, EVENT_ALL_ACCESS);  
outstandingCall.event = event;  
  
// Project necessary namespaces.  
JsProjectWinRTNamespace(L"Windows.Foundation");  
JsProjectWinRTNamespace(L"Windows.Web");  
  
// Get content from an Uri.  
JsRunScript(L"var uri = new Windows.Foundation.Uri(\"http://somedatasource.com\"); " \  
    L"var httpClient = new Windows.Web.Http.HttpClient();" \  
    L"httpClient.getStringAsync(uri).done(function (content) { " \  
    L"    // do something with the string content " \    
    L"}, onError); " \  
    L"function onError(reason) { " \  
    L"    // error handling " \        
    L"}",   
    currentSourceContext, L"", &result);  
  
// Wait for async call to come in and then execute; not necessary in UWP applications.  
WaitForSingleObjectEx(outstandingCall.event, 10000, FALSE) == WAIT_OBJECT_0;  
outstandingCall.jsCallback(outstandingCall.jsContext);  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Aplicación de ejemplo del tiempo de ejecución de JavaScript](http://go.microsoft.com/fwlink/p/?LinkID=306674&clcid=0x409)   
 [Referencia (JavaScript en tiempo de ejecución)](../chakra-hosting/reference-javascript-runtime.md)   
 [Hospedaje de tiempo de ejecución de JavaScript](../chakra-hosting/javascript-runtime-hosting.md)