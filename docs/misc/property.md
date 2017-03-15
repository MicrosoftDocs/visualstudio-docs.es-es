---
title: "__property | Microsoft Docs"
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
  - "__property_cpp"
  - "__property"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__property (palabra clave)"
  - "clases administradas"
  - "clases administradas de propiedades [C++]"
ms.assetid: 235e3574-6882-4c52-8301-270277b9216d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __property
> [!NOTE]
>  Este tema solo es aplicable a la versión 1 de Extensiones administradas para C\+\+. Esta sintaxis solo se debe utilizar para mantener el código de la versión 1. Consulte [propiedad](/visual-cpp/windows/property-cpp-component-extensions) para obtener información sobre el uso de la funcionalidad equivalente en la nueva sintaxis.  
  
 Declara una propiedad escalar o indizada para la clase administrada.  
  
## Sintaxis  
  
```  
  
__property  
function-declarator  
  
```  
  
## Comentarios  
 La palabra clave `__property` presenta la declaración de una propiedad y puede aparecer en una clase, interfaz o tipo de valor. Una propiedad puede tener una función captadora \(de solo lectura\), una función establecedor \(de solo escritura\) o ambas \(de lectura y escritura\).  
  
> [!NOTE]
>  Un nombre de propiedad no puede coincidir con el nombre de la clase administrada que lo contiene. El tipo de valor devuelto de la función captadora debe coincidir con el tipo del último parámetro de una función establecedora correspondiente.  
  
## Ejemplo  
 En el ejemplo siguiente, se agrega una propiedad escalar \(`Size`\) a la declaración `MyClass`. A continuación, la propiedad se establece y recupera implícitamente mediante las funciones `get_Size` y `set_Size`:  
  
```  
// keyword__property.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc class MyClass {  
public:  
   MyClass() : m_size(0) {}  
   __property int get_Size() { return m_size; }  
   __property void set_Size(int value) { m_size = value; }  
   // compiler generates pseudo data member called Size  
protected:  
   int m_size;  
};  
  
int main() {  
   MyClass* class1 = new MyClass;  
   int curValue;  
  
   Console::WriteLine(class1->Size);  
  
   class1->Size = 4;   // calls the set_Size function with value==4  
   Console::WriteLine(class1->Size);  
  
   curValue = class1->Size;   // calls the get_Size function  
   Console::WriteLine(curValue);  
}  
```  
  
## Salida  
  
```  
0  
4  
4  
```