---
title: Lista de eventos gráficos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 555a786ceed97bb83b0924eef45f102c43755b2e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870747"
---
# <a name="graphics-event-list"></a>Lista de eventos gráficos
Use la lista de eventos gráficos del Analizador de gráficos de Visual Studio para explorar los eventos Direct3D que se registraron mientras se presentaba un fotograma de su juego o aplicación.  

 Esta es la lista de eventos:  

 ![Una lista de eventos que tienen "Índice" en su nombre. ](media/gfx_diag_demo_event_list_orientation.png "gfx_diag_demo_event_list_orientation")  

## <a name="using-the-event-list"></a>Uso de la lista de eventos  
 Cuando selecciona un evento de la lista de eventos, se refleja en la información que muestran otras herramientas de análisis de gráficos. Si usa la lista en sintonía con estas otras herramientas, puede examinar un problema de representación en detalle para determinar su causa. Para obtener más información sobre cómo solucionar problemas de presentación usando la lista de eventos junto con otras herramientas de Análisis de gráficos, consulte [Ejemplos](graphics-diagnostics-examples.md).  

 Utilizar las funciones de la lista de eventos eficazmente es importante para eludir fotogramas complejos que pueden contener miles de eventos. Para utilizar la lista de eventos eficazmente, elija la vista que mejor le convenga, utilice la búsqueda para filtrar la lista de eventos, siga los vínculos para aprender más sobre los objetos de Direct3D que están asociados con un evento y utilice los botones de flecha para moverse entre las llamadas de dibujo rápidamente.  

### <a name="color-coded-events-in-direct3d-12"></a>Eventos codificados por colores en Direct3D 12  
 Direct3D 12 expone varias colas que corresponden a las distintas funciones del hardware. Para facilitar la identificación de la cola asociada a un evento de gráficos en Direct3D 12, los eventos se codifican por colores en la lista según su cola de eventos cuando se trabaja con una captura de una aplicación Direct3D 12.  

|Cola de Direct3D 12|Color|  
|-----------------------|-----------|  
|Cola de representación|Verde|  
|Cola de proceso|Amarillo|  
|Cola de copia|Naranja|  

 Direct3D 11 no expone varias colas, de modo que los eventos no están codificados por colores en la lista de eventos cuando se trabaja con una captura de una aplicación de Direct3D 11.  

### <a name="event-list-views"></a>Vistas de la lista de eventos  
 La lista de eventos tiene dos vistas diferentes que organizan los eventos de gráficos de maneras diferentes, para adaptarse así a su flujo de trabajo y preferencias. La primera vista es la *vista de trabajo de GPU* que organiza jerárquicamente los eventos y su estado asociado. La segunda vista es la *vista de escala de tiempo* , que organiza los eventos cronológicamente, en una lista plana.  

 El **trabajo de GPU** vista  
 Muestra los eventos capturados y su estado en una jerarquía. El nivel superior de la jerarquía está hecho de eventos, como llamadas de dibujo, borrados, presentes y los relacionados con las vistas. En la lista de eventos, puede expandir las llamadas de dibujo para mostrar el estado del dispositivo en el momento de la llamada a draw y expandir el estado para mostrar los eventos que establecen sus valores. En este nivel, también puede ver si un estado concreto se estableció en un fotograma previo o si se ha establecido más de una vez desde la última llamada a draw.  

 La vista de **Escala de tiempo**  
 Muestra todos los eventos capturados en orden cronológico. Esta manera de organizar la lista de eventos es la misma que en las versiones anteriores de Visual Studio.  

##### <a name="to-change-the-event-list-view-mode"></a>Cambio de la vista de la lista de eventos  

-   En el **lista de eventos gráficos** ventana, encima de la lista de eventos, busque el **vista** lista desplegable y elija entre la **escala de tiempo** vista o la **detrabajodeGPU** vista.  

### <a name="filtering-events"></a>Filtrado de eventos  
 Puede utilizar el Cuadro de búsqueda, situado en la esquina superior derecha de la ventana **Lista de eventos gráficos** , para filtrar la lista de eventos de modo que incluya solo los eventos cuyo nombre contenga determinadas palabras clave. Puede especificar una palabra clave, como `Vertex`(como se muestra en la ilustración anterior), o varias palabras clave separadas por un punto y coma, como `Draw;Primitive`, lo que mostrará eventos que tengan tanto `Draw` como `Primitive` en sus nombres. Las búsquedas distinguen los espacios (por ejemplo, `VSSet` y `VS Set` son búsquedas diferentes, de modo que debe efectuarlas con cuidado).  

### <a name="moving-between-draw-calls"></a>Cómo moverse entre llamadas de dibujo  
 Dada la importancia de examinar las llamadas a `Draw` , puede usar los botones **Ir a la siguiente llamada a draw** e **Ir a la llamada a draw anterior** , situados en la esquina superior izquierda de la ventana **Lista de eventos gráficos** , para buscar las llamadas a draw y pasar rápidamente de una a otra.  

### <a name="links-to-graphics-objects"></a>Vínculos a objetos gráficos  
 Para entender ciertos eventos gráficos, es posible que necesite información adicional sobre el estado actual de Direct3D o los objetos Direct3D a los que hace referencia el evento. Muchos eventos ofrecen vínculos a esta información, que puede seguir para obtener más detalles.  

## <a name="kinds-of-events-and-event-markers"></a>Tipos y marcadores de eventos  
 Los eventos que se muestran en la lista de eventos se organizan en cuatro categorías: eventos generales, eventos de dibujo, grupos de eventos definidos por el usuario y marcadores de eventos definidos por el usuario. Excepto los eventos generales, cada evento se muestra junto con un icono que indica la categoría a la que pertenece.  

|Iconos|Descripción del evento|  
|----------|-----------------------|  
|(sin icono)|Evento general<br /> Cualquier evento que no sea un evento definido por el usuario, un grupo de eventos definido por el usuario o un evento de dibujo.|  
|![El icono de evento draw](media/vsg_eventlist_icon_draw.png "vsg_eventlist_icon_draw")|Evento de dibujo<br /> Marca un evento de dibujo que ha ocurrido durante el fotograma capturado.|  
|![El usuario&#45;definido por el icono de marcador de evento](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Grupo de eventos definido por el usuario<br /> Eventos relacionados con grupos, definidos por la aplicación.|  
|![El usuario&#45;definido por el icono de marcador de evento](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|Marcador de eventos definido por el usuario<br /> Marca una ubicación específica, definida por la aplicación.|  

## <a name="marking-user-defined-events-in-your-app"></a>Marcar eventos definidos por el usuario en la aplicación  
 Los eventos definidos por el usuario son específicos de la aplicación. Puede utilizarlos para correlacionar eventos importantes que ocurren en su aplicación con eventos de la Lista de eventos gráficos. Por ejemplo, puede crear grupos de eventos definidos por el usuario para organizar eventos relacionados, como los que presentan la interfaz de usuario, en grupos o jerarquías, para poder examinar la lista de eventos más fácilmente o crear marcadores cuando se dibujan ciertos tipos de objetos y así poder encontrar fácilmente sus eventos de gráficos en la lista de eventos.  

 Para crear grupos y marcadores en la aplicación, utilice las mismas API que ofrece Direct3D para que la utilicen otras herramientas de depuración de Direct3D. A veces, estas API cambian entre versiones de Direct3D, pero las funciones básicas son las mismas.  

### <a name="user-defined-events-in-direct3d-12"></a>Eventos definidos por el usuario en Direct3D 12  
 Para crear grupos y marcadores en Direct3D 12, use las API descritas en esta sección. En la tabla siguiente se resumen las API que puede usar según si está marcando eventos en una cola de comandos o en una lista de comandos.  

|Descripción de la API|[ID3D12CommandQueue](/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)|[ID3D12GraphicsCommandList](/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)|  
|---------------------| - | - |  
|Comprobar la disponibilidad de evento definido por el usuario|[PIXGetStatus](https://msdn.microsoft.com/library/f7ebd985-fb5d-46d7-abec-099df4b9be0e)|[PIXGetStatus](http://msdn.microsoft.com/en-us/1046ac43-a0a3-42bf-bae8-14aa72fa7567)|  
|Empezar un grupo de eventos|[PIXBeginEvent](http://msdn.microsoft.com/en-us/5f51fff7-f313-4558-965b-2a443653cd7b)|[PIXBeginEvent](http://msdn.microsoft.com/en-us/4ddb3311-b9b5-449a-bbfb-7634e0d56e87)|  
|Finalizar un grupo de eventos|[PIXEndEvent](http://msdn.microsoft.com/en-us/fb526bf2-c17d-4a2a-8665-3b577a0f7fba)|[PIXEndEvent](http://msdn.microsoft.com/en-us/a3cd34a9-9dd9-40e1-ae86-0214b25ff185)|  
|Crear un marcador de eventos|[PIXSetMarker](http://msdn.microsoft.com/en-us/0caf49ed-c99d-405e-89f4-0c887b8474ad)|[PIXSetMarker](http://msdn.microsoft.com/en-us/6610e5b9-a0c5-4236-b551-b6eb9fac64c1)|  

### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Eventos definidos por el usuario en Direct3D 11 y versiones anteriores  
 Para crear grupos y marcadores en Direct3D 11 o versiones anteriores, use las API descritas en esta sección. En la tabla siguiente se resumen las API que puede usar para las distintas versiones de Direct3D 11 y versiones anteriores de Direct3D.  

|Descripción de la API|[ID3D11DeviceContext2](/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) (Direct3D 11.2)|[ID3DUserDefinedAnnotation](http://go.microsoft.com/fwlink/p/?LinkID=250967) (Direct3D 11.1)|Familia D3DPerf_API (Direct3D 11.0 y versiones anteriores)|  
|---------------------| - | - | - |  
|Empezar un grupo de eventos|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|  
|Finalizar un grupo de eventos|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|  
|Crear un marcador de eventos|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|  

 Puede utilizar cualquiera de estas API que sea compatible con su versión de Direct3D, por ejemplo, si tiene como destino la API de Direct3D 11.1, puede utilizar `SetMarker` o `D3DPerf_SetMarker` para crear un marcador de evento, pero no `SetMarkerInt` , porque solo está disponible en Direct3D 11.2, e incluso puede juntar las que son compatibles con versiones diferentes de Direct3D en la misma aplicación.  

<!-- VERSIONLESS -->
<a name="resource-history"></a>
## <a name="resource-history"></a>Historial de recursos
Visual Studio 2017 y versiones posteriores contienen la **historial de recursos** ventana.  Seleccione el icono de inspección ![icono inspección](media/gfx_watch.png) junto a una entrada en el **lista de eventos** se abrirá la ventana la **historial de recursos** ventana se muestra a continuación:

![Historial de recursos](media/gfx_diag_resource_history.png)

Esta ventana le permite ver el historial del elemento seleccionado en la lista de eventos.  Sirve para seleccionar otros elementos para ver el historial de la lista desplegable en la parte superior.  La mitad superior de la ventana contiene los **eventos de configuración de marco**.  Estos son los eventos que pertenecen a la *crear* categoría de tipos y son las llamadas que suelen inicializaron y creación el recurso.  La parte inferior de la ventana de la mitad contiene el **eventos de fotogramas** sección.  Estos son la lectura normal y escriben los eventos que se producen durante el uso del recurso.  


| Columna | Descripción |
|-----------| - |
| **Type** | Muestra el tipo de la entrada, normalmente *crear*, *lectura* y *escribir*. |
| **Vista** | Muestra una vista en miniatura del recurso en ese momento.  Haga doble clic en la miniatura para abrir una vista de detalles del recurso en ese momento. |
| **Event** | Se muestra la llamada de método que se produjeron que generó el evento.  Cualquier historial adicional en los elementos individuales se puede ver seleccionando el icono de inspección ![icono inspección](media/gfx_watch.png) en la línea adecuada.  Además, cualquier elemento que se dibuja en el texto azul, tales como `m_commandList` en la captura de pantalla anterior, se puede seleccionar para obtener más detalles. |

<!-- /VERSIONLESS -->

## <a name="see-also"></a>Vea también  
 [Tutorial: Objetos ausentes debido al estado del dispositivo](walkthrough-missing-objects-due-to-device-state.md)