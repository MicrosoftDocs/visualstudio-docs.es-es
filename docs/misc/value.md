---
title: "__value | Microsoft Docs"
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
  - "__value_cpp"
  - "__value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__value (palabra clave)"
  - "tipos de valor, declarar"
  - "__value (palabra clave), sintaxis"
ms.assetid: b14b64f7-5db6-4e92-a144-fcbf67572b49
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __value
> [!NOTE]
>  Este tema solo es aplicable a la versión 1 de Extensiones administradas para C\+\+. Esta sintaxis solo se debe utilizar para mantener el código de la versión 1. Consulte [Clases y structs](/visual-cpp/windows/classes-and-structs-cpp-component-extensions) para obtener información sobre el uso de la funcionalidad equivalente en la nueva sintaxis.  
  
 Declara que una clase es de tipo \_\_value.  
  
## Sintaxis  
  
```  
  
__value  
 class-specifier  
__value  
 struct-specifier  
__nogc  
array-specifier  
__nogc  
pointer-specifier  
  
```  
  
## Comentarios  
 Un tipo `__value` difiere de los tipos `__gc` en que las variables de tipo `__value` contienen directamente los datos, mientras que las variables administradas apuntan a los datos, que se almacenan en el montón de Common Language Runtime.  
  
 Las condiciones siguientes se aplican a los tipos `__value`:  
  
-   La palabra clave `__value` no se puede aplicar a una interfaz.  
  
-   Un tipo `__value` puede heredar de cualquier número de interfaces y no puede heredar de otros tipos o tipos `__value`.  
  
-   Un tipo `__value` está sellado por definición. Para obtener más información, vea [\_\_sealed](../misc/sealed.md).  
  
-   Es válido usar un tipo `__value` en cualquier lugar donde se permita un tipo administrado.  
  
> [!NOTE]
>  La palabra clave `__value` no se permite cuando se usa con la palabra clave `__abstract`.  
  
 Un tipo `__value` puede conectarse explícitamente a un puntero **System::Object**. Esto se conoce como conversión boxing.  
  
 Las directrices siguientes se aplican a la inserción de un tipo de valor dentro de un tipo `__nogc`:  
  
-   El tipo de valor debe tener **LayoutSequential** o **LayoutExplicit**.  
  
-   El tipo de valor no puede tener miembros de puntero gc.  
  
-   El tipo de valor no puede tener miembros de datos privados.  
  
 En Extensiones administradas de C\+\+, los equivalentes de una clase de C\# y un struct de C\# son los siguientes:  
  
|Extensiones administradas de C\+\+|C\#|Para obtener más información|  
|----------------------------------------|---------|----------------------------------|  
|\_\_gc struct<br /><br /> O bien<br /><br /> \_\_gc class|clase|Palabra clave [class](/dotnet/csharp/language-reference/keywords/class)|  
|\_\_value struct<br /><br /> O bien<br /><br /> \_\_value class|struct|Palabra clave [struct](/dotnet/csharp/language-reference/keywords/struct)|  
  
## Ejemplo  
 En el ejemplo siguiente, se declara un tipo `__value`\(`V`\) y, a continuación, se manipulan dos instancias del tipo `__value`:  
  
```  
// keyword__value.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__value struct V {   
   int m_i;  
};  
  
int main() {  
   V v1, v2;  
   v1.m_i = 5;  
   v2 = v1;   // copies all fields of v1 to v2  
   v2.m_i = 6;   // does not affect v1.m_I  
}  
```