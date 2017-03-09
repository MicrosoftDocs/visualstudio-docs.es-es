---
title: "Direcci&#243;n de funciones sobrecargadas | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "funciones de sobrecarga de direcciones [C++]"
  - "devolver sobrecargadas de direcciones [C++]"
  - "función de sobrecarga, dirección de función"
  - "Este puntero, las funciones sobrecargadas"
ms.assetid: e7913e65-a295-445d-b2b0-1e60f8dfbc54
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Direcci&#243;n de funciones sobrecargadas
El uso de un nombre de función sin argumentos devuelve la dirección de esa función. Por ejemplo:  
  
```  
int Func( int i, int j );  
int Func( long l );  
  
...  
  
int (*pFunc) ( int, int ) = Func;  
```  
  
 En el ejemplo anterior, se selecciona la primera versión de `Func` y su dirección se copia en `pFunc`.  
  
 El compilador determina qué versión de la función seleccionar buscando una función con una lista de argumentos que coincida exactamente con la del destino. Los argumentos de las declaraciones de funciones sobrecargadas se hacen coincidir con una de las siguientes opciones:  
  
-   Un objeto que se esté inicializando \(como se muestra en el ejemplo anterior\)  
  
-   El lado izquierdo de una instrucción de asignación  
  
-   Un argumento formal para una función  
  
-   Un argumento formal para un operador definido por el usuario  
  
-   Un tipo de valor devuelto de función  
  
 Si no se encuentra una coincidencia exacta, la expresión que acepta la dirección de la función es ambigua y se genera un error.  
  
 Tenga en cuenta que aunque en el ejemplo anterior se usó una función que no es miembro, `Func`, al tomar la dirección de funciones miembro sobrecargadas se aplican las mismas reglas.  
  
## Vea también  
 [Sobrecargar \(C\+\+\)](../misc/overloading-cpp.md)