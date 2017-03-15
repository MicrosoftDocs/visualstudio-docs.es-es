---
title: "__gc | Microsoft Docs"
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
  - "__gc"
  - "__gc_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__gc (tipos)"
  - "clases administradas [C++]"
  - "clases administradas"
ms.assetid: 63b1e7ab-d1c8-4582-aa89-21bfddf694a9
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __gc
> [!NOTE]
>  Este tema solo es aplicable a la versión 1 de Extensiones administradas para C\+\+. Esta sintaxis solo se debe utilizar para mantener el código de la versión 1. Consulte [Clases y structs](/visual-cpp/windows/classes-and-structs-cpp-component-extensions) para obtener información sobre el uso de la funcionalidad equivalente en la nueva sintaxis.  
  
 Declara un tipo \_\_gc.  
  
## Sintaxis  
  
```  
  
__gc  
array-specifier  
__gc   
class-specifier  
__gc   
struct-specifier  
__gc  
interface-specifier  
__gc  
pointer-specifier  
__gc new  
  
```  
  
## Comentarios  
 Un tipo \_\_gc es una extensión del lenguaje C\+\+ que simplifica la programación en .NET Framework proporcionando características como interoperabilidad y recolección de elementos no utilizados.  
  
> [!NOTE]
>  Cada función miembro de una clase abstracta \_\_gc debe definirse a menos que la función miembro sea virtual pura.  
  
 En Extensiones administradas de C\+\+, los equivalentes de una clase de C\# y un struct de C\# son los siguientes:  
  
|Extensiones administradas de C\+\+|C\#|Para obtener más información|  
|----------------------------------------|---------|----------------------------------|  
|struct \_\_gc o clase \_\_gc|clase|Palabra clave [class](/dotnet/csharp/language-reference/keywords/class)|  
|struct \_\_value o clase \_\_value|struct|Palabra clave [struct](/dotnet/csharp/language-reference/keywords/struct)|  
  
## Ejemplo  
 En el ejemplo siguiente, una clase administrada \(`X`\) se declara con un miembro de datos público, que se manipula a través de un puntero administrado:  
  
```  
// keyword__gc.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc class X {  
public:  
   int i;  
   int ReturnInt() { return 5; }  
};  
  
int main() {  
   // X is a __gc class, so px is a __gc pointer  
   X* px;  
   px = new X;   // creates a managed object of type X  
   Console::WriteLine(px->i);  
  
   px->i = 4;   // modifies X::i through px  
   Console::WriteLine(px->i);  
  
   int n = px->ReturnInt();   // calls X::ReturnInt through px  
   Console::WriteLine(n);  
}  
```  
  
## Resultado  
  
```  
0  
4  
5  
```