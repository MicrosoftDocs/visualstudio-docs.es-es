---
title: "Advertencia de conformidad con CLS CLS01303 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS01303"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01303"
ms.assetid: a8aa0cda-a2dd-41da-bcc2-53221207ea70
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Advertencia de conformidad con CLS CLS01303
Un literal conforme a CLS debe tener un valor especificado en los metadatos de inicialización de campos que sea exactamente igual que el literal \(o el tipo subyacente, si el literal es una enumeración\).  
  
 El valor de un estático literal se especifica mediante el uso de metadatos de inicialización de campos. Un literal conforme a CLS debe tener un valor especificado en los metadatos de inicialización de campos que sea exactamente igual que el literal \(o el tipo subyacente, si el literal es una enumeración\).  
  
 Asegúrese de que el literal de campo tiene exactamente el mismo tipo que el literal \(o tipo subyacente, si el literal es una enumeración\).  
  
 Para más información sobre la comprobación de conformidad con CLS, vea [Ensamblados compatibles con CLS](http://msdn.microsoft.com/es-es/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 La siguiente declaración \(mediante el lenguaje ensamblador MSIL\) muestra lo que podría provocar CLS01303:  
  
```  
.field public static literal char Field2 = int32(0x00000002)  
```  
  
 Si hace que el tipo del inicializador sea igual que el tipo de literal, puede resolver esta advertencia:  
  
```  
.field public static literal char Field2 = char(0x00000002)  
```