---
title: "Demasiados clientes de aplicaci&#243;n DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrID47"
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Demasiados clientes de aplicaci&#243;n DLL
La biblioteca de vínculos dinámicos \(DLL\) de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] solo puede admitir el acceso de un número limitado de aplicaciones host. La aplicación y otras aplicaciones que son hosts de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] \(es posible que su aplicación acceda a algunos de estos\) están intentando acceder a la DLL de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] al mismo tiempo.  
  
### Para corregir este error  
  
-   Reduzca el número de aplicaciones abiertas que acceden a [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
## Vea también  
 [Tipos de error](/dotnet/visual-basic/programming-guide/language-features/error-types)