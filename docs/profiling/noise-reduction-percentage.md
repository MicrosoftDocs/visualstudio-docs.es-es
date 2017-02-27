---
title: "Porcentaje de reducci&#243;n de ruido | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.filter"
helpviewer_keywords: 
  - "Visualizador de simultaneidad, Porcentaje de reducción de ruido"
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Porcentaje de reducci&#243;n de ruido
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

De forma predeterminada, el valor de la opción Porcentaje de reducción de nodos irrelevantes es 2.  Solamente las entradas que tienen un porcentaje de tiempo inclusivo mayor o igual que este valor se muestran en el árbol de llamadas.  Puede controlar el número de entradas que aparecen en el árbol de llamadas modificando el valor.  Por ejemplo, si cambia el valor a 10, solamente se mostrarán las entradas del árbol de llamadas que tienen un tiempo inclusivo mayor o igual que el 10%.  Si aumenta el valor de esta opción, puede concentrar la atención en las entradas que tienen un impacto mayor sobre el rendimiento del proceso.