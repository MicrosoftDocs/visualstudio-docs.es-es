---
title: "Error del compilador CS0844 | Microsoft Docs"
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
  - "CS0844"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0844"
ms.assetid: ccf74e01-292a-42d0-897c-8add7aee2118
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0844
No se puede usar la variable 'name' antes de declararla. La declaración de la variable local oculta el campo 'name'.  
  
 Un identificador solo puede tener un significado en un bloque determinado. Las variables locales que tengan el mismo nombre que los campos de clase pueden ocultar el campo si introducen un segundo significado para el identificador. Por lo tanto, el compilador genera un error cuando se hace referencia a un campo de clase en un método y, después, se declara una variable local con el mismo nombre.  
  
### Para corregir este error  
  
-   Use `this.num` para hacer referencia al campo de clase.  
  
-   Asigne a la variable local un nombre diferente al del campo de clase.  
  
## Ejemplo  
 El código siguiente genera el error CS0844:  
  
```  
class Test { int num; public void TestMethod() { num = 5; // CS0844 int num = 6;        } public static int Main() { return 1; } }  
```