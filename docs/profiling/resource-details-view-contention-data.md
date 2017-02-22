---
title: "Vista Detalles de recursos: datos de contenci&#243;n del generador de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.resourcedetails"
helpviewer_keywords: 
  - "Detalles de recursos (vista)"
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista Detalles de recursos: datos de contenci&#243;n del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Detalles de recursos presenta un gráfico de escala de tiempo de los eventos de bloqueo producidos por las contenciones en un recurso seleccionado.  Los eventos de bloqueo se producen cuando un subproceso se ve obligado a suspender la ejecución porque otro subproceso ha bloqueado el acceso al recurso.  
  
 Esta vista representa la escala de tiempo de ejecución de cada subproceso como una barra horizontal y cada evento de bloqueo como una barra vertical en la escala de tiempo del subproceso.  Si es necesario, puede ampliar una sección de la escala de tiempo para ver eventos individuales.  Para ver la ruta de ejecución \(pila de llamadas\) de las funciones que condujeron al evento, haga clic en la barra del evento.  Las funciones aparecen en la ventana **Pila de llamadas**.  Si está disponible el código fuente de una función, puede hacer clic en el nombre de la función para editar el archivo de origen en la interfaz de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Procedimientos  
  
#### Para ampliar un segmento de la escala de tiempo  
  
-   Arrastre el puntero del mouse sobre un área de la escala de tiempo.  
  
     Al soltar el botón del mouse, la vista amplía el segmento de tiempo seleccionado.  Puede repetir el proceso para ampliar todavía más el segmento.  El cuadro de la barra de desplazamiento de tiempo representa el tamaño relativo del segmento de tiempo que aparece en la vista.  
  
#### Para alejar una escala de tiempo  
  
-   Realice uno de estos pasos:  
  
    -   Haga clic en **Alejar** para volver al nivel de zoom anterior.  
  
    -   Haga clic en **Restablecer zoom** para mostrar toda la escala de tiempo en la vista.  
  
#### Para ver la pila de llamadas de un evento  
  
-   En el gráfico de escala de tiempo, haga clic en la barra del evento.  
  
#### Para ver o editar el código fuente de una función en la pila de llamadas  
  
-   En la ventana **Pila de llamadas**, haga clic en el nombre de la función.  
  
 El código fuente de la función debe formar parte del proyecto actual.  
  
#### Para ver el árbol de llamadas de eventos de contención del recurso  
  
-   En el gráfico de escala de tiempo, haga clic en **Total**.  
  
     Aparece la vista Contenciones del recurso.  Para obtener más información, vea [Vista de conflictos de recursos](../profiling/resource-contentions-view-contention-data.md)  
  
#### Para ver todos los eventos de contención de un subproceso  
  
-   En el gráfico de escala de tiempo, haga clic en el nombre o el identificador del subproceso.  
  
     Aparece la vista Detalles del subproceso para el subproceso seleccionado.  Para obtener más información, vea [Detalles del subproceso \(vista\)](../profiling/thread-details-view-contention-data.md).