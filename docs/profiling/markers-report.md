---
title: "Informe de marcadores | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.report.markers"
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Informe de marcadores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El Informe de marcadores lista los marcadores en el intervalo de tiempo mostrado.  Acercarse, alejarse u ocultar carriles podría hacer que los marcadores aparecieran o desaparecieran  El informe contiene esta información sobre cada marcador:  
  
-   El momento en que comenzó, relativo al inicio del seguimiento.  
  
-   Su duración.  La duración es cero para las marcas y los mensajes porque representan un instante.  
  
-   El identificador del subproceso que lo generó.  
  
-   El proveedor del seguimiento de eventos de Windows \(ETW\) que lo generó.  
  
-   La ejecución del marcador desde la que se escribió.  
  
-   La categoría de eventos a la que pertenece.  
  
-   El nivel de importancia.  
  
-   El tipo \(intervalo, marca o mensaje\).  
  
-   Descripción de alto nivel de lo que representa  
  
 Elija el botón **Exportar** para guardar el informe de marcadores como un archivo CSV.  Se pueden utilizar los datos del archivo CSV con otras aplicaciones o herramientas.  
  
> [!NOTE]
>  El Informe de marcadores puede mostrar hasta 1.000 marcadores.  Para ver todos los marcadores, exporte el informe detallado a un archivo CSV.