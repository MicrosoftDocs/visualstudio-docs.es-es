---
title: "El m&#233;todo &#39;&lt;methodname&gt;&#39; tiene una petici&#243;n de v&#237;nculo, pero reemplaza o implementa los siguientes m&#233;todos que no tienen petici&#243;n de v&#237;nculo. Puede existir una vulnerabilidad de seguridad: | Microsoft Docs"
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
  - "bc42200"
  - "vbc42200"
helpviewer_keywords: 
  - "BC42200"
ms.assetid: c79d672e-638c-4d87-9b93-edf12ce84a52
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El m&#233;todo &#39;&lt;methodname&gt;&#39; tiene una petici&#243;n de v&#237;nculo, pero reemplaza o implementa los siguientes m&#233;todos que no tienen petici&#243;n de v&#237;nculo. Puede existir una vulnerabilidad de seguridad:
Se ha agregado una acción de petición de vínculo de seguridad al método. Sin embargo, el método reemplaza o implementa métodos que no tienen peticiones de vínculo. Por lo tanto, es posible llamar a los métodos reemplazados o implementados con permisos insuficientes, lo cual puede provocar un problema de seguridad.  
  
 De forma predeterminada, este mensaje es una advertencia. Para más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Id. de error:** BC42200  
  
### Para corregir este error  
  
-   Agregue peticiones de vínculo a los métodos reemplazados o implementados.  
  
## Vea también  
 [Link Demands](../Topic/Link%20Demands.md)   
 [Demand versus LinkDemand](http://msdn.microsoft.com/es-es/1ab877f2-70f4-4e0d-8116-943999dfe8f5)   
 [Optimizaciones de seguridad](http://msdn.microsoft.com/es-es/cf255069-d85d-4de3-914a-e4625215a7c0)