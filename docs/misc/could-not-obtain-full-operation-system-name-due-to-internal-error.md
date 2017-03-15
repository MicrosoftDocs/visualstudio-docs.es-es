---
title: "No se pudo obtener el nombre completo del sistema operativo debido a un error interno | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrDiagnosticInfo_FullOSName"
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se pudo obtener el nombre completo del sistema operativo debido a un error interno
No se pudo obtener el nombre completo del sistema operativo debido a un error interno. La causa podría ser que WMI no exista en la máquina actual.  
  
 Error al llamar a la propiedad `My.Computer.Info.OSFullName`. Una posible causa de este error es que Instrumental de administración de Windows \(WMI\) no esté instalado en el equipo actual.  
  
### Para corregir este error  
  
1.  Agregue un bloque `Try...Catch` alrededor de la llamada a la propiedad `My.Computer.Info.OSFullName`.  
  
2.  Para más información acerca de WMI y cómo instalarlo, vaya a  y busque el "Servicio principal Instrumental de administración de Windows".  
  
## Vea también  
 [Propiedad My.Computer.Info.OSFullName](http://msdn.microsoft.com/es-es/b3b0fbd1-4dc5-428a-ad04-0d9fc9c2a9be)   
 [Control de excepciones y errores en Visual Basic](http://msdn.microsoft.com/es-es/3e351e73-cf23-40ab-8b60-05794160529e)   
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)