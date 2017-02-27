---
title: "Caracter&#237;sticas de IntelliTrace | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [Visual Studio ALM], IntelliTrace"
  - "depurar [Visual Studio ALM], grabar historial de ejecución"
  - "IntelliTrace, depurar con eventos"
  - "IntelliTrace, depurar con eventos e información de llamadas"
  - "IntelliTrace, deshabilitar"
  - "IntelliTrace, habilitar"
  - "IntelliTrace, navegar por historial de eventos y llamadas"
  - "IntelliTrace, grabar historial de ejecución"
  - "IntelliTrace, guardar la sesión"
  - "IntelliTrace, iniciar depuración"
  - "IntelliTrace, desactivar"
  - "IntelliTrace, activar"
ms.assetid: 5ccc059c-6097-46b4-9d4b-34236c02d549
caps.latest.revision: 67
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 67
---
# Caracter&#237;sticas de IntelliTrace
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

IntelliTrace le permite registrar eventos y llamadas de método de su aplicación, por lo que puede examinar el estado de la misma \(pila de llamadas y valores de variables locales\) en distintos puntos de la ejecución.  Empiece la depuración como de costumbre: IntelliTrace está activado de forma predeterminada y la información que registra se puede ver en la nueva ventana **Herramientas de diagnóstico** de la pestaña **Eventos**.  Seleccione un evento y haga clic en **Activar depuración histórica** para ver la pila de llamadas y las variables locales registradas para este evento.  
  
 Para obtener una descripción paso a paso, vea [Tutorial: Uso de IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
 IntelliTrace está disponible en la edición Visual Studio Enterprise, pero no en las ediciones Professional o Community.  
  
 Para confirmar que IntelliTrace está activado, abra la página de opciones **Herramientas\/Opciones\/IntelliTrace**.  **Habilitar IntelliTrace** debería estar activado de forma predeterminada.  
  
> [!NOTE]
>  Los valores de la página de opciones de **IntelliTrace** se aplican a Visual Studio en su totalidad, no a soluciones o proyectos individuales.  Un cambio en estos valores se aplica a todas las instancias de Visual Studio, a todas las sesiones de depuración y a todos los proyectos o soluciones.  
  
##  <a name="ChooseEvents"></a> Elegir los eventos que IntelliTrace registra  
 Es posible activar o desactivar el registro de eventos específicos de IntelliTrace.  
  
 Si está depurando, detenga la depuración.  Vaya a **Herramientas\/Opciones\/IntelliTrace\/Eventos de IntelliTrace**.  Elija los eventos que desea que IntelliTrace registre.  
  
##  <a name="GoingFurther"></a> Recopilar eventos de IntelliTrace e información sobre llamadas  
 Además de los eventos, IntelliTrace puede registrar las llamadas de método, aunque esta opción no está habilitada de forma predeterminada.  Para habilitar la recopilación de llamadas de método, vaya a **Herramientas\/Opciones\/IntelliTrace\/ General** y seleccione **Eventos de IntelliTrace e información de llamadas**.  
  
 Esto le permite ver el historial de la pila de llamadas y retroceder o avanzar a través de las llamadas de código.  IntelliTrace registra datos como nombres de método, puntos de entrada y salida de métodos, y ciertos valores de parámetros y valores devueltos.  
  
> [!TIP]
>  Esta opción no está habilitada de forma predeterminada porque agrega una sobrecarga considerable.  IntelliTrace no solo tiene que interceptar todas las llamadas de método que realiza la aplicación, sino que también debe encargarse de un conjunto mucho mayor de datos a la hora de mostrarlos en pantalla o guardarlos en el disco.  
>   
>  Para reducir la sobrecarga de rendimiento, restrinja la lista de eventos registrados por IntelliTrace y reduzca al mínimo el número de módulos que se recopilan.  Para obtener más información, vea [Controlar cuánta información de llamadas registra IntelliTrace](../debugger/intellitrace-features.md#ControlCallData).  
  
### Usar el medianil de navegación  
 Puede usar el medianil de navegación que aparece a la izquierda de la ventana de código.  Si no ve el medianil de navegación, vaya a **Herramientas\/Opciones\/IntelliTrace\/Avanzado** y seleccione **Mostrar el medianil de navegación en modo de depuración**.  
  
 El medianil de navegación permite desplazarse hacia delante y hacia atrás por las llamadas de métodos y los eventos en el modo de depuración histórica.  Para obtener más información sobre la depuración histórica, vea [Depuración histórica](../debugger/historical-debugging.md).  Tiene una serie de comandos:  
  
|||  
|-|-|  
|**Establecer aquí el contexto del depurador**|Establece el contexto de depuración en el período de tiempo de la llamada donde aparece.<br /><br /> Este icono solo aparece en la pila de llamadas actual.|  
|**Volver al sitio de llamada**|Devolver el puntero y el contexto de depuración al punto en que se llamó a la función actual.<br /><br /> Si está en modo de depuración en directo, este comando activa la depuración histórica.  Si regresa a la interrupción de ejecución original, la depuración histórica se desactiva y la depuración en directo se activa.|  
|**Ir a llamada o evento de IntelliTrace anterior**|Devolver el puntero y el contexto de depuración a la llamada o evento anterior.<br /><br /> Si está en modo de depuración en directo, este comando activa la depuración histórica.|  
|**Entrar**|Depurar paso a paso por instrucciones la función seleccionada actualmente.<br /><br /> Este comando solo está disponible en el modo de depuración histórica.|  
|**Ir a llamada o evento de IntelliTrace siguiente**|Mover el puntero y el contexto de depuración a la siguiente llamada o evento para los que existen datos de IntelliTrace.<br /><br /> Este comando solo está disponible en el modo de depuración histórica.|  
|**Ir a modo real**|Volver al modo de depuración en directo.|  
  
### Buscar una línea o método en IntelliTrace  
 Los métodos solo se pueden examinar si se habilita la información sobre llamadas de método.  En el historial de IntelliTrace se puede buscar una línea o un método específicos.  Con la ejecución de la depuración detenida, haga clic con el botón derecho en el cuerpo de la función para ver el menú contextual y, a continuación, haga clic en **Buscar esta línea en IntelliTrace** o **Buscar este método en IntelliTrace**.  
  
###  <a name="ControlCallData"></a> Controlar cuánta información de llamadas registra IntelliTrace  
 De forma predeterminada, IntelliTrace registra información sobre todos los módulos usados por la solución.  No obstante, IntelliTrace se puede configurar para que registre información de llamadas solo para los módulos que le interesen.  En **Herramientas\/Opciones\/IntelliTrace\/Módulos**, puede especificar los módulos que desee incluir o excluir de IntelliTrace.  De este modo, IntelliTrace recopilará únicamente los eventos que se originaron en los módulos especificados y las llamadas de método que se produjeron en los módulos de interés.  
  
 Para agregar varios módulos, utilice el carácter comodín \* al principio o al final de la cadena.  En los nombres de módulo, use nombres de archivo y no nombres de ensamblado.  No se aceptan rutas de acceso a archivos.  
  
 Intente reducir al máximo el número de módulos,  ya que el rendimiento mejora al tener que recopilar menos datos.  También se obtiene menos ruido en la interfaz de usuario porque se deben recorrer menos datos.  
  
##  <a name="SaveSession"></a> Guardar datos de IntelliTrace en un archivo  
 Para guardar los datos recopilados por IntelliTrace, vaya a **Depurar\/IntelliTrace\/Guardar sesión de IntelliTrace** mientras se está depurando y la aplicación está en estado de interrupción.  El elemento de menú está deshabilitado y no podrá guardar los datos recopilados por IntelliTrace si la aplicación se está ejecutando o si se ha detenido la depuración.  
  
 IntelliTrace también se puede configurar para que guarde los datos automáticamente en un archivo; para ello, vaya a **Herramientas\/Opciones\/IntelliTrace\/Avanzado** y seleccione **Almacenar registros de IntelliTrace en este directorio**.  También puede configurar un tamaño fijo para el archivo generado; esto hará que IntelliTrace sobrescriba los datos más antiguos cuando se quede sin espacio.  Visual Studio crea dos archivos para cada sesión de IntelliTrace cuando se guardan automáticamente y se activa el proceso de hospedaje de Visual Studio \(vshost.exe\).  
  
> [!TIP]
>  Para ahorrar espacio en disco, desactive el guardado automático de archivos cuando ya no los necesite.  Los archivos existentes no se eliminarán.  Siempre hay la posibilidad de guardar en archivo desde el menú contextual.  
  
 Al guardar los datos de IntelliTrace en un archivo, se crea un archivo .itrace para cada proceso en el que recopile IntelliTrace.  A continuación puede abrir el archivo .itrace en Visual Studio desde **Archivo\/Abrir\/Archivo** y seleccione el archivo .itrace en el cuadro de diálogo Abrir archivo.  Para obtener más información, vea el tema sobre el [Depurar la aplicación con datos guardados de IntelliTrace](../debugger/using-saved-intellitrace-data.md).  
  
## Blogs  
 [IntelliTrace en Visual Studio Enterprise 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/intellitrace-in-visual-studio-ultimate-2015.aspx)  
  
 [Tutorial de depuración en directo con IntelliTrace en Visual Studio 2015 \(Editor de texto\)](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor.aspx)  
  
 [Tutorial de depuración en directo con IntelliTrace en Visual Studio 2015 \(Social Club\)](http://blogs.msdn.com/b/visualstudioalm/archive/2000/1/1/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club.aspx)  
  
 [IntelliTrace en Visual Studio Enterprise 2015 ahora admite adjuntos](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach.aspx)  
  
 [Recopilar datos de un servicio Windows con el recopilador independiente IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector.aspx)  
  
 [Edición del plan de recopilación de IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2015/03/09/editing-the-intellitrace-collection-plan.aspx)  
  
 [TraceSource y depuración personalizados con IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/17/custom-tracesource-and-debugging-using-intellitrace.aspx)  
  
 [Recopilador independiente IntelliTrace y grupos de aplicaciones en cuentas de Active Directory](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/22/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts.aspx)  
  
## Foros  
 [Depurador de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)  
  
## Vídeos  
 [Experiencia de IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)  
  
 [Depuración histórica con IntelliTrace en Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)