---
title: "El m&#233;todo &#39;&lt;nombreDeM&#233;todo&gt;&#39; no tiene la misma firma que el delegado &#39;&lt;nombreDeDelegado&gt;&#39; | Microsoft Docs"
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
  - "bc30408"
  - "vbc30408"
helpviewer_keywords: 
  - "BC30408"
ms.assetid: 845f6686-388f-4253-b635-146e517015a1
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El m&#233;todo &#39;&lt;nombreDeM&#233;todo&gt;&#39; no tiene la misma firma que el delegado &#39;&lt;nombreDeDelegado&gt;&#39;
Existe un error de coincidencia entre las firmas del método y el delegado que está intentando usar. La instrucción `Delegate` define los tipos de parámetro y los tipos de valores devueltos de una clase de delegado. Cualquier procedimiento con parámetros, tipos y tipos devueltos coincidentes pueden usarse para crear una instancia de este tipo de delegado. Cada clase delegada define un constructor que se pasa la especificación de un método de objeto.  
  
 **Identificador de error:** BC30408  
  
### Para corregir este error  
  
-   Compruebe las firmas para encontrar el error de coincidencia y corríjalo.  
  
## Vea también  
 [Delegate \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/delegate-statement)