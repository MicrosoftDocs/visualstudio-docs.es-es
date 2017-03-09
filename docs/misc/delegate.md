---
title: "__delegate | Microsoft Docs"
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
  - "__delegate_cpp"
  - "__delegate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "delegados, _delegate (palabra clave)"
  - "punteros a función, administrados"
  - "__delegate (palabra clave)"
ms.assetid: a41d2211-b79b-4509-a4c2-cc91f3d4fc9d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __delegate
**Nota** Este tema solo es aplicable a la versión 1 de Extensiones administradas para C\+\+. Esta sintaxis solo se debe utilizar para mantener el código de la versión 1. Consulte [delegado](/visual-cpp/windows/delegate-cpp-component-extensions) para obtener información sobre el uso de la funcionalidad equivalente en la nueva sintaxis.  
  
 Define un tipo de referencia que se puede utilizar para encapsular un método con una signatura específica.  
  
## Sintaxis  
  
```  
  
__delegate   
function-declarator  
  
```  
  
## Comentarios  
 Un delegado es más o menos equivalente a un puntero de función de C\+\+ salvo por la diferencia siguiente:  
  
-   Un delegado solo se puede enlazar a uno o más métodos dentro de una clase \_\_gc.  
  
 Cuando el compilador encuentra la palabra clave `__delegate`, se genera una definición de una clase \_\_gc. Esta clase \_\_gc tiene las características siguientes:  
  
-   Hereda de **System::MulticastDelegate**.  
  
-   Tiene un constructor que toma dos argumentos: un puntero a una clase \_\_gc o **NULL** \(en el caso del enlace a un método estático\) y un método completo del tipo especificado.  
  
-   Tiene un método denominado `Invoke`, cuya signatura coincide con la signatura declarada del delegado.  
  
## Ejemplo  
 En el ejemplo siguiente, se declaran una clase \_\_gc \(`MyCalendar`\) y un delegado \(`GetDayOfWeek`\). El delegado se enlaza después a los diferentes métodos de `MyCalendar`, invocando cada uno a su vez:  
  
```  
// keyword__delegate.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__delegate int GetDayOfWeek();  
__gc class MyCalendar {  
public:  
   MyCalendar() : m_nDayOfWeek(4) {}  
   int MyGetDayOfWeek() {   
      Console::WriteLine("handler"); return m_nDayOfWeek;   
   }  
   static int MyStaticGetDayOfWeek() {   
      Console::WriteLine("static handler");   
      return 6;  
   }  
private:  
   int m_nDayOfWeek;  
};  
  
int main () {  
   GetDayOfWeek * pGetDayOfWeek;  // declare delegate type  
   int nDayOfWeek;  
  
   // bind delegate to static method  
   pGetDayOfWeek = new GetDayOfWeek(0, &MyCalendar::MyStaticGetDayOfWeek);  
   nDayOfWeek = pGetDayOfWeek->Invoke();  
   Console::WriteLine(nDayOfWeek);  
  
   // bind delegate to instance method  
   MyCalendar * pcal = new MyCalendar();  
   pGetDayOfWeek = static_cast<GetDayOfWeek*>(Delegate::Combine(pGetDayOfWeek,  
      new GetDayOfWeek(pcal, &MyCalendar::MyGetDayOfWeek)));  
   nDayOfWeek = pGetDayOfWeek->Invoke();  
   Console::WriteLine(nDayOfWeek);  
  
   // delegate now bound to two methods; remove instance method  
   pGetDayOfWeek = static_cast<GetDayOfWeek*>(Delegate::Remove(pGetDayOfWeek,  
      new GetDayOfWeek(pcal, &MyCalendar::MyGetDayOfWeek)));  
}  
```  
  
## Resultados del ejemplo  
  
```  
static handler  
6  
static handler  
handler  
4  
```