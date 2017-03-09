---
title: "Covarianza de matrices | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
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
  - "matrices [C++], covarianza"
ms.assetid: 889fdde3-85fe-44d5-bf2d-d3d4aa14e746
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "mithom"
manager: "douge"
---
# Covarianza de matrices
Dado que la clase de referencia D con la clase base directa o indirecta B, una matriz de tipo D puede asignarse a una variable de matriz de tipo B.  
  
```  
// clr_array_covariance.cpp  
// compile with: /clr  
using namespace System;  
  
int main() {  
   // String derives from Object  
   array<Object^>^ oa = gcnew array<String^>(20);  
}  
```  
  
## Comentarios  
 Una asignación a un elemento de matriz debe ser compatible con la asignación con el tipo de la matriz dinámico. Una asignación a un elemento de matriz con tipo incompatible hará System:: ArrayTypeMismatchException se produzca.  
  
 Covarianza de matrices no se aplica a las matrices de tipo de clase de valor. Por ejemplo, no se puede convertir matrices de Int32 al objeto ^ matrices, incluso a través de la conversión boxing.  
  
## Ejemplo  
  
```  
// clr_array_covariance2.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct Base { int i; };  
ref struct Derived  : Base {};  
ref struct Derived2 : Base {};  
ref struct Derived3 : Derived {};  
ref struct Other { short s; };  
  
int main() {  
   // Derived* d[] = new Derived*[100];  
   array<Derived^> ^ d = gcnew array<Derived^>(100);  
  
   // ok by array covariance  
   array<Base ^> ^  b = d;  
  
   // invalid  
   // b[0] = new Other;  
  
   // error (runtime exception)  
   // b[1] = gcnew Derived2;  
  
   // error (runtime exception),  
   // must be "at least" a Derived.  
   // b[0] = gcnew Base;  
  
   b[1] = gcnew Derived;  
   b[0] = gcnew Derived3;  
}  
```  
  
## Vea también  
 [Matrices](/visual-cpp/windows/arrays-cpp-component-extensions)