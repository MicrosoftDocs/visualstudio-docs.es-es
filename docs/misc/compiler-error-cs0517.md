---
title: "Error del compilador CS0517 | Microsoft Docs"
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
  - "CS0517"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0517"
ms.assetid: 33732ade-6ab9-4582-bea4-125d63388779
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0517
'class' no tiene clase base y no puede llamar a un constructor base  
  
 El error CS0517 solo puede producirse cuando Common Language Runtime de .NET Framework compila el código fuente de la clase object, que es la única clase que no tiene clase base.