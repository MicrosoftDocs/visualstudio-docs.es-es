---
title: "Se esperaba &#39;@&#39; | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1032"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Se esperaba &#39;@&#39;
Has intentado crear una variable que se usará con instrucciones de compilación condicional mediante la instrucción `@set`, pero no has puesto una arroba "**@**" delante del nombre de variable.  
  
### Para corregir este error  
  
-   Agrega una arroba "**@**" inmediatamente antes del nombre de variable.  Por ejemplo:  
  
    ```javascript  
    @set @myvar = 1  
    ```  
  
## Vea también  
 [@set \(Instrucción\)](../../javascript/reference/at-set-statement-javascript.md)   
 [Compilación condicional](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de compilación condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)