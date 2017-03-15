---
title: "Cambios importantes en Visual C++ 2015 Update 2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5545ce3f-d8da-4007-88b7-8dba7dcd4d10
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "mithom"
---
# Cambios importantes en Visual C++ 2015 Update 2
Al actualizar a Visual C\+\+ 2015 Update 2 CTP, se pueden producir errores de compilación o en tiempo de ejecución en código previamente compilado que se ejecutaba correctamente. Los cambios en el comportamiento del compilador o en tiempo de ejecución que producen tales problemas se conocen como *cambios importantes* y normalmente son necesarios debido a las modificaciones en el estándar del lenguaje C\+\+, las firmas de función o la disposición de los objetos en la memoria.  
  
 En el resto de este artículo se describen cambios importantes concretos en Visual C\+\+ 2015 Update 2 CTP. En este artículo, los términos "nuevo comportamiento" o "ahora" hacen referencia a esa versión. Los términos "comportamiento anterior" y "antes" hacen referencia a Visual C\+\+ 2015 Update 1 y versiones anteriores. Para obtener información sobre cambios importantes que se produjeron entre la versión inicial de Visual C\+\+ 2015 y Visual C\+\+ 2015 Update 1, consulte [Cambios importantes en Update 1](../misc/breaking-changes-in-visual-cpp-2015-update-1.md). Para obtener información sobre cambios importantes que se produjeron entre Visual C\+\+ 2013 y Visual C\+\+ 2015, vea [Cambios importantes en Visual C\+\+ 2015](/visual-cpp/porting/visual-cpp-change-history-2003-20151).  
  
-   [Cambios importantes en el compilador](#BK_compiler)  
  
##  <a name="BK_compiler"></a> Compilador de Visual C\+\+  
  
-   **Puede que se generen errores y advertencias adicionales como resultado de la compatibilidad parcial con la expresión SFINAE.**  
  
     Las versiones anteriores del compilador no analizaban determinados tipos de expresiones dentro de especificadores `decltype` debido a la falta de compatibilidad con la expresión SFINAE. Este comportamiento anterior era incorrecta y no se ajusta al estándar de C\+\+. Ahora, el compilador analiza estas expresiones y tiene compatibilidad parcial para la expresión SFINAE gracias a las mejoras de cumplimiento continuas. Como resultado, ahora, el compilador genera advertencias y errores detectados en las expresiones que las versiones anteriores del compilador no analizaban.  
  
     Cuando este comportamiento nuevo analiza una expresión `decltype` que incluye un tipo que aún no se ha declarado, el compilador genera el error de compilador C2039 como resultado.  
  
 **error C2039: *'type'*: no es un miembro de *'\`global namespace''***     Ejemplo 1: uso de un tipo no declarado \(antes\)  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
     Ejemplo 1 \(después\)  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
     Cuando este comportamiento nuevo analiza una expresión `decltype` en que falta el uso necesario de la palabra clave `typename` para especificar que un nombre dependiente es un tipo, el compilador emite la advertencia de compilador C4346, junto con el error de compilador C2923.  
  
 **advertencia C4346: *'S2\<T\>::Type'*: un nombre dependiente no es un tipo error C2923: *'s1'*: *'S2\<T\>::Type'* no es un argumento de tipo de template válido para el parámetro *'T'***     Ejemplo 2: un nombre dependiente no es un tipo \(antes\)  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
     Ejemplo 2 \(después\)  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
-   Las variables de miembro `volatile`  **impiden los operadores de asignación y constructores definidos implícitamente**  
  
     Las versiones anteriores del compilador permitían que se generaran automáticamente constructores para copiar o mover y operadores de asignación para copiar o mover predeterminados para una clase con variables de miembro `volatile`. Este comportamiento anterior era incorrecta y no se ajusta al estándar de C\+\+. Ahora, el compilador considera que una clase que tiene variables de miembro volátiles tiene operadores de asignación y construcción no triviales, lo que impide que se generen implementaciones predeterminadas de estos operadores automáticamente.  Cuando esta clase es miembro de una unión \(o una unión anónima dentro de una clase\), los constructores para copiar o mover y los operadores de asignación de copiar o mover de la unión \(o la clase que contiene la unión anónima\) se definirán implícitamente como eliminados. Intentar crear o copiar la unión \(o la clase que contiene la unión anónima\) sin definirlas explícitamente es un error y, en tal caso, el compilador genera el error de compilador C2280 como resultado.  
  
 **error C2280: *'B::B\(const B &\)'*: se está intentando hacer referencia a una función eliminada**     Ejemplo \(antes\)  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
     Ejemplo \(después\)  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
-   **Las funciones miembro estáticas no admiten calificadores cv.**  
  
     Las versiones anteriores de Visual C\+\+ 2015 permitían que las funciones miembro estáticas tuvieran calificadores cv. Este comportamiento se debe a una regresión en Visual C\+\+ 2015 y Visual C\+\+ 2015 Update 1; Visual C\+\+ 2013 y las versiones anteriores de Visual C\+\+ rechazan el código escrito de este modo. El comportamiento de Visual C\+\+ 2015 y Visual C\+\+ 2015 Update 1 es incorrecto y no cumple el estándar de C\+\+.  Visual Studio 2015 Update 2 rechaza el código escrito de este modo y genera el error de compilador C2511 en su lugar.  
  
 **error C2511: 'void A::func\(void\) const': la función miembro sobrecargada no se ha encontrado en 'A'**     Ejemplo \(antes\)  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
     Ejemplo \(después\)  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
-   **No se permite la declaración adelantada de la enumeración en el código de WinRT** \(solo afecta a \/ZW\)  
  
     El código compilado para Windows Runtime \(WinRT\) no permite que los tipos `enum` se declaren por adelantado, del mismo modo que cuando el código C\+\+ administrado se compila para .NET Framework mediante el modificador de compilador \/clr. Este comportamiento garantiza que siempre se conozca el tamaño de una enumeración y que se pueda proyectar correctamente al sistema de tipos de WinRT. El compilador rechaza el código escrito de este modo y genera los errores de compilador C2599 y C3197.  
  
 **error C2599: *'CustomEnum'*: no se permite la declaración adelantada de una enumeración WinRT error C3197: *'public'*: solamente se puede utilizar en definiciones**     Ejemplo \(antes\)  
  
    ```cpp  
    namespace A {  
      public enum class CustomEnum: int32;  // forward declaration; error C2599, error C3197  
    }  
  
    namespace A {  
      public enum class CustomEnum: int32  
      {  
        Value1  
      };  
    }  
  
    public ref class Component sealed  
    {  
    public:  
      CustomEnum f()  
      {  
        return CustomEnum::Value1;  
      }  
    };  
    ```  
  
     Ejemplo \(después\)  
  
    ```cpp  
  
              // forward declaration of CustomEnum removed  
  
    namespace A {  
      public enum class CustomEnum: int32  
      {  
        Value1  
      };  
    }  
  
    public ref class Component sealed  
    {  
    public:  
      CustomEnum f()  
      {  
        return CustomEnum::Value1;  
      }  
    };  
    ```  
  
-   **El operador no miembro sobrecargado new y el operador delete no se pueden declarar como inline**  \(nivel 1 \(\/ W1\), activo de forma predeterminada\)  
  
     Las versiones anteriores del compilador no generan ninguna advertencia cuando las funciones de operador no miembro new y de operador delete se declaraban como inline. El código escrito de este modo tiene un formato incorrecto \(no se requiere ningún diagnóstico\) y puede provocar problemas de memoria derivados de operadores new y delete no coincidentes \(especialmente si se usan junto con una desasignación dimensionada\) que puede resultar difícil de diagnosticar.   Ahora, el compilador emite la advertencia C4595 para ayudarle a identificar el código escrito de este modo.  
  
 **advertencia C4595: *'operator new'*: las funciones new o delete de operador no miembro no se pueden declarar como inline**     Ejemplo \(antes\)  
  
    ```cpp  
  
              inline void* operator new(size_t sz)  // warning C4595  
    {  
      ...  
    }  
    ```  
  
     Ejemplo \(después\)  
  
    ```cpp  
  
              void* operator new(size_t sz)  // removed inline  
    {  
      ...  
    }  
    ```  
  
     Corregir el código escrito de este modo puede requerir el traslado de las definiciones de operador fuera de un archivo de encabezado y al archivo de origen correspondiente.