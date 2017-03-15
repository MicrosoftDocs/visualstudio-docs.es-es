---
title: "__sealed | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__sealed_cpp"
  - "__sealed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sealed (palabra clave) [C++]"
  - "__sealed (palabra clave)"
ms.assetid: 9e5f778a-4ad8-468d-9c44-783e576fb49b
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __sealed
> [!NOTE]
>  Este tema solo es aplicable a la versión 1 de Extensiones administradas para C\+\+. Esta sintaxis solo se debe utilizar para mantener el código de la versión 1. Consulte [sellado](/visual-cpp/windows/sealed-cpp-component-extensions) para obtener información sobre el uso de la funcionalidad equivalente en la nueva sintaxis.  
  
 Evita que un método se invalide o una clase sea una clase base.  
  
## Sintaxis  
  
```  
  
__sealed   
class-specifier  
__sealed   
struct-specifier  
__sealed   
function-declarator  
  
```  
  
## Comentarios  
 La palabra clave `__sealed` especifica que un método de clase no puede invalidarse o que una clase no puede ser una clase base.  
  
 Cuando use la palabra clave `__sealed`, tenga en cuenta los puntos siguientes:  
  
-   Un método virtual `__sealed` no puede invalidarse.  
  
-   Si un método de miembro no virtual se marca con `__sealed`, la calificación de `__sealed` se omite.  
  
-   Un método `__sealed` no puede ser puro.  
  
-   El **\_\_sealed** no se permite la palabra clave cuando se usa con el [\_\_interface](/visual-cpp/cpp/interface) \(palabra clave\).  
  
 Cuando una clase \(o struct\) se marca con `__sealed`, no se puede usar como clase base. Por ejemplo:  
  
```  
__sealed __gc class A {  
   // ...  
};  
// error: cannot derive from a sealed class  
__gc class B : public A { /* ...*/ };  
```  
  
> [!NOTE]
>  La palabra clave `__sealed` no se permite cuando se usa con la palabra clave `__abstract`.  
  
## Ejemplo  
 En el ejemplo siguiente, se declara un método virtual sellado \(`f`\). La función se invalida en `main()`, produciendo un error del compilador:  
  
```  
// keyword__sealed.cpp  
// compile with: /clr:oldSyntax  
  
#using <mscorlib.dll>  
extern "C" int printf_s(const char*, ...);  
  
__gc struct I  
{  
    __sealed virtual void f()  
    {   
        printf_s("I::f()\n");   
    }  
    virtual void g()  
    {  
        printf_s("I::g()\n");  
    }  
};  
  
__gc struct A : I   
{  
    void f() // C3248 sealed function  
    {   
        printf_s("A::f()\n");   
    }     
    void g()  
    {  
        printf_s("A::g()\n");  
    }  
};  
  
int main()  
{  
    A* pA = new A;  
  
    pA->f();  
    pA->g();  
}  
```