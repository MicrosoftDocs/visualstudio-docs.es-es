---
title: "__box | Microsoft Docs"
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
  - "__box"
  - "__box_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__box (palabra clave)"
  - "boxing"
  - "unboxing"
  - "conversión boxing, palabra clave __box"
ms.assetid: 935b4a4d-fc45-484c-87c6-d95cfc67cc9d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __box
> [!NOTE]
>  Este tema solo es aplicable a la versión 1 de Extensiones administradas para C\+\+. Esta sintaxis solo se debe utilizar para mantener el código de la versión 1. Consulte [Conversión boxing](/visual-cpp/windows/boxing-cpp-component-extensions) para obtener información sobre el uso de la funcionalidad equivalente en la nueva sintaxis.  
  
 Crea una copia administrada de un objeto de la clase \_\_value.  
  
## Sintaxis  
  
```  
  
__box(  
value-class identifier  
)  
  
```  
  
## Comentarios  
 La palabra clave `__box` se utiliza para crear un objeto administrado \(derivado de **System::ValueType**\) a partir de un objeto existente de la clase \_\_value. Cuando la palabra clave `__box` se aplica a una clase \_\_value:  
  
-   Un objeto administrado se asignad en el montón de Common Language Runtime.  
  
-   El valor actual del objeto de la clase \_\_value se copia bit a bit en el objeto administrado.  
  
-   Se devuelve la dirección del nuevo objeto administrado.  
  
 Este proceso se denomina conexión boxing. Esto permite que cualquier objeto de la clase \_\_value se utilice en las rutinas genéricas que funcionan para cualquier objeto administrado porque el objeto administrado hereda indirectamente de **System::Object** \(ya que **System::ValueType** hereda de **System::Object**\).  
  
> [!NOTE]
>  El objeto al que se ha aplicado la conversión que se acaba de crear es una copia del objeto de clase \_\_value. Por tanto, las modificaciones realizadas al valor del objeto al que se ha aplicado la conversión boxing no afectan al contenido del objeto de la clase \_\_value.  
  
## Ejemplo  
 A continuación se muestra un ejemplo de lo que realiza una conversión boxing y una conversión unboxing:  
  
```  
// keyword__box.cpp  
// compile with: /clr:oldSyntax  
#using < mscorlib.dll >  
using namespace System;  
  
int main() {  
  Int32 i = 1;  
  System::Object* obj = __box(i);  
  Int32 j = *dynamic_cast<__box Int32*>(obj);  
}  
```  
  
 En el ejemplo siguiente, un tipo de valor no administrado \(`V`\) es objeto de una conversión boxing y se como parámetro administrado a la función `Positive`.  
  
```  
// keyword__box2.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__value struct V {  
   int i;  
};  
void Positive(Object*) {}   // expects a managed class  
  
int main() {  
   V v={10};   // allocate and initialize  
   Console::WriteLine(v.i);  
  
   // copy to the common language runtime heap  
   __box V* pBoxedV = __box(v);  
   Positive(pBoxedV);   // treat as a managed class  
  
   pBoxedV->i = 20;   // update the boxed version  
   Console::WriteLine(pBoxedV->i);  
}  
```  
  
 **10 20**