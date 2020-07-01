---
title: Uso de red | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 45fa397d-d7a1-4c4c-9c97-ede6c21643bd
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 20f7003bbcd319a6a8487d496697d3dcd0b7a18a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548426"
---
# <a name="network-usage"></a>Uso de red
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La herramienta de diagnóstico **Red** de Visual Studio recopila datos acerca de las operaciones de red realizadas mediante la [Windows.Web.Http API](https://msdn.microsoft.com/library/windows/apps/windows.web.http.aspx). Analizar los datos puede ayudarle a resolver problemas como los problemas de acceso y autenticación, uso incorrecto de la caché y rendimiento deficiente de visualización y descarga.  
  
 La herramienta de red admite solo las aplicaciones de plataforma universal de Windows. En este momento no se admiten otras plataformas.  
  
> [!NOTE]
> Para obtener una descripción más completa de la herramienta Red, consulte [Presentación de la herramienta de red de Visual Studio](https://devblogs.microsoft.com/visualstudio/?m=20155).  
  
## <a name="collecting-network-tool-data"></a>Recopilar datos de la herramienta de red  
 Debería ejecutar la herramienta **Red** con un proyecto de Visual Studio abierto en el equipo de Visual Studio.  
  
1. Abra el proyecto en Visual Studio.  
  
2. En el menú, haga clic en **depurar/generador de perfiles de rendimiento..**.. Elija **red**y, a continuación, elija **iniciar**.  
  
3. La herramienta de red comienza a recopilar el tráfico de red HTTP de la aplicación.  
  
    Al ejecutar la aplicación, la vista resumen en el panel izquierdo muestra automáticamente una lista de operaciones HTTP capturadas. Elija un elemento en la vista de resumen para ver más información en el panel de detalles del panel derecho.  
  
4. Elija **Detener** para cerrar la aplicación.  
  
   La ventana del informe debería tener un aspecto similar a este:  
  
   ![La ventana Red](../profiling/media/network-fullwindow.png "NETWORK_FullWindow")  
  
## <a name="analyzing-data"></a>Análisis de datos  
 Puede analizar el tráfico HTTP capturado mientras se ejecuta la aplicación, o incluso después de cerrarla, seleccionando cualquiera de las operaciones de red que se muestran en la vista de resumen.  
  
 La vista de resumen **Red** muestra los datos de cada operación de red durante la ejecución de la aplicación. Elija un encabezado de columna para ordenar la lista o seleccione los tipos de contenido que desea mostrar en la vista de filtro **Tipo de contenido**.  
  
 Elija **Guardar como HAR** para crear un archivo JSON que puedan utilizar las herramientas de terceros, como Fiddler.  
  
 La vista de detalles **Red** muestra más información sobre una operación de red en la vista de resumen.  
  
 ![Panel de detalles de la herramienta de red](../profiling/media/network-detailsviewpane.png "NETWORK_DetailsViewPane")  
  
|Nombre|Descripción|  
|-|-|  
|**Encabezados**|Información acerca de los encabezados de solicitud del evento.|  
|**Cuerpo**|Datos de carga de contenido de solicitud y respuesta.|  
|**Parámetros**|Los nombres y valores de los parámetros de la cadena de consulta.|  
|**Cookies**|Datos de la cookie de solicitud y respuesta.|  
|**Horarios**|Un gráfico de las fases del proceso de adquisición de los recursos seleccionados.|  
  
 La barra de **resumen** de Red muestra el número de operaciones de red que se muestran en un momento dado, cuántos datos se han transferido, cuánto tiempo llevó descargarlos y cuántos errores (solicitudes con respuestas 4xx o 5xx) hay visibles.  
  
### <a name="analysis-tips"></a>Sugerencias de análisis  
 Esta herramienta resalta determinadas áreas que pueden ser útiles al ejecutar análisis relacionados con redes:  
  
1. Las solicitudes que se atienden por completo desde la memoria caché se muestran como **(de caché)** en la columna **Recibido**. Esto puede ayudarle a determinar si se utiliza la caché de forma eficaz para ahorrar ancho de banda de usuario, o si está almacenando respuestas en caché por error y proporcionando datos obsoletos al usuario final de la aplicación.  
  
2. Las respuestas de error (4xx o 5xx) se muestran en la columna **Resultados** con un código de estado rojo, además de resaltarse en la barra de resumen. Esto hace fácil detectar errores entre las muchas solicitudes posibles en la aplicación.  
  
3. El botón de impresión bonita (dentro de la pestaña Cuerpo) puede ayudarle a analizar cargas de respuesta JSON, XML, HTML, CSS, JavaScript y TypeScript al aumentar la legibilidad del contenido.  
  
## <a name="see-also"></a>Consulte también  
 [Ejecutar herramientas de generación de perfiles sin depuración](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)   
 [Blog de Visual Studio: presentación del inspector de red de Visual Studio](https://blogs.msdn.com/b/visualstudio/)   
 [Vídeo de Channel 9: "Herramientas de diagnóstico de VS: nuevo generador de perfiles de red"](https://channel9.msdn.com/Series/ConnectOn-Demand/206)
