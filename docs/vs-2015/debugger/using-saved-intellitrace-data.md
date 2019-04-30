---
title: Uso de los datos de IntelliTrace guardados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.norepro
helpviewer_keywords:
- iTrace files
- IntelliTrace, log files
- IntelliTrace log files
- .iTrace files
ms.assetid: 9f2cce86-345a-4e22-84ba-91542d81e67a
caps.latest.revision: 112
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 549c4f5225773a7d9ac40c16a9db6ca9309c7d6f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437774"
---
# <a name="using-saved-intellitrace-data"></a>Uso de datos de IntelliTrace guardados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Inicie la depuración desde un archivo de registro de IntelliTrace (.iTrace) para ir a puntos concretos de la ejecución de la aplicación. Este archivo puede contener eventos de rendimiento, excepciones, subprocesos, pasos de prueba, módulos y otra información del sistema que IntelliTrace recopila mientras se ejecuta la aplicación.  
  
 Asegúrese de que tiene:  
  
- Archivos de código fuente y archivos de símbolos (.pdb) que coincidan para el código de la aplicación. De lo contrario, Visual Studio no puede resolver las ubicaciones de origen y muestra el mensaje "Símbolos no encontrados". Consulte [especificar símbolos (.pdb) y archivos de código fuente](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) y [diagnosticar problemas después de la implementación](../debugger/diagnose-problems-after-deployment.md).  
  
- Visual Studio Enterprise (y no las versiones Professional o Community) el equipo de desarrollo o en otro equipo para abrir los archivos .iTrace  
  
- Un archivo .iTrace de uno de estos orígenes:  
  
    |**Origen**|**Vea**|  
    |----------------|-------------|  
    |Una sesión IntelliTrace en Visual Studio Enterprise (pero no en las ediciones Professional o Community).|[Características de IntelliTrace](../debugger/intellitrace-features.md)|  
    |Una sesión de prueba en Microsoft Test Manager. Se asociará un archivo .iTrace a un elemento de trabajo de Team Foundation Server.|[Recopilar más datos de diagnóstico en las pruebas manuales](http://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2)|  
    |Microsoft Monitoring Agent, solo o con System Center 2012 R2 Operations Manager, para las aplicaciones web ASP.NET y las aplicaciones de SharePoint que se ejecutan en la implementación|-   [Diagnosis de problemas tras la implementación](../debugger/diagnose-problems-after-deployment.md)<br />-   [Novedades de System Center 2012 R2 Operations Manager](http://technet.microsoft.com/library/dn249700.aspx)|  
  
## <a name="GetStarted"></a> ¿Qué desea hacer?  
  
- [Abrir un registro de IntelliTrace](#Open)  
  
- [Obtener información sobre el registro de IntelliTrace](#Understand)  
  
- [Iniciar la depuración desde un registro de IntelliTrace](#StartDebugging)  
  
## <a name="Open"></a> Abrir un registro de IntelliTrace  
 En un equipo con Visual Studio Enterprise, abra el archivo .iTrace.  
  
- Haga doble clic en el archivo .iTrace fuera de Visual Studio o abra el archivo desde Visual Studio.  
  
     \- o -  
  
- Si el archivo .iTrace está asociado a un elemento de trabajo de Team Foundation Server, siga estos pasos en el elemento de trabajo:  
  
    - En **Todos los vínculos**, busque el archivo .iTrace. Ábralo.  
  
         \- o -  
  
    - En **Pasos de reproducción**, elija el vínculo **IntelliTrace** .  
  
> [!TIP]
> Si cerró el archivo IntelliTrace durante la depuración, puede volver a abrirlo fácilmente. Vaya al menú **Depuración** , elija **IntelliTrace**, **Mostrar resumen de registro**. También puede elegir **Mostrar resumen de registro** en la ventana de **IntelliTrace** . Esto solo está disponible durante la depuración con IntelliTrace.  
  
## <a name="Understand"></a> Obtener información sobre el registro de IntelliTrace  
 Algunas de las secciones siguientes del archivo .iTrace solo aparecen si recopiló datos de un origen determinado, por ejemplo, desde Test Manager o desde aplicaciones de SharePoint.  
  
|**Sección**|**Contiene**|**Origen de la recopilación**|  
|-----------------|------------------|---------------------------|  
|[Infracciones de rendimiento](#Performance)|Eventos de rendimiento con llamadas de función que superan el umbral configurado|Microsoft Monitoring Agent, solo o con System Center 2012 R2 Operations Manager para aplicaciones web ASP.NET hospedadas en IIS|  
|[Datos de excepción](#ExceptionData)|Excepciones, incluida la pila de llamadas completa de cada excepción|Todos los orígenes|  
|[Análisis](#Analysis)|Solo para aplicaciones de SharePoint 2010 y SharePoint 2013. Diagnostique los eventos de IntelliTrace y SharePoint, como eventos de depurador, eventos de ULS, excepciones no controladas y otros datos registrados por Microsoft Monitoring Agent.|Microsoft Monitoring Agent, solo o con System Center 2012 R2 Operations Manager|  
|[Información del sistema](#SystemInfo)|Configuración y especificaciones del sistema host|Todos los orígenes|  
|[Lista de subprocesos](#ThreadsList)|Subprocesos que se ejecutaron durante la recolección|Todos los orígenes|  
|[Datos de pruebas](#TestData)|Pasos de prueba y los resultados de una sesión de prueba|Administrador de pruebas|  
|[Módulos](#Modules)|Módulos que el proceso de destino ha cargado en el orden en que se cargaron.|Todos los orígenes|  
  
 A continuación se muestran algunas sugerencias que le ayudarán a encontrar información en cada sección:  
  
- Elija un encabezado de columna para ordenar los datos.  
  
- Use el cuadro de búsqueda para filtrar los datos. La búsqueda de texto sin formato funciona en todas las columnas excepto en las columnas de tiempo. También puede filtrar las búsquedas a una columna específica con un filtro por columna. Escriba el nombre de columna sin espacios, dos puntos (**:**) y el valor de la búsqueda. Incluya después un punto y coma (**;**) para agregar otra columna y buscar el valor.  
  
     Por ejemplo, para buscar los eventos de rendimiento que tienen la palabra “lento” en la columna **Descripción** , escriba:  
  
     `Description:slow`  
  
## <a name="StartDebugging"></a> Iniciar la depuración desde un registro de IntelliTrace  
  
### <a name="Performance"></a> Infracciones de rendimiento  
 Consulte los eventos de rendimiento que se registraron para la aplicación. Puede ocultar los eventos que no ocurren a menudo.  
  
##### <a name="to-start-debugging-from-a-performance-event"></a>Para iniciar la depuración desde un evento de rendimiento  
  
1. En **Infracciones de rendimiento**, consulte los eventos de rendimiento registrados, el tiempo de ejecución total y otra información del evento. A continuación, profundice más en los métodos que se llamaron durante un evento de rendimiento específico.  
  
     ![Visualización de los detalles del evento de rendimiento](../debugger/media/ffr-itsummarypageperformance.png "FFR_ITSummaryPagePerformance")  
  
     También puede hacer doble clic en el evento.  
  
2. En la página de eventos, revise los tiempos de ejecución de estas llamadas. Busque una llamada lenta en el árbol de ejecución.  
  
     Las llamadas más lentas aparecen en su propia sección si tiene varias llamadas, anidadas o de otra manera.  
  
3. Expanda esa llamada para revisar todas las llamadas anidadas y los valores de parámetro que se registraron en ese punto en el tiempo.  
  
     (Teclado: Para mostrar u ocultar una llamada anidada, presione las teclas **Flecha derecha** o **Flecha izquierda**, respectivamente. Para mostrar y ocultar los valores de parámetro de una llamada anidada, presione la tecla **Barra espaciadora** ).  
  
     Inicie la depuración desde la llamada.  
  
     ![Inicio de la depuración desde una llamada al método](../debugger/media/ffr-itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")  
  
     También puede hacer doble clic en la llamada o presionar la tecla **Entrar** .  
  
     Si el método está en el código de aplicación, Visual Studio va a ese método.  
  
     ![Consulta del código de la aplicación a partir del evento de rendimiento](../debugger/media/ffr-itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")  
  
     Ahora puede revisar otros valores registrados, la pila de llamadas, recorrer el código o utilizar la ventana **IntelliTrace** para [moverse hacia atrás o hacia delante “en el tiempo” por otros métodos](../debugger/intellitrace.md) a los que se llamó durante este evento de rendimiento.  
  
### <a name="ExceptionData"></a> Datos de excepción  
 Revise las excepciones que se produjeron y registraron para su aplicación. Puede agrupar las excepciones que tienen el mismo tipo y pila de llamadas para que solo vea la excepción más reciente.  
  
##### <a name="to-start-debugging-from-an-exception"></a>Para iniciar la depuración desde una excepción  
  
1. En **Datos de excepción**, revise los eventos de excepciones registrados, sus tipos, mensajes y cuándo se produjeron las excepciones. Para profundizar en el código, inicie la depuración desde el evento más reciente de un grupo de excepciones.  
  
     ![Inicio de la depuración a partir del evento de excepción](../debugger/media/ffr-itsummarypageexception.png "FFR_ITSummaryPageException")  
  
     También puede hacer doble clic en el evento. Si los eventos no están agrupados, elija **Depurar este evento**.  
  
     Si se produjo una excepción en el código de la aplicación, Visual Studio va al lugar donde se ha producido la excepción.  
  
     ![Consulta del código de la aplicación desde un evento de excepción](../debugger/media/ffr-itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")  
  
     Ahora puede revisar otros valores registrados, la pila de llamadas o utilizar la ventana **IntelliTrace** para [moverse hacia atrás o hacia delante “en el tiempo” por otros eventos registrados](../debugger/intellitrace.md), código relacionado y los valores registrados en esos puntos en el tiempo.  
  
    |**Columna**|**Muestra**|  
    |----------------|-------------------|  
    |**Tipo**|El tipo .NET de la excepción|  
    |**Mensaje más reciente** para excepciones agrupadas o **Mensaje** para excepciones no agrupadas|El mensaje que proporciona la excepción|  
    |**Recuento** para excepciones agrupadas|El número de veces que se produjo la excepción|  
    |**Id. del subproceso** para excepciones no agrupadas|El identificador del subproceso que produjo la excepción|  
    |**Hora del evento más reciente** u **Hora del evento**|La marca de hora registrada cuando se produjo la excepción|  
    |**Pila de llamadas**|Pila de llamadas para una excepción.<br /><br /> Para ver la pila de llamadas, elija una excepción de la lista. La pila de llamadas aparece bajo la lista de excepciones.|  
  
### <a name="Analysis"></a> Análisis  
 Diagnostique los problemas con aplicaciones de SharePoint 2010 y SharePoint 2013 mediante un identificador de correlación de SharePoint o revise todas las excepciones no controladas detectadas por Microsoft Monitoring Agent.  
  
- Use un identificador de correlación de SharePoint para buscar solicitudes web y eventos coincidentes. Elija un evento e inicie la depuración en el punto en el que se produjo el evento.  
  
- Si Microsoft Monitoring Agent ha encontrado excepciones no controladas, puede elegir una excepción e iniciar la depuración en el punto en el que se produjo la excepción.  
  
##### <a name="start-debugging-with-a-sharepoint-correlation-id"></a>Iniciar la depuración con un identificador de correlación de SharePoint  
  
1. Copie el identificador de correlación de SharePoint de su origen.  
  
    Por ejemplo:  
  
    ![IntelliTrace &#45; SharePoint error &#45; Id. de correlación](../debugger/media/sharepointerror-intellitrace.png "SharePointError_IntelliTrace")  
  
2. Abra el archivo .iTrace, después vaya a **Análisis** y especifique el identificador de correlación de SharePoint para revisar la solicitud web y los eventos registrados coincidentes.  
  
    ![Registro de IntelliTrace &#45; Id. de correlación de SharePoint escriba](../debugger/media/entersharepointcorrelationid.png "EnterSharePointCorrelationID")  
  
3. En **Eventos de solicitud**, examine los eventos. Empezando por el principio, los eventos aparecen en el orden en que se produjeron.  
  
   1. Elija un evento para ver sus detalles.  
  
   2. Elija **Iniciar depuración** para iniciar la depuración en el punto donde se produjo el evento.  
  
      ![Archivo de registro de IntelliTrace &#45; Ver solicitud de web &#43; eventos](../debugger/media/entersharepointcorrelationid2.png "EnterSharePointCorrelationID2")  
  
   Puede ver estas clases de eventos de SharePoint junto con los eventos de IntelliTrace:  
  
- **Eventos de perfil de usuario**  
  
     Estos eventos se generan cuando SharePoint carga un perfil de usuario y cuando se leen o se cambian las propiedades de perfil de usuario.  
  
- **Eventos del sistema de registro unificado (ULS)**  
  
     Microsoft Monitoring Agent registra un subconjunto de eventos ULS de SharePoint y estos campos:  
  
    |**Campo de IntelliTrace**|**Campo ULS de SharePoint**|  
    |----------------------------|------------------------------|  
    |**Id.**|**Id. de evento**|  
    |**Nivel**|**Nivel**|  
    |**Identificador de categoría**|**Identificador de categoría**|  
    |**Categoría**|**Categoría**|  
    |**Área**|**Producto**|  
    |**Salida**|**Mensaje**|  
    |**Id. de correlación**|**Id. de correlación**|  
  
##### <a name="start-debugging-from-an-unhandled-exception"></a>Iniciar la depuración desde una excepción no controlada  
  
1. Elija un identificador de correlación de SharePoint de una excepción. Las excepciones se agrupan por tipo y pila de llamadas.  
  
2. (Opcional) Expanda **Pila de llamadas** para ver la pila de llamadas de un grupo de excepciones.  
  
3. Elija **Depurar excepción** para iniciar la depuración en el punto en el que se produjo la excepción.  
  
    ![Registro de IntelliTrace &#45; las excepciones no controladas de SharePoint](../debugger/media/sharepointunhandledexceptions-intellitrace.png "SharePointUnhandledExceptions_IntelliTrace")  
  
   Para ver un tutorial, vea [Tutorial: Depurar una aplicación de SharePoint mediante IntelliTrace](http://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4). Para los tipos de datos que registra el agente, vea [las características de IntelliTrace](../debugger/intellitrace-features.md).  
  
### <a name="ThreadsList"></a> Lista de subprocesos  
 Examine los subprocesos registrados que se ejecutaron en el proceso de destino. Puede iniciar la depuración desde el primer evento válido de IntelliTrace en un subproceso seleccionado.  
  
##### <a name="to-start-debugging-from-a-specific-thread"></a>Para iniciar la depuración desde un subproceso concreto  
  
1. En **Lista de subprocesos**, elija un subproceso.  
  
2. En la parte inferior de **Lista de subprocesos**, elija **Iniciar depuración**. También puede hacer doble clic en un subproceso.  
  
    Para iniciar la depuración desde donde se inicia la aplicación, haga doble clic en **Subproceso principal**. Consulte [las características de IntelliTrace](../debugger/intellitrace-features.md).  
  
   Los datos de subproceso que el usuario crea podrían ser más útiles que los subprocesos que un servidor crea y administra para las aplicaciones web hospedadas en IIS.  
  
|**Columna**|**Muestra**|  
|----------------|-------------------|  
|**ID**|El número de identificador del subproceso|  
|**Name**|El nombre del subproceso. Los subprocesos sin nombre se muestran como “\<Sin nombre>”.|  
|**Hora de inicio**|La hora en que se creó el subproceso|  
|**Hora de finalización**|La hora en que se completó el subproceso|  
  
### <a name="TestData"></a> Datos de pruebas  
 Examine los datos de IntelliTrace que registró Test Manager mientras probaba la aplicación.  
  
##### <a name="to-start-debugging-from-a-specific-test-step"></a>Para iniciar la depuración desde un paso de prueba específico  
  
1. Expanda **Cuadrícula de pasos de prueba**. Elija un paso de prueba.  
  
2. En la parte inferior de **Cuadrícula de pasos de prueba**, elija **Iniciar depuración**. También puede hacer doble clic en un paso de prueba.  
  
     Se iniciará la depuración desde el primer evento válido de IntelliTrace después del paso de prueba seleccionado.  
  
     Cuando existen datos de prueba, IntelliTrace intenta resolver la compilación de Team Foundation Server asociada que se usó para realizar la serie de pruebas. Si se encuentra la compilación, los símbolos asociados de la aplicación se resuelven automáticamente.  
  
|**Campo**|**Muestra**|  
|---------------|-------------------|  
|**Sesión de prueba**|Las sesiones de pruebas que se han registrado. Normalmente, solo hay una. Esta lista está vacía si los datos de prueba se crearon mediante una prueba exploratoria manual.|  
|**Caso de prueba**|Los casos de prueba de la sesión de prueba seleccionada. Esta lista está vacía si los datos de prueba se crearon mediante una prueba exploratoria manual.|  
|**Cuadrícula de pasos de prueba**|Los pasos de prueba que se registraron con el resultado de éxito o fracaso de las pruebas|  
  
### <a name="SystemInfo"></a> Información del sistema  
 En esta sección se muestran los detalles del sistema que hospedó la aplicación, como el hardware, el sistema operativo e información específica del entorno y del proceso.  
  
### <a name="Modules"></a> Módulos  
 En esta sección se muestran los módulos que cargó el proceso de destino. Los módulos aparecen en el orden en que se cargaron.  
  
|**Columna**|**Muestra**|  
|----------------|-------------------|  
|**Nombre del módulo**|Nombre de archivo del módulo|  
|**Ruta de acceso del módulo**|Ubicación del disco en el que se cargó el módulo|  
|**Identificador del módulo**|Identificador único del módulo específico de esta versión que ayuda a encontrar archivos de símbolos (PDB) coincidentes. Vea [Finding symbol (.pdb) files and source files](http://msdn.microsoft.com/05384c85-d264-4e18-abaa-aa482ab25470).|  
  
### <a name="where-can-i-get-more-information"></a>¿Dónde puedo obtener más información?  
 [Usar el recopilador independiente de IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
 [Características de IntelliTrace](../debugger/intellitrace-features.md)  
  
 [Recopilar más datos de diagnóstico en las pruebas manuales](http://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2)  
  
 [IntelliTrace](../debugger/intellitrace.md)  
  
#### <a name="forums"></a>Foros  
 [Depurador de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)  
  
#### <a name="guidance"></a>Orientación  
 [Pruebas para entrega continua con Visual Studio 2012 – capítulo 6: Un cuadro de herramientas de pruebas](http://go.microsoft.com/fwlink/?LinkID=255203)
