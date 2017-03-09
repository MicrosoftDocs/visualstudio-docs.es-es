---
title: "Error del compilador CS0434 | Microsoft Docs"
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
  - "CS0434"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0434"
ms.assetid: 8f8871fc-a4bb-4a9e-ba19-999f4943001e
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0434
El espacio de nombres NombreEspacioNombres1 de NombreEspacioNombres2 entra en conflicto con el tipo NombreTipo1 en NombreEspaciodeNombres3.  
  
 Este error se produce cuando un tipo importado y un espacio de nombres anidado importado tienen el mismo nombre completo. Cuando se hace referencia a ese nombre, el compilador no puede distinguir entre los dos. Si puede cambiar el código fuente importado, puede resolver el error cambiando el nombre del tipo o el espacio de nombres para que ambos sean únicos en el ensamblado.  
  
 El código siguiente genera el error CS0434:  
  
## Ejemplo  
 Este código crea la primera copia del tipo con el nombre completo idéntico.  
  
```  
// CS0434_1.cs // compile with: /t:library namespace TypeBindConflicts { namespace NsImpAggPubImp { public class X { } } }  
```  
  
## Ejemplo  
 Este código crea la segunda copia del tipo con el nombre completo idéntico.  
  
```  
// CS0434_2.cs // compile with: /t:library namespace TypeBindConflicts { // Conflicts with another import (import2.cs). public class NsImpAggPubImp { } // Try this instead: // public class UniqueClassName { } }  
```  
  
## Ejemplo  
 Este código hace referencia al tipo con el nombre completo idéntico.  
  
```  
// CS0434.cs // compile with: /r:cs0434_1.dll /r:cs0434_2.dll using TypeBindConflicts; public class Test { public TypeBindConflicts.NsImpAggPubImp.X n2 = null; // CS0434 }  
```