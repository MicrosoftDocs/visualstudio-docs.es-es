---
title: "Error del compilador CS0537 | Microsoft Docs"
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
  - "CS0537"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0537"
ms.assetid: 6c832a5f-47dc-4f60-aed8-69ac328af44b
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0537
La clase System.Object no puede tener una clase base o implementar una interfaz  
  
 El error CS0537 se produce al volver a generar las bibliotecas de clases <xref:System> y donde <xref:System.Object> se deriva de otra clase. Es muy poco probable que encuentre este error. Si se encuentra con este error, no debe derivarse de <xref:System.Object> desde una clase o interfaz: es la raíz de la jerarquía de clases de .NET Framework completa y, por lo tanto, no se deriva de cualquier otra cosa.