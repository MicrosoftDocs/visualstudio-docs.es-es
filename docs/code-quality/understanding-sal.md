---
title: "Introducci&#243;n a SAL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Introducci&#243;n a SAL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El lenguaje de anotación de código fuente de Microsoft \(SAL\) proporciona un conjunto de anotaciones que se puede utilizar para describir cómo una función utiliza parámetros, las suposiciones que crea sobre ellas y las garantías que crea cuando finaliza.  Las anotaciones se definen en el archivo de encabezado `<sal.h>`.  El análisis de código de Visual Studio para C\+\+ utiliza las anotaciones de SAL para modificar su análisis de funciones.  Para obtener más información sobre SAL 2,0 para el desarrollo del controlador de Windows, vea [SAL 2,0 Annotations para los controladores de Windows](http://go.microsoft.com/fwlink/?LinkId=250979).  
  
 De forma nativa, C y C\+\+ proporcionan sólo formas limitadas para que los desarrolladores expresen intentos e invarianza.  Mediante anotaciones SAL, se pueden describir las funciones con mayor detalle de modo que los programadores que las utilicen sepan cómo utilizarlas.  
  
## ¿Qué es SAL y por qué debería implementarse?  
 Dicho simplemente, SAL es una manera económica de permitir al compilador comprobar el código automáticamente.  
  
### SAL hace el código más valioso  
 SAL puede hacer que su diseño del código sea más comprensible, para los seres humanos y para las herramientas de análisis de código.  Considere este ejemplo que muestra la función `memcpy`del runtime de C:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 ¿Se puede saber lo que hace esta función?  Cuando se implementa o se llama a una función, algunas propiedades se deben mantener para garantizar la corrección de programa.  Hacer sólo un examen de una declaración como la del ejemplo, no sirve para saber qué son.  Sin anotaciones SAL, se tendría que confiar en los comentarios de la documentación o del código.  Esto es lo que dice la documentación de MSDN para `memcpy` :  
  
> “Copia count bytes de src a dest.Si el origen y destino se superponen, el comportamiento de memcpy es indefinido.Utilice memmove para controlar las áreas superpuestas.  
> **Nota de seguridad:** Asegúrese de que el búfer de destino es del mismo tamaño o mayor que el búfer de origen.Para obtener más información, vea Para evitar las saturaciones del búfer.  
  
 La documentación contiene un par de bits de información que sugieren que el código tiene que mantener ciertas propiedades para garantizar la exactitud del programa:  
  
-   `memcpy` copia `count` bytes del búfer de origen al búfer de destino.  
  
-   El búfer de destino debe ser por lo menos tan grande como el búfer de origen.  
  
 Sin embargo, el compilador no puede leer la documentación o comentarios informales.  No sabe que existe una relación entre los dos búferes y `count` y tampoco puede saber mucho sobre una relación.  SAL podría proporcionar más claridad sobre las propiedades y la implementación de la función, como se muestra aquí:  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 Observe que estas anotaciones se parecen a la información en la documentación de MSDN, pero más concisas y siguiendo un modelo semántico.  Cuando lea este código, puede entender rápidamente las propiedades de esta función y cómo evitar los problemas de seguridad de la saturación del búfer.  Mejor aún, los modelos semánticos que SAL proporciona pueden mejorar la eficacia y la eficiencia de las herramientas de análisis de código automatizadas en la detección temprana de posibles errores.  Imagine que alguien escribe esta implementación con errores de `wmemcpy`:  
  
```cpp  
  
wchar_t * wmemcpy(  
   _Out_writes_all_(count) wchar_t *dest,   
   _In_reads_(count) const wchar_t *src,   
   size_t count)  
{  
   size_t i;  
   for (i = 0; i <= count; i++) { // BUG: off-by-one error  
      dest[i] = src[i];  
   }  
   return dest;  
}  
  
```  
  
 Esta aplicación contiene un error off\-by\-one común.  Afortunadamente, el autor del código incluye la herramienta de análisis de código de anotación —una herramienta de análisis de código podría capturar el bug analizando sólo esta función.  
  
### fundamentos de SAL  
 SAL define cuatro clases básicas de parámetros, que están clasificadas por el modelo de uso.  
  
|Categoría|Anotación de parámetro|Descripción|  
|---------------|----------------------------|-----------------|  
|**Para llamar la función de entrada**|`_In_`|Los datos se pasan a la función denominada y se tratan como de solo lectura.|  
|**Entrada de llamada de función y de salida al llamador**|`_Inout_`|Los datos que se pasan a la función y potencialmente se modifican.|  
|**Salida al llamador**|`_Out_`|El llamador sólo proporciona el espacio para la función llamada para escribir.  La función llamada escribe datos en ese espacio.|  
|**Salida del puntero al llamador**|`_Outptr_`|Como **Salida al llamador**.  El valor devuelto por la función llamada es un puntero.|  
  
 Estas cuatro anotaciones básicas se pueden crear más explícitas de varias maneras.  De forma predeterminada, el puntero indica que se asume que los parámetros son requeridos —deberán ser no nulos para que la función sea correcta.  La variación más utilizada de las anotaciones básicas indica que un puntero que es el parámetro opcional —si es NULL, la función todavía puede tener éxito en realizar su trabajo.  
  
 Esta tabla muestra cómo distinguir entre parámetros opcionales y requeridos:  
  
||Se requieren parámetros|Los parámetros son opcionales|  
|-|-----------------------------|-----------------------------------|  
|**Para llamar la función de entrada**|`_In_`|`_In_opt_`|  
|**Entrada de llamada de función y de salida al llamador**|`_Inout_`|`_Inout_opt_`|  
|**Salida al llamador**|`_Out_`|`_Out_opt_`|  
|**Salida del puntero al llamador**|`_Outptr_`|`_Outptr_opt_`|  
  
 Estas anotaciones ayudan a identificar posibles valores sin inicializar y aplicaciones no válidas del puntero NULL de manera formal y precisa.  Pasar NULL a un parámetro obligatorio puede provocar un bloqueo, o podría provocar un código de error “error” que se devolverá.  En cualquier caso, la función no puede tener éxito al realizar su trabajo.  
  
## Ejemplos de SAL  
 Esta sección muestra ejemplos de código para las anotaciones básicas SAL.  
  
### Mediante la herramienta de análisis de código de Visual Studio para encontrar defectos  
 En los ejemplos, la herramienta de análisis de código de Visual Studio se utiliza junto con anotaciones SAL para encontrar defectos de código.  Aquí se muestra cómo hacerlo.  
  
##### Para utilizar las herramientas de análisis de código de Visual Studio y SAL  
  
1.  En Visual Studio, abra un proyecto de C\+\+ que contiene las anotaciones SAL.  
  
2.  En la barra de menús, elija **Compilación**, **Ejecutar análisis de código en la solución**.  
  
     Considere el ejemplo \_In\_ de esta sección.  Si ejecuta el análisis de código en él, se muestra esta advertencia:  
  
    > **C6387 Valor de parámetro no válido**   
    > 'pInt' podría ser '0': no cumple la especificación para la función 'InCallee'.  
  
### Ejemplo: La anotación de \_In\_  
 La anotación `_In_` indica que:  
  
-   El parámetro debe ser válido y no se modificará.  
  
-   La función leerá sólo del búfer de un elemento.  
  
-   El llamador debe proporcionar el búfer e inicializarlo.  
  
-   `_In_` especifica "solo lectura".  Un error común es aplicar `_In_` a un parámetro que debe tener la anotación `_Inout_` en su lugar.  
  
-   Se permite `_In_` pero lo omite el analizador en escalares de no puntero.  
  
```cpp  
void InCallee(_In_ int *pInt)  
{  
   int i = *pInt;  
}  
  
void GoodInCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
  
   InCallee(pInt);  
   delete pInt;     
}  
  
void BadInCaller()  
{  
   int *pInt = NULL;  
   InCallee(pInt); // pInt should not be NULL  
}  
  
```  
  
 Si se utiliza el análisis de código de Visual Studio en este ejemplo, valida que los llamadores pasen un puntero no nulo a un búfer inicializado para `pInt`.  En este caso, el puntero `pInt` no puede ser NULL.  
  
### Ejemplo: La anotación \_In\_opt\_  
 `_In_opt_` es igual que `_In_`, salvo que el parámetro de entrada puede ser NULL y, por consiguiente, la función debe comprobar esto.  
  
```cpp  
  
void GoodInOptCallee(_In_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
   }  
}  
  
void BadInOptCallee(_In_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
}  
  
void InOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOptCallee(pInt);  
   BadInOptCallee(pInt);  
}  
  
```  
  
 El análisis de código de Visual Studio validará que la función compruebe si es NULL antes de obtener acceso al búfer.  
  
### Ejemplo: La anotación \_Out\_  
 `_Out_` admite un escenario común en el que un puntero no nulo que señala a un búfer de elemento se pasa y la función inicializa el elemento.  El llamador no tiene que inicializar el búfer antes de la llamada; la función llamada va a inicializarla antes de retornar.  
  
```cpp  
  
void GoodOutCallee(_Out_ int *pInt)  
{  
   *pInt = 5;  
}  
  
void BadOutCallee(_Out_ int *pInt)  
{  
   // Did not initialize pInt buffer before returning!  
}  
  
void OutCaller()  
{  
   int *pInt = new int;  
   GoodOutCallee(pInt);  
   BadOutCallee(pInt);  
   delete pInt;  
}  
  
```  
  
 La herramienta de análisis de código de Visual Studio valida que el llamador pase un puntero no nulo a un búfer para `pInt` y que el búfer sea inicializado por la función antes de retornar.  
  
### Ejemplo: La anotación \_Out\_opt\_  
 `_Out_opt_` es igual que `_Out_`, salvo que el parámetro puede ser NULL y, por consiguiente, la función debe comprobar esto.  
  
```cpp  
  
void GoodOutOptCallee(_Out_opt_ int *pInt)  
{  
   if (pInt != NULL) {  
      *pInt = 5;  
   }  
}  
  
void BadOutOptCallee(_Out_opt_ int *pInt)  
{  
   *pInt = 5; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutOptCaller()  
{  
   int *pInt = NULL;  
   GoodOutOptCallee(pInt);  
   BadOutOptCallee(pInt);  
}  
  
```  
  
 El análisis de código de Visual Studio validará que la función compruebe si es NULL antes de que se desreferencie `pInt` y si `pInt` no es NULL, que el búfer sea inicializado por la función antes de retornar.  
  
### Ejemplo: La anotación \_Inout\_  
 `_Inout_` se utiliza para anotar un parámetro de puntero que puede cambiar la función.  El puntero debe señalar a datos inicializados válidos antes de la llamada e incluso si cambia, aún debe tener un valor válido en la devolución.  Anotación especifica que la función puede leer libremente y escribir en el búfer de un elemento.  El llamador debe proporcionar el búfer e inicializarlo.  
  
> [!NOTE]
>  Como `_Out_`, `_Inout_` se debe aplicar un valor modificable.  
  
```cpp  
  
void InOutCallee(_Inout_ int *pInt)  
{  
   int i = *pInt;  
   *pInt = 6;  
}  
  
void InOutCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
   InOutCallee(pInt);  
   delete pInt;  
}  
  
void BadInOutCaller()  
{  
   int *pInt = NULL;  
   InOutCallee(pInt); // ‘pInt’ should not be NULL  
}  
  
```  
  
 El análisis de código de Visual Studio validará que los llamadores pasen un puntero no nulo a un búfer inicializado para `pInt`, y que, antes de devolución, `pInt` todavía sea NULL y se inicialice el búfer.  
  
### Ejemplo: La anotación \_Inout\_opt\_  
 `_Inout_opt_` es igual que `_Inout_`, salvo que el parámetro de entrada se permite que sea NULL y, por consiguiente, la función debe comprobar esto.  
  
```cpp  
  
void GoodInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
      *pInt = 6;  
   }  
}  
  
void BadInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
   *pInt = 6;  
}  
  
void InOutOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOutOptCallee(pInt);  
   BadInOutOptCallee(pInt);  
}  
  
```  
  
 El análisis de código de Visual Studio validará que la función compruebe si es NULL antes de obtener acceso al búfer y, si `pInt` no es NULL, que el búfer sea inicializado por la función antes de retornar.  
  
### Ejemplo: La anotación \_Outptr\_  
 `_Outptr_` se utiliza para anotar un parámetro que planea devolver un puntero.  El parámetro propio no debe ser NULL y la función llamada devuelve un puntero no nulo en ella y ese puntero apunta a datos inicializados.  
  
```cpp  
  
void GoodOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 5;  
  
   *pInt = pInt2;  
}  
  
void BadOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   // Did not initialize pInt buffer before returning!  
   *pInt = pInt2;  
}  
  
void OutPtrCaller()  
{  
   int *pInt = NULL;  
   GoodOutPtrCallee(&pInt);  
   BadOutPtrCallee(&pInt);  
}  
  
```  
  
 El análisis de código de Visual Studio valida que el llamador pase un puntero no nulo para `*pInt` y que el búfer sea inicializado por la función antes de retornar.  
  
### Ejemplo: La anotación \_Outptr\_opt\_  
 `_Outptr_opt_` es igual que `_Outptr_`, salvo que el parámetro es llamador opcional —el llamador puede pasar un puntero NULL para el parámetro.  
  
```cpp  
  
void GoodOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
  
   if(pInt != NULL) {  
      *pInt = pInt2;  
   }  
}  
  
void BadOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
   *pInt = pInt2; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutPtrOptCaller()  
{  
   int **ppInt = NULL;  
   GoodOutPtrOptCallee(ppInt);  
   BadOutPtrOptCallee(ppInt);  
}  
  
```  
  
 El análisis de código de Visual Studio validará que la función compruebe si es NULL antes de que se desreferencie `*pInt` y que el búfer sea inicializado por la función antes de retornar.  
  
### Ejemplo: El \_Success\_ Anotación junto con \_Out\_  
 Las anotaciones se pueden aplicar a la mayoría de los objetos.  En particular, se puede anotar una función completa.  Una de las características más obvias de una función es que puede tener éxito o error.  Pero como la asociación entre un búfer y su tamaño, C\/C\+\+ no puede expresar el éxito o error de una función.  Mediante la anotación `_Success_`, se puede establecer qué tiene éxito parece tener una función.  El parámetro para la anotación `_Success_` es una expresión que cuando es verdadera indica que la función ha tenido éxito.  La expresión puede ser cualquier cosa que el analizador de anotación puede controlar.  Los efectos de las anotaciones después de que retornen de la función sólo son aplicables cuando la función tiene éxito.  Este ejemplo muestra cómo `_Success_` interactúa con `_Out_` para hacer lo correcto.  Se puede utilizar la palabra clave `return` para representar el valor devuelto.  
  
```cpp  
  
_Success_(return != false) // Can also be stated as _Success_(return)  
bool GetValue(_Out_ int *pInt, bool flag)  
{  
   if(flag) {  
      *pInt = 5;  
      return true;  
   } else {  
      return false;  
   }  
}  
  
```  
  
 La anotación `_Out_` hace que el análisis de código de Visual Studio valide que el llamador pase un puntero no nulo a un búfer para `pInt` y que el búfer sea inicializado por la función antes de retornar.  
  
## Procedimiento recomendado SAL  
  
### Agregar anotaciones al código existente  
 SAL es una tecnología eficaz que puede ayudar a mejorar la seguridad y confiabilidad del código.  Después de que se obtenga información SAL, se puede aplicar el nuevo conocimiento a su trabajo diario.  En el nuevo código, se pueden utilizar especificaciones basadas en SAL por diseño en todas partes; en un código previo, se pueden agregar anotaciones mejoradas y por tanto aumentar las ventajas cada vez que se actualiza.  
  
 Los encabezados públicos de Microsoft ya están anotados.  Por consiguiente, sugerimos que en los proyectos primero se anoten funciones de nodo hoja y las funciones que llaman API Win32 para obtener el mayor beneficio.  
  
### ¿Cuándo anotar?  
 He aquí algunas instrucciones:  
  
-   Anotar todos los parámetros de puntero.  
  
-   Observe las anotaciones del siguiente valor intervalo de modo que el análisis de código puede garantizar la seguridad del búfer y del puntero.  
  
-   Anotar las reglas y efectos secundarios de bloqueo.  Para obtener más información, vea [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md).  
  
-   Anotar las propiedades del controlador y otras propiedades específicas del dominio.  
  
 O se pueden anotar todos los parámetros para clarificar el intento y para facilitar comprobar que las anotaciones se han finalizado.  
  
## Recursos relacionados  
 [Blog del equipo de análisis de código](http://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## Vea también  
 [Utilizar anotaciones SAL para reducir defectos de código de C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Anotar parámetros de función y valores devueltos](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotar el comportamiento de funciones](../code-quality/annotating-function-behavior.md)   
 [Anotar structs y clases](../code-quality/annotating-structs-and-classes.md)   
 [Anotar comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)   
 [Especificar cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)