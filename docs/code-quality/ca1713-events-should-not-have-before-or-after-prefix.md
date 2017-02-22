---
title: "CA1713: Los eventos no deber&#237;an tener prefijos antes ni despu&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EventsShouldNotHaveBeforeOrAfterPrefix"
  - "CA1713"
helpviewer_keywords: 
  - "CA1713"
  - "EventsShouldNotHaveBeforeOrAfterPrefix"
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1713: Los eventos no deber&#237;an tener prefijos antes ni despu&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|  
|Identificador de comprobación|CA1713|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## Motivo  
 El nombre de un evento empieza por 'Before' o 'After'.  
  
## Descripción de la regla  
 Los nombres de evento deben describir la acción que provoca el evento.  Para nombrar los eventos relacionados que se provocan en una secuencia específica, utilice el tiempo presente o pasado para indicar la posición relativa en la secuencia de acciones.  Por ejemplo, al nombrar un par de eventos que se provocan al cerrar un recurso, debe nombrarlos 'Closing' y 'Closed', en lugar de 'BeforeClose' y 'AfterClose'.  
  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime.  Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.  
  
## Cómo corregir infracciones  
 Quite el prefijo del nombre de evento y considere el hecho de modificar el nombre para utilizar el tiempo presente o pasado de un verbo.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.