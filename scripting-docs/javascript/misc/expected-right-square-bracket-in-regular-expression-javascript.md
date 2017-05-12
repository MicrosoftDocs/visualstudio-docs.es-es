---
title: "Se esperaba &#39;]&#39; en la expresi&#243;n regular (JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5019"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Se esperaba &#39;]&#39; en la expresi&#243;n regular (JavaScript)
Has intentado crear una clase de caracteres para una coincidencia de expresión regular, pero no incluía el corchete derecho.  Pueden ensamblarse combinaciones específicas de caracteres literales en clases de caracteres poniéndolas entre corchetes.  Una clase de caracteres halla una coincidencia con cualquiera de los caracteres que contiene.  Por ejemplo, \/\[abc\]\/ encuentra coincidencias con cualquiera de la letras "a", "b" o "c".  
  
### Para corregir este error  
  
-   Agrega el corchete derecho a la expresión regular.  
  
    > [!NOTE]
    >  Si quieres hallar una coincidencia de un corchete simple, precédelo de la barra diagonal inversa, "\\\[", para que [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] no lo interprete como un carácter especial.  
  
## Vea también  
 [Regular Expression \(Objeto\)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/es-es/ab0766e1-7037-45ed-aa23-706f58358c0e)