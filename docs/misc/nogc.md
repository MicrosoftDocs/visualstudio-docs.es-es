---
title: "__nogc | Microsoft Docs"
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
  - "__nogc_cpp"
  - "__nogc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__nogc (declaraciones de tipos)"
  - "clases [C++], tipo no administrado"
  - "clases no administradas, declaración de"
  - "clases no administradas"
ms.assetid: 3e7f1b09-0fc3-4a8f-9458-a22f7a38ce45
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __nogc
> [!NOTE]
>  Este tema solo es aplicable a la versión 1 de Extensiones administradas para C\+\+. Esta sintaxis solo se debe utilizar para mantener el código de la versión 1. En la nueva sintaxis, no necesita marcar explícitamente un tipo como no administrado.  
  
 Los tipos no administrados se declaran explícitamente.  
  
## Sintaxis  
  
```  
  
__nogc   
class-specifier  
__nogc   
struct-specifier  
__nogc  
interface-specifier  
__nogc  
array-specifier  
__nogc  
pointer-specifier  
__nogc  
new  
  
```  
  
## Comentarios  
 La palabra clave `__nogc` se utiliza para especificar explícitamente que un objeto está asignado en el montón de C\+\+ estándar. Esta palabra clave es opcional. Si no especifica `__gc` ni `__nogc` delante de una declaración de clase, se utiliza `__nogc` de forma predeterminada.  
  
 Los objetos de este tipo se parecen a los objetos estándar de C\+\+ en que se asignan desde el montón de C\+\+ estándar y no están sujetos a las restricciones de un objeto administrado.  
  
 La palabra clave `__nogc` se usa también cuando un objeto de un tipo \_\_value se asigna explícitamente en el montón de C\+\+ estándar:  
  
```  
// keyword__nogc.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
__value struct V {   
   int i;  
};  
int main() {  
   V * v = __nogc new V;  
   v->i = 10;  
   delete v;  
}  
```  
  
> [!NOTE]
>  La palabra clave `__nogc` se puede aplicar también a los tipos de matriz y puntero.  
  
 Un puntero gc no puede ser un miembro de una clase `__nogc`. Vea [\_\_value](../misc/value.md) para obtener instrucciones sobre cómo incrustar un tipo de valor en una clase `__nogc`.  
  
## Ejemplo  
 En el ejemplo siguiente se declara una clase no administrada \(`X`\) y se crea y se modifica una instancia de un objeto:  
  
```  
// keyword__nogc_2.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__nogc class X {  
public:  
   int i;  
};  
  
int main() {  
   X* x;   // declares an unmanaged pointer of type X  
   x = new X();   // creates unmanaged object of type X on the C++ heap  
   Console::WriteLine(x->i);  
  
   x->i = 4;   // modifies unmanaged object  
   Console::WriteLine(x->i);  
  
   delete x;   // call C++ delete operator to clean up resource  
}  
```  
  
 **48378256 4**