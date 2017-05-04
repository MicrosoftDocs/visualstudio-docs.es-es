---
title: "Se esperaba &#39;)&#39; en la expresi&#243;n regular (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5020"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Se esperaba &#39;)&#39; en la expresi&#243;n regular (JavaScript)
Has intentado crear una captura, una aserción o un grupo en una expresión regular, pero no has incluido el paréntesis de cierre.  Los paréntesis se usan para varios fines en las expresiones regulares.  Principalmente, se utilizan para capturar subexpresiones, especificar aserciones o agrupar patrones entre sí, para que los elementos se puedan tratar como una sola unidad por \*, \+, ?, etc.  
  
### Para corregir este error  
  
-   Agrega el paréntesis de cierre derecho.  
  
    > [!NOTE]
    >  Si quieres hallar una coincidencia de un paréntesis simple, precédelo de la barra diagonal inversa, "\\\(", para que [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] no lo interprete como un carácter especial.  
  
## Vea también  
 [Regular Expression \(Objeto\)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/es-es/ab0766e1-7037-45ed-aa23-706f58358c0e)