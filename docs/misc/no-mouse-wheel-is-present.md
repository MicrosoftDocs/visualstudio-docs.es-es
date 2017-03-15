---
title: "No hay rueda del mouse presente. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrMouse_NoWheelIsPresent"
ms.assetid: e924ffba-4af1-4247-9a6f-d19a03738f62
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No hay rueda del mouse presente.
Se llamó a la propiedad `My.Computer.Mouse.WheelScrollLines`, pero el mouse no tiene rueda del mouse.  
  
### Para corregir este error  
  
-   Compruebe la propiedad `My.Computer.Mouse.WheelExists` para ver si el mouse tiene una rueda antes de llamar a la propiedad `My.Computer.Mouse.WheelScrollLines`.  
  
     O bien  
  
-   Instale un mouse con una rueda en el equipo.  
  
## Vea también  
 [Propiedad My.Computer.Mouse.WheelScrollLines](http://msdn.microsoft.com/es-es/67600f96-25d7-4dd9-946a-b46e1fc6a57f)   
 [Propiedad My.Computer.Mouse.WheelExists](http://msdn.microsoft.com/es-es/332d44f7-0b66-4eaa-b4ce-d7f161bfbd07)   
 [Control de excepciones y errores en Visual Basic](http://msdn.microsoft.com/es-es/3e351e73-cf23-40ab-8b60-05794160529e)