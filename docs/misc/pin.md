---
title: "__pin | Microsoft Docs"
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
  - "__pin"
  - "__pin_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fijar punteros, la palabra clave __pin"
  - "tipos no administrados"
  - "__pin (palabra clave)"
ms.assetid: 8b55c792-5654-4669-bb0e-a52100f4cabe
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __pin
**Nota** Este tema solo es aplicable a la versión 1 de Extensiones administradas para C\+\+. Esta sintaxis solo se debe utilizar para mantener el código de la versión 1. Consulte [pin\_ptr \(C\+\+\/CLI\)](/visual-cpp/windows/pin-ptr-cpp-cli) para obtener información sobre el uso de la funcionalidad equivalente en la nueva sintaxis.  
  
 Evita que Common Language Runtime mueva un objeto o un objeto incrustado de una clase administrada durante la recolección de elementos no utilizados.  
  
## Sintaxis  
  
```  
  
__pin   
identifier  
  
```  
  
## Comentarios  
 La palabra clave `__pin` declara un puntero a un objeto o un objeto incrustado de una clase administrada y evita que Common Language Runtime mueva el objeto durante la recolección de elementos no utilizados. Esto es útil cuando se pasa la dirección de una clase administrada a una función no administrada porque la dirección no cambiará de forma inesperada durante la resolución de la llamada de función no administrada.  
  
 Un puntero anclado sigue siendo válido en su ámbito léxico. En cuanto el puntero anclado salga del ámbito, el objeto no se considerará anclado \(a menos que, por supuesto, existan otros punteros anclados que señalen al objeto o al interior del mismo\).  
  
 MSIL no tiene el concepto de "ámbito de bloque"; todas las variables locales residen en el ámbito de la función. Permitir que el sistema conozca el anclaje ya no está en vigor; el compilador genera código que asigna NULL al puntero anclado. Esto también lo puede hacer el usuario personalmente si necesita desanclar el objeto sin abandonar el bloque.  
  
 No debe convertir el puntero anclado a un puntero no administrado y seguir utilizando este puntero no administrado después de que el objeto deje de estar anclado \(después de que el puntero anclado salga del ámbito\). A diferencia de los punteros gc, los punteros anclados se pueden convertir a nogc, punteros no administrados. Sin embargo, es responsabilidad del usuario mantener el anclaje mientras el puntero no administrado está en uso.  
  
 No se debe usar un puntero anclado para obtener la dirección de una variable y utilizar esa dirección después de que el puntero anclado salga del ámbito.  
  
```  
// keyword_pin_scope_bad.cpp  
// compile with: /clr:oldSyntax /LD  
#using <mscorlib.dll>  
__gc struct X {  
   int x;  
};  
  
int* Get_x( X* pX ) {  
   int __pin* px = &pX -> x;  
   return px;   // BE CAREFUL px goes of scope,   
                // so object pointed by it is no longer pinned,  
                // making the return value unsafe.  
}  
```  
  
 En el ejemplo siguiente se muestra el comportamiento correcto:  
  
```  
// keyword_pin_scope_good.cpp  
// compile with: /clr:oldSyntax /LD  
#using <mscorlib.dll>  
__gc struct X {  
   int x;  
};  
  
int Get_x( X* pX ) {  
   int __pin* px = &pX -> x;  
   return *px;   // OK, value obtained from px before px out of scope  
}  
```  
  
## Ejemplo  
 En el ejemplo siguiente, el objeto señalado por `pG` está anclado hasta que sale del ámbito:  
  
```  
// keyword__pin.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
#include <iostream>  
  
__gc class G {   
public:   
   int i;   
   G() {i = 0;};  
};  
  
class H {  
public:  
   // unmanaged function  
   void incr(int * i) {  
      (*i)++;   
      std::cout << *i << std::endl;  
   };  
};  
  
int main() {  
   G __pin * pG = new G;  // pG is a pinning pointer  
   H * h = new H;  
   // pointer to managed data passed as actual parameter of unmanaged   
   // function call  
   h->incr(& pG -> i);   
}  
```  
  
## Salida  
  
```  
1  
```