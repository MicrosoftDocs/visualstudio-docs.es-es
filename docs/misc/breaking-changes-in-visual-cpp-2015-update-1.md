---
title: "Cambios importantes en Visual C++ 2015 Update 1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c0b1c2b-e1cf-4767-885b-b98df9b3730e
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "mithom"
manager: "ghogen"
---
# Cambios importantes en Visual C++ 2015 Update 1
Al actualizar a Visual C\+\+ 2015 Update 1, se pueden producir errores de compilación o en tiempo de ejecución en código previamente compilado que se ejecutaba correctamente. Los cambios en el comportamiento del compilador o en tiempo de ejecución que producen tales problemas se conocen como *cambios importantes* y normalmente son necesarios debido a las modificaciones en el estándar del lenguaje C\+\+, las firmas de función o la disposición de los objetos en la memoria.  
  
 En el resto de este artículo se describen cambios importantes concretos en Visual C\+\+ 2015 Update 1. En el artículo, los términos “nuevo comportamiento” o “ahora” hacen referencia a esa versión. Los términos “comportamiento anterior” y “antes” hacen referencia a la versión de Visual Studio 2015 y versiones anteriores. Para información sobre cambios importantes que se produjeron entre Visual Studio 2013 y Visual Studio 2015, vea [Cambios importantes en Visual C\+\+ 2015](/visual-cpp/porting/visual-cpp-change-history-2003-20151).  
  
-   [Cambios importantes en el compilador](#BK_compiler)  
  
##  <a name="BK_compiler"></a> Compilador de Visual C\+\+  
  
-   **Clases base virtuales privadas y herencia indirecta**  
  
     Las versiones anteriores del compilador permiten una clase derivada para llamar a funciones de miembro de sus clases base *derivadas indirectamente* `private virtual`. Este comportamiento anterior era incorrecta y no se ajusta al estándar de C\+\+. El compilador ya no acepta el código escrito de este modo y emite el error del compilador C2280 como resultado.  
  
 **error C2280: *'void \*S3::\_\_delDtor\(unsigned int\)'*: intentando hacer referencia a una función eliminada**     Ejemplo \(antes\)  
  
    ```cpp  
    class base { protected: base(); ~base(); }; class middle: private virtual base {};class top: public virtual middle {}; void destroy(top *p) { delete p;  // }  
    ```  
  
     Ejemplo \(después\)  
  
    ```cpp  
    class base;  // as above class middle: protected virtual base {}; class top: public virtual middle {}; void destroy(top *p) { delete p; }  
    ```  
  
     O bien  
  
    ```  
    class base;  // as above class middle: private virtual base {}; class top: public virtual middle, private virtual bottom {}; void destroy(top *p) { delete p; }  
    ```  
  
-   **operator new y delete sobrecargado**  
  
     Las versiones anteriores del compilador permitieron que `operator new` no miembro y `operator delete` no miembro se declarasen estático y que se declararan en espacios de nombres distintos del espacio de nombres global.  Este comportamiento anterior crea un riesgo de que el programa no llame a la implementación del operador `new` o `delete` que el programador diseñó, generando un comportamiento en tiempo de ejecución incorrecto silencioso. El compilador ya no acepta el código escrito de este modo y emite el error del compilador C2323 en su lugar.  
  
 **Error C2323: *'operator new'*: es posible que las funciones de operator new o delete no miembros se declaren estáticas o en un espacio de nombres distinto del espacio de nombres global.**     Ejemplo \(antes\)  
  
    ```cpp  
  
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323  
    ```  
  
     Ejemplo \(después\)  
  
    ```cpp  
  
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'  
    ```  
  
     Además, aunque el compilador no ofrece un diagnóstico específico, se considera que el operador en línea nuevo está mal formado.  
  
-   **Llamada a 'operator *type*\(\)' \(conversión definida por el usuario\) en tipos que no son de clase**  
  
     Las versiones anteriores del compilador permitieron que se llamara 'operator *type*\(\)' en tipos que no son de clase mientras que se les ignora en modo silencioso. Este comportamiento anterior creó un riesgo de generación de código incorrecto silencioso, lo que produjo un comportamiento impredecible en tiempo de ejecución. El compilador ya no acepta el código escrito de este modo y emite el error del compilador C2228 en su lugar.  
  
 **error C2228: la izquierda de '.operator *type*' debe tener clase\/estructura\/unión**     Ejemplo \(antes\)  
  
    ```cpp  
    typedef int index_t; void bounds_check(index_t index); void login(int column) { bounds_check(column.operator index_t());  // error C2228 }  
    ```  
  
     Ejemplo \(después\)  
  
    ```cpp  
    typedef int index_t; void bounds_check(index_t index); void login(int column) { bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int' }  
    ```  
  
-   **Typename redundante en los especificadores de tipos elaborados**  
  
     Las versiones anteriores del compilador permitieron `typename` en especificadores de tipo elaborados; el código escrito de este modo es incorrecto semánticamente. El compilador ya no acepta el código escrito de este modo y emite el error del compilador C3406 en su lugar.  
  
 **error C3406: 'typename' no se puede usar en un especificador de tipo elaborado**     Ejemplo \(antes\)  
  
    ```cpp  
    template <typename class T> class container;  
    ```  
  
     Ejemplo \(después\)  
  
    ```cpp  
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case class container;  
    ```  
  
-   **Deducción de tipos de matrices de una lista de inicializadores**  
  
     Las versiones anteriores del compilador no admitían la deducción de tipos de matrices de una lista de inicializadores. El compilador admite ahora esta forma de deducción de tipos y, como resultado, las llamadas a las plantillas de función mediante listas de inicializadores podrían ser ahora ambiguas o se podría elegir una sobrecarga diferente de la de versiones anteriores del compilador. Para resolver estos problemas, el programa debe especificar ahora explícitamente la sobrecarga que el programador tiene como objetivo.  
  
     Cuando este comportamiento nuevo haga que la resolución de sobrecarga considere que un candidato adicional sea igual de bueno que el candidato histórico, la llamada pasará a ser ambigua y el compilador emitirá el error del compilador C2668 como resultado.  
  
 **error C2668: '*function*': llamada ambigua a una función sobrecargada.**     Ejemplo 1: llamada ambigua a una función sobrecargada \(antes\)  
  
    ```cpp  
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...) template <typename... Args> void f(int, Args...);  // template <int N, typename... Args> void f(const int (&)[N], Args...); int main() { // The compiler now considers this call ambiguous, and issues a compiler error  f({3});  error C2668: 'f' ambiguous call to overloaded function }  
    ```  
  
     Ejemplo 1: llamada ambigua a una función sobrecargada \(después\)  
  
    ```cpp  
    template <typename... Args> void f(int, Args...);  // template <int N, typename... Args> void f(const int (&)[N], Args...); int main() { // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it. f(3); }  
    ```  
  
     Cuando este comportamiento nuevo provoque que la resolución de sobrecarga considere que un candidato adicional es una coincidencia mejor que el candidato histórico, la llamada resuelve sin ambigüedades al nuevo candidato, provocando un cambio en el comportamiento del programa que probablemente sea diferente de lo que el programador pensaba.  
  
     Ejemplo 2: cambio en la resolución de sobrecarga \(antes\)  
  
    ```cpp  
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...) struct S { int i; int j; }; template <typename... Args> void f(S, Args...); template <int N, typename... Args> void f(const int *&)[N], Args...); int main() { // The compiler now resolves this call to f(const int (&)[N], Args...) instead  f({1, 2}); }  
    ```  
  
     Ejemplo 2: cambio en la resolución de sobrecarga \(después\)  
  
    ```cpp  
    struct S;  // as before template <typename... Args> void f(S, Args...); template <int N, typename... Args> void f(const int *&)[N], Args...); int main() { // To call f(S, Args...), perform an explicit cast to S on the initializer list. f(S{1, 2}); }  
    ```  
  
-   **Restauración de las advertencias de la instrucción switch**  
  
     Una versión anterior del compilador quitó advertencias existentes anteriormente relacionadas con instrucciones `switch`; estas advertencias se han restaurado ahora. El compilador emite ahora las advertencias restauradas y se emiten ahora advertencias relacionadas con los casos específicos \(incluido el caso predeterminado\) en la línea que contiene el caso que genera el error, en lugar de en la última línea de la instrucción switch. Como resultado de emitir ahora esas advertencias en líneas diferentes a como se hacía en el pasado, ya no se podrán suprimir según lo previsto las advertencias suprimidas anteriormente mediante `#pragma warning(disable:####)`. Para suprimir estas advertencias según lo previsto, es posible que sea necesario mover la directiva `#pragma warning(disable:####)` a una línea por encima del primer caso que genera potencialmente el error. Las siguientes son las advertencias restauradas.  
  
 **advertencia C4060: la instrucción switch no contiene etiquetas 'case' ni 'default' advertencia C4061: el enumerador '*bit1*' en la instrucción switch de la enumeración '*flags*' no está controlado de forma explícita por una etiqueta de caso advertencia C4061: el enumerador '*bit1*' en la instrucción switch de la enumeración '*flags*' no está controlado advertencia C4063: el caso '*bit32*' no es un valor válido para la instrucción switch de la enumeración '*flags*' advertencia C4064: instrucción switch de una enumeración'*flags*' incompleta advertencia C4065: la instrucción switch contiene etiquetas 'default' pero no etiquetas 'case' advertencia C4808: case '*value*' no es un valor correcto para la condición switch de tipo '*bool*' advertencia C4809: la instrucción switch tiene una etiqueta 'default' redundante; se proporcionan todas las etiquetas 'case' posibles**     Ejemplo de C4063: \(antes\)  
  
    ```cpp  
    class settings { public: enum flags { bit0 = 0x1, bit1 = 0x2, ... }; ... }; int main() { auto val = settings::bit1; switch (val) { case settings::bit0: break; case settings::bit1: break;  case settings::bit0 | settings::bit1:  // warning C4063 break; } };  
    ```  
  
     Ejemplo de C4063: \(después\)  
  
    ```cpp  
    class settings {...};  // as above int main() { // since C++11, use std::underlying_type to determine the underlying type of an enum typedef std::underlying_type<settings::flags>::type flags_t; auto val = settings::bit1; switch (static_cast<flags_t>(val)) { case settings::bit0: break; case settings::bit1: break; case settings::bit0 | settings::bit1:  // ok break; } };  
    ```  
  
     En su documentación se ofrecen ejemplos de las otras advertencias restauradas.  
  
-   **\#include: uso del especificador de principal\-directorio'..' en pathname** \(solo afecta a \/WX \/Wall\)  
  
     Las versiones anteriores del compilador no detectaron el uso del especificador de principal\-directorio '..' en el nombre de la ruta de acceso de las directivas `#include`. El código escrito de este modo normalmente está pensado para incluir encabezados que existen fuera del proyecto usando incorrectamente rutas de acceso relativas del proyecto. Este comportamiento antiguo crea un riesgo de que el programa se pueda compilar incluyendo un archivo de origen diferente del que pensaba el programador, o que esas rutas de acceso relativas no son portables a otros entornos de compilación. Ahora el compilador detecta y notifica al programador del código escrito de esta manera y emite una advertencia C4464 de compilador opcional, si se habilita.  
  
 **advertencia C4464: la ruta de acceso de inclusión relativa contiene '..'**     Ejemplo \(antes\)  
  
    ```cpp  
    #include "..\headers\C4426.h"  // emits warning C4464  
    ```  
  
     Ejemplo \(después\)  
  
    ```cpp  
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories  
    ```  
  
     Además, aunque el compilador no ofrece un diagnóstico específico, también se recomienda que el especificador de principal\-directorio ".." en el caso de que se use una nota para especificar los directorios de inclusión de su proyecto.  
  
-   **optimize\(\) \#pragma se extiende más allá del final del archivo de encabezado** \(solo afecta a \/WX \/Wall\)  
  
     Las versiones anteriores del compilador no detectaban cambios en la configuración de la marca de optimización que eluden un archivo de encabezado incluido dentro de una unidad de traducción. Ahora el compilador detecta y notifica al programador del código escrito de esta manera y emite una advertencia C4426 de compilador opcional en la ubicación de `#include` que genera el problema, si se habilita. Esta advertencia solo se emite si el cambio entra en conflicto con las marcas de optimización establecidas por los argumentos de la línea de comandos para el compilador.  
  
 **advertencia C4426: las marcas de optimización cambiadas después de incluir el encabezado se pueden deber a \#pragma optimize\(\)**     Ejemplo \(antes\)  
  
    ```cpp  
    // C4426.h #pragma optimize("g", off) ... // C4426.h ends // C4426.cpp #include "C4426.h"  // warning C4426  
    ```  
  
     Ejemplo \(después\)  
  
    ```cpp  
    // C4426.h #pragma optimize("g", off) ... #pragma optimize("", on)  // restores optimization flags set via command-line arguments // C4426.h ends // C4426.cpp #include "C4426.h"  
    ```  
  
-   **Mismatched \#pragma warning\(push\)** y **\#pragma warning\(pop\)** \(solo afecta a \/WX \/Wall\)  
  
     Las versiones anteriores del compilador no detectaban que los cambios de estado `#pragma warning(push)` se emparejaban con cambios de estado `#pragma warning(pop)` en un archivo de origen diferente, lo que rara vez es lo previsto. Este comportamiento antiguo creaba un riesgo de que el programa se compilara con un conjunto de advertencias habilitadas diferentes de lo que el programador había pensado, lo cual puede provocar un comportamiento en tiempo de ejecución incorrecto silencioso. Ahora el compilador detecta y notifica al programador del código escrito de esta manera y emite una advertencia C5031 de compilador opcional en la ubicación de `#pragma warning(pop)` coincidente, si se habilita. Esta advertencia incluye una nota en la que se hace referencia a la ubicación de la \#pragma warning\(push\) correspondiente.  
  
 **advertencia C5031: \#pragma warning\(pop\): probablemente falta de coincidencia,mensaje de estado de advertencia insertado en otro archivo**     Ejemplo \(antes\)  
  
    ```cpp  
    // C5031_part1.h #pragma warning(push) #pragma warning(disable:####) ... // C5031_part1.h ends without #pragma warning(pop) // C5031_part2.h ... #pragma warning(pop)  // pops a warning state not pushed in this source file ... // C5031_part1.h ends // C5031.cpp #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling' ... #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031 ...   
    ```  
  
     ejemplo \(después\)  
  
    ```cpp  
    // C5031_part1.h #pragma warning(push) #pragma warning(disable:####) ... #pragma warning(pop)  // pops the warning state pushed in this source file // C5031_part1.h ends without #pragma warning(pop) // C5031_part2.h #pragma warning(push)  // pushes the warning state pushed in this source file #pragma warning(disable:####) ... #pragma warning(pop) // C5031_part1.h ends // C5031.cpp #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order. ... #include "C5031_part2.h" ...   
    ```  
  
     Aunque es poco común, el código escrito de esta manera a veces es intencional. El código escrito de este modo es sensible a los cambios en orden `#include`; cuando sea posible, se recomienda que los archivos de código fuente administren el estado de advertencia de forma independiente.  
  
-   **\#pragma warning\(push\) sin coincidencia**  \(solo afecta a \/Wall \/WX\)  
  
     Las versiones anteriores del compilador no detectaron cambios de estado `#pragma warning(push)` sin coincidencia al final de una unidad de traducción. Ahora el compilador detecta y notifica al programador del código escrito de esta manera y emite una advertencia C5032 de compilador opcional en la ubicación de \#pragma warning\(push\) no coincidente, si se habilita. Esta advertencia solo se emite si no hay ningún error de compilación en la unidad de traducción.  
  
 **advertencia C5032: \#pragma warning\(push\) detectada con ningún  \#pragma warning\(pop\) correspondiente**     Ejemplo \(antes\)  
  
    ```cpp  
    // C5032.h #pragma warning(push) #pragma warning(disable:####) ... // C5032.h ends without #pragma warning(pop) // C5032.cpp #include "C5032.h" ... // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h  
    ```  
  
     Ejemplo \(después\)  
  
    ```cpp  
    // C5032.h #pragma warning(push) #pragma warning(disable:####) ... #pragma warning(pop) // matches #pragma warning (push) on line 1 // C5032.h ends // C5032.cpp #include "C5032.h" ... // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)  
    ```  
  
-   **Se pueden emitir advertencias adicionales como resultado del seguimiento del estado de advertencia \#pragma mejorado**  
  
     Las versiones anteriores del compilador no realizaron un seguimiento de los cambios de estados de advertencia \#pragma lo suficientemente bueno como para emitir todas las advertencias que se pretendían. Este comportamiento provocó un riesgo de que se suprimirían algunas advertencias de manera eficaz en circunstancias diferentes de las que tenía previstas el programador. El compilador realiza ahora el seguimiento del estado de advertencia \#pragma con mayor eficacia, especialmente en relación con los cambios de estado de advertencia \#pragma dentro de las plantillas, y opcionalmente emite nuevas advertencias C5031 y C5032 que están pensadas para ayudar al programador a localizar usos imprevistos de `#pragma warning(push)` y `#pragma warning(pop)`.  
  
     Como resultado del seguimiento del cambio de estado de advertencia de \#pragma mejorado, es posible emitir ahora las advertencias anteriormente suprimidas de manera incorrecta o las advertencias relacionadas con problemas que anteriormente tenían un mal diagnóstico.  
  
-   **Mejora de la identificación del código inalcanzable**  
  
     Los cambios en la biblioteca estándar de C\+\+ y la mejora en la capacidad para llamadas a funciones insertadas respecto a versiones anteriores del compilador pueden permitirle a este demostrar que determinado código ahora es inaccesible. Este nuevo comportamiento puede producir nuevas instancias de advertencia C4720 emitidas con mayor frecuencia.  
  
 **advertencia C4720: código inalcanzable**     En muchos casos, esta advertencia solo se puede emitir al compilar con las optimizaciones habilitadas, puesto que las optimizaciones pueden insertar más llamadas a funciones, eliminar código redundante o hacer posible de otra manera que se determine cierto código que no sea accesible. Hemos observado que las instancias nuevas de la advertencia C4720 han aparecido con frecuencia en bloques try\/catch, especialmente en relación con el uso de [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True).  
  
     Ejemplo \(antes\)  
  
    ```cpp  
    try { auto iter = std::find(v.begin(), v.end(), 5); } catch(…) { do_something();  // ok }  
    ```  
  
     Ejemplo \(después\)  
  
    ```cpp  
    try { auto iter = std::find(v.begin(), v.end(), 5); } catch(…) { do_something();  // warning C4702: unreachable code }  
    ```