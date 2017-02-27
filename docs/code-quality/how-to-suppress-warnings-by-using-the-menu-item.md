---
title: "C&#243;mo: Suprimir advertencias mediante el elemento de men&#250; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "advertencias, suprimir"
  - "análisis de código, suprimir advertencias"
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# C&#243;mo: Suprimir advertencias mediante el elemento de men&#250;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  La supresión de código fuente no se admite en C\/C\+\+ ni en los proyectos de sitios web.  
  
 Se puede usar la ventana de Análisis de código para suprimir las advertencias de análisis de código.  Suprimir una advertencia no es lo mismo que deshabilitarla.  Cuando se suprime una advertencia, sólo se aplica a una instancia determinada de la infracción.  Las demás infracciones de la misma advertencia se continuarán registrando en la ventana Lista de errores.  
  
 Después de ejecutar el análisis de código, se podría determinar que una o varias de las advertencias del análisis de código que se muestran en la ventana de Análisis de código no son válidas para su aplicación.  Por ejemplo, es posible que determine que el código está correcto así.  Pero también puede suceder que haya algunas infracciones de prioridad baja que no se corrijan en el ciclo de desarrollo actual.  Independientemente del motivo, con frecuencia resulta útil indicar que la advertencia no es aplicable, para hacerles saber a los miembros del equipo que el código se ha revisado y que se ha determinado que la advertencia podía suprimirse.  En el código fuente, la supresión es útil porque permite colocar una supresión cerca de donde se genera la advertencia.  
  
 Puede elegir si la supresión aparecerá en el código fuente o en el archivo de supresión global.  Algunas supresiones se deben colocar en el archivo de supresión global.  Si éste es el caso, la opción **En origen** estará deshabilitada.  
  
### Para suprimir una advertencia con un elemento de menú  
  
1.  En el menú **Analizar**, elija **Ventanas** y elija **Análisis de código**.  
  
2.  En la ventana **Análisis de código**, seleccione suprimir la advertencia.  
  
3.  Elija Acciones, luego **Suprimir mensaje\(s\)**, y elija **En código fuente** o **Archivo de supresión en el proyecto**.  
  
     Se suprime la advertencia correspondiente y ésta aparece tachada en la ventana de Análisis de código.  
  
> [!NOTE]
>  Las supresiones que no tienen destino aparecen en el archivo de supresiones global.