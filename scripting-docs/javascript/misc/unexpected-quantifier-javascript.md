---
title: "No se esperaba un cuantificador (JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5018"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# No se esperaba un cuantificador (JavaScript)
Al crear el patrón de búsqueda de expresión regular, has creado un elemento pattern con un factor de repetición no válido.  Por ejemplo, el patrón  
  
```  
/^+/  
```  
  
 no es válido porque el elemento ^ \(principio de la entrada\) no puede tener un factor de repetición.  En la tabla siguiente se muestran los elementos que no pueden tener factores de repetición.  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|^|Principio de la entrada|  
|$|Fin de la entrada|  
|\\b|Límite de palabra|  
|\\B|Límite que no es una palabra|  
|\*|Cero o más repeticiones|  
|\+|Una o más repeticiones|  
|?|Cero o una repetición|  
|{n}|n repeticiones|  
|{n,}|n o más repeticiones|  
|{n,m}|De n a m repeticiones, ambas incluidas|  
  
### Para corregir este error  
  
-   Asegúrate de que elemento del patrón de búsqueda solo contiene factores de repetición válidos.  
  
## Vea también  
 [Regular Expression \(Objeto\)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/es-es/ab0766e1-7037-45ed-aa23-706f58358c0e)