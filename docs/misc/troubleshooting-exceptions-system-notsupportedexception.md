---
title: "Soluci&#243;n de problemas de excepciones: System.NotSupportedException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "NotSupportedException (clase)"
ms.assetid: a214e851-ee0f-4bbd-9f72-8769046526f3
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.NotSupportedException
Cuando un método invocado no es compatible o cuando se intenta leer, buscar o escribir en una secuencia que no es compatible con la funcionalidad invocada, se produce una excepción <xref:System.NotSupportedException>.  
  
## Sugerencias asociadas  
 **Asegúrese de que el método es compatible.**  
 Existen métodos que no son compatibles con la clase base, pero se espera que sean compatibles con las clases derivadas. Si una clase derivada implementa solamente un subconjunto de los métodos de su clase base, se producirá una excepción <xref:System.NotSupportedException> para los métodos no compatibles.  
  
## Comentarios  
 Al trabajar con [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] y usar P\/Invoke en una función nativa, se puede producir esta excepción si:  
  
-   La declaración en código administrado es incorrecta.  
  
-   [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] no admite lo que se intenta hacer.  
  
-   Los nombres del archivo DLL tienen un sufijo en exportación.  
  
-   En estos casos, compruebe:  
  
-   Alguna infracción a las restricciones P\/Invoke de [!INCLUDE[Compact](../extensibility/includes/compact_md.md)].  
  
-   Algún argumento que requiera memoria previamente asignada. Si éstos existen, debe pasar una referencia a una variable existente.  
  
-   Que los nombres de las funciones exportadas sean correctos. Esto se puede comprobar con DumpBin.exe.  
  
-   Que no intenta pasar demasiados argumentos.  
  
## Vea también  
 <xref:System.NotSupportedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)