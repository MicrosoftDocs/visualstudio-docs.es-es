---
title: "__abstract | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__abstract_cpp"
  - "__abstract"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Resumen de clases [C++]"
  - "abstract (palabra clave)"
ms.assetid: fc6eee5e-9f07-4438-97f7-f2e124263575
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __abstract
> [!NOTE]
>  Este tema solo es aplicable a la versión 1 de Extensiones administradas para C\+\+. Esta sintaxis solo se debe utilizar para mantener el código de la versión 1. Consulte [abstractas](/visual-cpp/windows/abstract-cpp-component-extensions) para obtener información sobre el uso de la funcionalidad equivalente en la nueva sintaxis.  
  
 Declara una clase administrada de la que no se pueden crear instancias directamente.  
  
## Sintaxis  
  
```  
  
__abstract   
class-specifier  
__abstract   
struct-specifier  
  
```  
  
## Comentarios  
 La palabra clave `__abstract` declara que la clase de destino solo se puede utilizar como clase base de otra clase. Aplicar `__abstract` a una clase o estructura no implica que el resultado sea una clase \_\_gc o una estructura \_\_gc.  
  
 A diferencia de la noción de C\+\+ de una clase base [abstract](/visual-cpp/cpp/abstract-classes-cpp), una clase con la palabra clave `__abstract` puede definir sus propias funciones miembro.  
  
> [!NOTE]
>  La palabra clave `__abstract` no se permite cuando se utiliza con la palabra clave `__value` o `__sealed`, y es redundante cuando se utiliza con la palabra clave `__interface`.  
  
## Ejemplo  
 En el ejemplo siguiente, la clase `Derived` se deriva de una clase base abstracta \(`Base`\). La creación de instancias se intenta en ambos casos, pero solo `Derived` puede efectuarla.  
  
```  
// keyword__abstract.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__abstract __gc class Base {  
   int BaseFunction() {  
      return 0;  
   }  
};  
  
__gc class Derived: public Base {};  
  
int main() {  
   Base* MyBase = new Base();   // C3622 can't BAse is abstract  
   Derived* MyDerived = new Derived();  
}  
```