---
title: "__typeof | Microsoft Docs"
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
  - "__typeof_cpp"
  - "__typeof"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__typeof (palabra clave)"
ms.assetid: d71b9603-35d0-4c62-b5b4-90ffc2305a55
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __typeof
**Nota** Este tema solo es aplicable a la versión 1 de Extensiones administradas para C\+\+. Esta sintaxis solo se debe utilizar para mantener el código de la versión 1. Consulte [typeid](/visual-cpp/windows/typeid-cpp-component-extensions) para obtener información sobre el uso de la funcionalidad equivalente en la nueva sintaxis.  
  
 Devuelve el **System::Type** de un tipo especificado.  
  
```  
  
__typeof(  
typename  
)  
  
```  
  
 donde:  
  
 *typename*  
 El nombre de un tipo administrado para el que desea el nombre **System::Type**. Observe que, en un programa administrado, algunos tipos nativos se usan como alias para tipos de Common Language Runtime. Por ejemplo, `int` es un alias para **System::Int32**.  
  
## Comentarios  
 El operador **\_\_typeof** permite obtener el tipo de **System::Type** de un tipo que especifique.**\_\_typeof** también se puede utilizar para devolver un valor de **System::Type** en un bloque de atributos personalizados. Vea [attribute](/visual-cpp/windows/attribute) para obtener más información sobre cómo crear sus propios atributos.  
  
## Ejemplo  
 En el ejemplo siguiente, un atributo personalizado \(`AtClass`\) se aplica a una clase \_\_gc \(`B`\). El valor del atributo personalizado se recupera entonces con **\_\_typeof**:  
  
```  
// keyword__typeof.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
public __gc class MyClass {};  
  
[attribute(All)]  
__gc class AtClass {  
public:  
   AtClass(Type*) {  
      Console::WriteLine("in Type * constructor");  
   }  
  
   AtClass(String*) {}  
   AtClass(int) {}  
};  
  
[AtClass(__typeof(MyClass))]   // Apply AtClass attribute to class B  
__gc class B {};  
  
int main() {  
   Type * mytype = __typeof(B);  
   Object * myobject __gc[] = mytype -> GetCustomAttributes(true);  
   Console::WriteLine(myobject[0]);  
}  
```  
  
## Salida  
  
```  
in Type * constructor  
AtClass  
```