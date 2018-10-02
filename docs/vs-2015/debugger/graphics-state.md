---
title: Estado de los gráficos | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.statewindow
ms.assetid: 97e7757e-c372-4626-8149-99a81367a0e1
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 00b53745cc7a166d32633897c65888f4018f6068
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576028"
---
# <a name="graphics-state"></a>Estado de los gráficos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [estado de los gráficos](https://docs.microsoft.com/visualstudio/debugger/graphics/graphics-state).  
  
La ventana de estado de diagnóstico de gráficos de Visual Studio ofrece información sobre el estado activo de los gráficos en el momento del evento actual (por ejemplo, durante una llamada a draw).  
  
## <a name="understanding-the-state-window"></a>Descripción de la ventana de estado  
 La ventana de estado recopila información sobre el estado que afecta a la representación y la presenta de forma jerárquica, en un solo lugar. Dependiendo de la versión de Direct3D que usa la aplicación, pueden apreciarse ciertas diferencias en la información que se presenta en la ventana de estado.  
  
### <a name="state-views"></a>Vistas de estado  
 La tabla de estado puede verse de varias maneras:  
  
|Ver|Descripción|  
|----------|-----------------|  
|Vista de estado de entrada de la API|Esta vista presenta el estado con un diseño similar a los objetos de Direct3D que lo componen.|  
|Vista de estado de entrada lógica|Esta vista presenta el estado en una vista lógica que no refleja el diseño de los objetos de Direct3D que lo componen.|  
|Vista de estado anclado|En lugar de aplicar una estructura jerárquica, la vista de estado anclado presenta los elementos de estado anclado en una lista plana con nombres completos. Esta vista permite ver muchos elementos de estado de diferentes agrupaciones de estado en unas pocas líneas.|  
  
##### <a name="to-change-the-state-view"></a>Para cambiar la vista de estado:  
  
-   En la ventana de estado, vaya a la esquina superior izquierda, justo debajo de la barra de título, y elija el botón correspondiente al estilo de vista de estado que desea usar.  
  
    -   **Mostrar la vista de estado de entrada de API**  
  
    -   **Vista Mostrar estado lógico**  
  
    -   **Vista Mostrar estado anclado**  
  
> [!IMPORTANT]
>  Debe anclar el estado en el **API Mostrar estado de entrada** o **Mostrar estado lógico** vistas para que se muestre en el **vista Mostrar estado anclado**.  
  
### <a name="state-table-format"></a>Formato de la tabla de estado  
 La ventana de estado contiene varias columnas de información.  
  
|Columna|Descripción|  
|------------|-----------------|  
|nombre|El nombre del elemento de estado. Si este elemento representa una agrupación de estado, puede expandirse para mostrarla.<br /><br /> En el **vista de estado de entrada de API** y **vista estado lógico** indica que se aplica sangría a los nombres para mostrar la relación jerárquica entre Estados.<br /><br /> En el **vista de estado anclado** de estado, se muestran los nombres completos en una lista plana.|  
|Valor|El valor del elemento de estado.|  
|Tipo|El tipo del elemento de estado.|  
  
### <a name="changed-state"></a>Cambio de estado  
 Por lo general, el estado de los gráficos cambia de forma incremental entre las sucesivas llamadas a draw. Si se cambia el estado de forma incorrecta, pueden producirse diversos problemas de representación. Para que resulte más fácil la localización del estado que ha cambiado desde la llamada a draw anterior, se marca con un asterisco y se muestra en rojo (no solo el estado, sino también su correspondiente elemento de estado primario). De este modo, puede identificar con facilidad el estado que ha cambiado en el nivel superior y, a continuación, explorar los detalles en profundidad.  
  
### <a name="pinning-state"></a>Estado anclado  
 Dado que muchas aplicaciones representan objetos similares de forma secuencial, cuando se cambia un conjunto de estado conocido, a veces resulta útil anclar los estados que cambian en su lugar para ver cómo cambia este conjunto mientras se pasa de una llamada a draw a otra.  
  
 Esto también puede resultar útil si se ha aislado el origen de un problema generado por un cambio en un estado en particular.  
  
##### <a name="to-pin-state-in-place"></a>Para anclar el estado en su lugar:  
  
1.  En la ventana de estado, busque el estado que le interesa. Posiblemente deberá expandir el estado de alto nivel para localizar los detalles que le interesan.  
  
2.  Sitúe el cursor sobre el estado que le interesa. Aparecerá un icono de pin a la izquierda del elemento de estado.  
  
3.  Para anclar el elemento de estado en su lugar, elija el icono de pin.



