---
title: "Esta aplicaci&#243;n de una sola instancia no pudo conectar con la instancia original | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrAppModel_SingleInstanceCantConnect"
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Esta aplicaci&#243;n de una sola instancia no pudo conectar con la instancia original
Esta aplicación de una sola instancia no pudo conectar con la instancia original. Algunas de las posibles causas de este problema son:  
  
-   La instancia original ha dejado de responder.  
  
-   La aplicación no tiene permisos para crear los objetos de kernel. Para más información sobre los objetos de kernel, vea [Mutexes](../Topic/Mutexes.md).  
  
     El nombre base de los objetos de kernel procede de concatenar el GUID del ensamblado, el número de la versión principal y el número de la versión secundaria. Por ejemplo, el nombre base podría ser `3639f15d-9547-43da-8145-60da347829915.1`.  
  
### Para corregir este error al desarrollar la aplicación  
  
1.  Compruebe que la aplicación no entra en un estado que no responde.  
  
2.  Compruebe que la aplicación tiene permisos suficientes para crear objetos de kernel.  
  
3.  Reinicie la instancia original de la aplicación.  
  
4.  Reinicie el equipo para borrar cualquier proceso que pueda estar haciendo uso del recurso necesario para conectarse a la aplicación de instancia original.  
  
5.  Anote las circunstancias en las que se produjo el error y llame a los Servicios de soporte técnico de Microsoft.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Cómo: Especificar el comportamiento de las instancias para una aplicación \(Visual Basic\)](http://msdn.microsoft.com/es-es/48539ad8-d960-4210-beab-ee65f6c6dc6e)   
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)   
 [PAVEOVER Compatibilidad de productos y accesibilidad](http://msdn.microsoft.com/es-es/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)