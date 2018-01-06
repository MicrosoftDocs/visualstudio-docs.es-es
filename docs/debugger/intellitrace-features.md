---
title: "Características de IntelliTrace | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliTrace, debugging with events
- IntelliTrace, recording execution history
- debugging [Visual Studio ALM], recording execution history
- IntelliTrace, turn off
- IntelliTrace, navigating event and call history
- IntelliTrace, saving your session
- IntelliTrace, enabling
- IntelliTrace, start debugging
- IntelliTrace, debugging with events and call information
- IntelliTrace, disabling
- IntelliTrace, turn on
- debugging [Visual Studio ALM], IntelliTrace
ms.assetid: 5ccc059c-6097-46b4-9d4b-34236c02d549
caps.latest.revision: "67"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f2ad259a116b1679f1e619dc9d281c114fa086cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="intellitrace-features"></a>Características de IntelliTrace
IntelliTrace le permite registrar eventos y llamadas de método de su aplicación, por lo que puede examinar el estado de la misma (pila de llamadas y valores de variables locales) en distintos puntos de la ejecución. Simplemente empiece a depurar como de costumbre: IntelliTrace está activado de forma predeterminada y puede ver la información que se registra en el nuevo **herramientas de diagnóstico** ventana bajo la **eventos** ficha. Seleccione un evento y haga clic en **Activar depuración histórica** para ver la pila de llamadas ni variables locales registradas para este evento.  
  
 Para obtener una descripción paso a paso, consulte [Tutorial: uso de IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
 IntelliTrace está disponible en la edición Visual Studio Enterprise, pero no en las ediciones Professional o Community.  
  
 Para confirmar que IntelliTrace está activado, abra la **Herramientas > Opciones > IntelliTrace** página de opciones. **Habilitar IntelliTrace** debe estar activada de forma predeterminada.  
  
> [!NOTE]
>  El ámbito de todos los valores de la **IntelliTrace** página de opciones es Visual Studio como un todo, soluciones o proyectos no individuales. Un cambio en estos valores se aplica a todas las instancias de Visual Studio, a todas las sesiones de depuración y a todos los proyectos o soluciones.  
  
##  <a name="ChooseEvents"></a>Elegir los eventos que IntelliTrace registra  
 Es posible activar o desactivar el registro de eventos específicos de IntelliTrace.  
  
 Si está depurando, detenga la depuración. Vaya a **Herramientas > Opciones > IntelliTrace > eventos de IntelliTrace**. Elija los eventos que desea que IntelliTrace registre.  
  
## <a name="Snapshots"></a>Recopilar eventos e instantáneas  
 Esta opción no está habilitada de forma predeterminada, pero IntelliTrace puede capturar instantáneas de la aplicación en cada evento de paso de punto de interrupción y el depurador, y puede ver las instantáneas de esta en una sesión de depuración histórica. Una instantánea proporciona una vista de su estado completo de la aplicación. Para habilitar la captura de instantáneas, vaya a **Herramientas > Opciones > IntelliTrace > General**y seleccione **IntelliTrace eventos e instantáneas**. Para obtener más información, vea [ver instantáneas mediante la devolución de paso de IntelliTrace](../debugger/how-to-use-intellitrace-step-back.md)

 Las instantáneas están disponibles en Visual Studio Enterprise 2017 15.5 y versiones posteriores, y requiere actualización de aniversario de Windows 10 o superior.  Las instantáneas no están actualmente disponibles para las aplicaciones .NET Core y ASP.NET Core.

##  <a name="GoingFurther"></a>Recopilar eventos de IntelliTrace e información de llamadas  
 Esta opción no está habilitada de forma predeterminada, pero IntelliTrace puede registrar las llamadas de método junto con los eventos. Para habilitar la recopilación de método, las llamadas que se vaya a **Herramientas > Opciones > IntelliTrace > General**y seleccione **eventos de IntelliTrace e información de llamadas**.

 Información de llamadas no está actualmente disponible para las aplicaciones .NET Core y ASP.NET Core. 
  
 Esto le permite ver el historial de la pila de llamadas y retroceder o avanzar a través de las llamadas de código. IntelliTrace registra datos como nombres de método, puntos de entrada y salida de métodos, y ciertos valores de parámetros y valores devueltos.  
  
> [!TIP]
>  Esta opción no está habilitada de forma predeterminada porque agrega una sobrecarga considerable. IntelliTrace no solo tiene que interceptar todas las llamadas de método que realiza la aplicación, sino que también debe encargarse de un conjunto mucho mayor de datos a la hora de mostrarlos en pantalla o guardarlos en el disco.  
>   
>  Para reducir la sobrecarga de rendimiento, restrinja la lista de eventos registrados por IntelliTrace y reduzca al mínimo el número de módulos que se recopilan. Para obtener más información, consulte [Control cuánto información de llamadas registra IntelliTrace](../debugger/intellitrace-features.md#ControlCallData).  
  
### <a name="use-the-navigation-gutter"></a>Usar el medianil de navegación  
 Puede usar el medianil de navegación que aparece a la izquierda de la ventana de código. Si no ve el medianil de navegación, vaya a **Herramientas > Opciones > IntelliTrace > Opciones avanzadas**y seleccione **mostrar el medianil de navegación en modo de depuración**.  
  
 El medianil de navegación permite desplazarse hacia delante y hacia atrás por las llamadas de métodos y los eventos en el modo de depuración histórica. Para obtener más información sobre la depuración histórica, vea [depuración histórica](../debugger/historical-debugging.md). Tiene una serie de comandos:  
  
|||  
|-|-|  
|**Establecer aquí el contexto del depurador**|Establece el contexto de depuración en el período de tiempo de la llamada donde aparece.<br /><br /> Este icono solo aparece en la pila de llamadas actual.|  
|**Volver al sitio de llamada**|Devolver el puntero y el contexto de depuración al punto en que se llamó a la función actual.<br /><br /> Si está en modo de depuración en directo, este comando activa la depuración histórica. Si regresa a la interrupción de ejecución original, la depuración histórica se desactiva y la depuración en directo se activa.|  
|**Ir a llamada o evento de IntelliTrace anterior**|Devolver el puntero y el contexto de depuración a la llamada o evento anterior.<br /><br /> Si está en modo de depuración en directo, este comando activa la depuración histórica.|  
|**Paso a paso**|Depurar paso a paso por instrucciones la función seleccionada actualmente.<br /><br /> Este comando solo está disponible en el modo de depuración histórica.|  
|**Ir a llamada o evento de IntelliTrace siguiente**|Mover el puntero y el contexto de depuración a la siguiente llamada o evento para los que existen datos de IntelliTrace.<br /><br /> Este comando solo está disponible en el modo de depuración histórica.|  
|**Ir a modo real**|Volver al modo de depuración en directo.|  
  
### <a name="search-for-a-line-or-method-in-intellitrace"></a>Buscar una línea o método en IntelliTrace  
 Los métodos solo se pueden examinar si se habilita la información sobre llamadas de método. En el historial de IntelliTrace se puede buscar una línea o un método específicos. Mientras se detiene la ejecución del depurador, haga clic en el cuerpo de la función para ver el menú contextual y haga clic en **buscar esta línea en IntelliTrace** o **buscar este método en IntelliTrace**.  
  
###  <a name="ControlCallData"></a>Controlar cuánta información de llamadas registra IntelliTrace  
 De forma predeterminada, IntelliTrace registra información sobre todos los módulos usados por la solución. No obstante, IntelliTrace se puede configurar para que registre información de llamadas solo para los módulos que le interesen. En **Herramientas > Opciones > IntelliTrace > módulos**, puede especificar los módulos para incluir o excluir de IntelliTrace. De este modo, IntelliTrace recopilará únicamente los eventos que se originaron en los módulos especificados y las llamadas de método que se produjeron en los módulos de interés.  
  
 Para agregar varios módulos, utilice el carácter comodín * al principio o al final de la cadena. En los nombres de módulo, use nombres de archivo y no nombres de ensamblado. No se aceptan rutas de acceso a archivos.  
  
 Intente reducir al máximo el número de módulos, ya que el rendimiento mejora al tener que recopilar menos datos. También se obtiene menos ruido en la interfaz de usuario porque se deben recorrer menos datos.  
  
##  <a name="SaveSession"></a>Guardar datos de IntelliTrace en archivo  
 También puede guardar los datos recopilados por IntelliTrace va a **Depurar > IntelliTrace > Guardar sesión de IntelliTrace** mientras se está depurando y la aplicación está en un estado de interrupción. El elemento de menú está deshabilitado y no podrá guardar los datos recopilados por IntelliTrace si la aplicación se está ejecutando o si se ha detenido la depuración.  
  
 Puede configurar IntelliTrace para guardar automáticamente en un archivo, vaya a **Herramientas > Opciones > IntelliTrace > Opciones avanzadas** y seleccionando **almacenar registros de IntelliTrace en este directorio**. También puede configurar un tamaño fijo para el archivo generado; esto hará que IntelliTrace sobrescriba los datos más antiguos cuando se quede sin espacio. Visual Studio crea dos archivos para cada sesión de IntelliTrace cuando se guardan automáticamente y se activa el proceso de hospedaje de Visual Studio (vshost.exe).  
  
> [!TIP]
>  Para ahorrar espacio en disco, desactive la opción Guardar automáticamente los archivos cuando ya no necesite. Los archivos existentes no se eliminarán. Siempre hay la posibilidad de guardar en archivo desde el menú contextual.  
  
 Al guardar los datos de IntelliTrace en un archivo, se crea un archivo .itrace para cada proceso en el que recopile IntelliTrace. A continuación, puede abrir el archivo .itrace en Visual Studio, vaya a **archivo > Abrir > archivo** y seleccione el archivo .itrace en el cuadro de diálogo Abrir archivo. Para obtener más información, consulte [mediante los datos de IntelliTrace guardado](../debugger/using-saved-intellitrace-data.md).  
  
## <a name="blogs"></a>Blogs  
 [IntelliTrace en Visual Studio Enterprise 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/intellitrace-in-visual-studio-ultimate-2015.aspx)  
  
 [Tutorial de depuración en directo con IntelliTrace en Visual Studio 2015 (Editor de texto)](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor.aspx)  
  
 [Tutorial de depuración en directo con IntelliTrace en Visual Studio 2015 (Social Club)](http://blogs.msdn.com/b/visualstudioalm/archive/2000/1/1/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club.aspx)  
  
 [IntelliTrace en Visual Studio Enterprise 2015 ahora admite!](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach.aspx)  
  
 [Recopilar datos de un servicio de windows mediante el recolector independiente IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector.aspx)  
  
 [Editar el plan de recolección de IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2015/03/09/editing-the-intellitrace-collection-plan.aspx)  
  
 [TraceSource y depuración con IntelliTrace personalizados](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/17/custom-tracesource-and-debugging-using-intellitrace.aspx)  
  
 [Recopilador independiente IntelliTrace y grupos de aplicaciones se ejecutan en cuentas de Active Directory](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/22/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts.aspx)  
  
## <a name="forums"></a>Foros  
 [Depurador de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)  
  
## <a name="videos"></a>Vídeos  
 [Experiencia de IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)  
  
 [Depuración histórica con IntelliTrace en Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
