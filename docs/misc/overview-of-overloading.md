---
title: "Informaci&#243;n general de sobrecarga | Microsoft Docs"
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
  - "sobrecarga, acerca de la función sobrecarga de funciones"
  - "sobrecarga de operadores, acerca de la sobrecarga de operadores"
ms.assetid: cd012dd4-607c-4f8e-bd2e-2bd506ac81ea
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Informaci&#243;n general de sobrecarga
Con el lenguaje C\+\+, puede sobrecargar funciones y operadores. Sobrecarga es la práctica de proporcionar más de una definición para un nombre de función dado en el mismo ámbito. La elección de la versión adecuada de la función o el operador, sobre la base de los argumentos con los que se realiza la llamada, se deja al compilador. Por ejemplo, la función max se considera una función sobrecargada. Se puede usar en código como el siguiente:  
  
```  
// overview_overload.cpp  
double max( double d1, double d2 )  
{  
   return ( d1 > d2 ) ? d1 : d2;  
}  
  
int max( int i1, int i2 )  
{  
   return ( i1 > i2 ) ? i1 : i2;  
}  
int main()  
{  
   int    i = max( 12, 8 );  
   double d = max( 32.9, 17.4 );  
}  
```  
  
 En la primera llamada de función, donde se solicita el valor máximo de dos variables de tipo `int`, se llama a la función `max( int, int )`. Sin embargo, en la segunda llamada de función, los argumentos son de tipo `double`, así que se llama a la función `max( double, double )`.  
  
## Vea también  
 [Sobrecargar \(C\+\+\)](../misc/overloading-cpp.md)