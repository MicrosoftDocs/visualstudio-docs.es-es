---
title: "__try_cast | Microsoft Docs"
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
  - "__try_cast"
  - "__try_cast_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__try_cast (palabra clave)"
  - "errores de conversión"
  - "excepciones, conversiones incorrectas"
  - "iniciar excepciones, conversiones incorrectas"
ms.assetid: e9e5da3a-f5b9-4915-b30a-a432e8574d03
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __try_cast
**Nota** Este tema solo es aplicable a la versión 1 de Extensiones administradas para C\+\+. Esta sintaxis solo se debe utilizar para mantener el código de la versión 1. Consulte [safe\_cast](/visual-cpp/windows/safe-cast-cpp-component-extensions) para obtener información sobre el uso de la funcionalidad equivalente en la nueva sintaxis.  
  
 Realiza la conversión especificada o inicia una excepción si la conversión produce un error.  
  
## Sintaxis  
  
```  
  
__try_cast <  
 type-id  
 >  
(  
expression   
)  
  
```  
  
## Comentarios  
 La palabra clave de `__try_cast` \(similar en comportamiento a [dynamic\_cast](/visual-cpp/cpp/dynamic-cast-operator)\) proporciona compatibilidad para iniciar automáticamente una excepción \(de tipo **System::InvalidCastException**\) siempre que se produzca un error en la operación de conversión especificada.  
  
 La palabra clave `__try_cast` se puede usar durante la fase de pruebas de la aplicación y alerta automáticamente de posibles errores de conversión.  
  
 Al trasladar extensiones administradas para C\+\+, reemplace `__try_cast` llama a [safe\_cast](/visual-cpp/windows/safe-cast-cpp-component-extensions).  
  
 `__try_cast` no funciona en conversiones de puntero a tipos de valor \([\_\_value](../misc/value.md)\), ya que no es posible comprobar los tipos en tiempo de ejecución.  
  
## Ejemplo  
 En el ejemplo siguiente, se realiza un intento de convertir un puntero \(de tipo `Derived`\) a otro puntero \(de tipo `MoreDerived`\). Si la conversión produce un error, el bloque catch lo detecta e informa de ello:  
  
```  
// keyword__try_cast.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc struct Base {};   
__gc struct Derived : Base {};  
__gc struct MoreDerived : Derived {};  
  
int main() {  
   Base*bp = new Derived;  
   try {  
       MoreDerived* mdp = __try_cast<MoreDerived*>(bp);  
   }  
   catch(System::InvalidCastException*) {  
       Console::WriteLine("Could not cast 'bp' to MoreDerived*");  
   }  
}  
```  
  
## Salida  
  
```  
Could not cast 'bp' to MoreDerived*  
```