---
title: "Soluci&#243;n de problemas de excepciones: System.Exception | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.Exception (excepción)"
  - "clases base, excepciones"
  - "excepciones, clase base"
ms.assetid: fc15931a-9323-47c6-a42f-55d0534b939a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Exception
Representa los errores que se producen durante la ejecución de una aplicación. Es la clase base de todas las excepciones.  
  
## Sugerencias asociadas  
 **Compruebe la propiedad InnerException para obtener más información.**  
 Para corregir el error, es probable que necesite información sobre la excepción interna \(o anterior\) que dio lugar a la excepción actual. La propiedad <xref:System.Exception.InnerException%2A> de la excepción actual contiene la excepción interna. Puede utilizar el vínculo **Ver detalle** del cuadro de diálogo **Asistente de excepciones** para obtener acceso a la propiedad <xref:System.Exception.InnerException%2A>.  
  
 **Desactive temporalmente la depuración de Sólo mi código.**  
 La excepción puede haberse producido en código que no haya escrito usted mismo. Para depurar dicho código, es posible que tenga que desactivar la depuración de Sólo mi código. Para obtener más información, consulta [General, Depuración, Opciones \(Cuadro de diálogo\)](../debugger/general-debugging-options-dialog-box.md).  
  
## Vea también  
 <xref:System.Exception>   
 <xref:System.Exception.InnerException%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Cómo: Interrumpir cuando se produce una excepción](../misc/how-to-break-when-an-exception-is-thrown.md)   
 [General, Depuración, Opciones \(Cuadro de diálogo\)](../debugger/general-debugging-options-dialog-box.md)