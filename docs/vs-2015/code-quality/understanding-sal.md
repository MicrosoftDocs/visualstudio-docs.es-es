---
title: Descripción de SAL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: c8f29a909f6aef75976a551546d4cbeafdf03b37
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291872"
---
# <a name="understanding-sal"></a>Introducción a SAL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El lenguaje de anotación de código fuente (SAL) de Microsoft proporciona un conjunto de anotaciones que puede usar para describir cómo una función usa sus parámetros, las suposiciones que hace sobre ellos y las garantías que realiza cuando finaliza. Las anotaciones se definen en el archivo de encabezado `<sal.h>`. El análisis de código de C++ Visual Studio para utiliza anotaciones sal para modificar su análisis de funciones. Para obtener más información sobre SAL 2,0 para el desarrollo de controladores de Windows, consulte [anotaciones de sal 2,0 para controladores de Windows](https://go.microsoft.com/fwlink/?LinkId=250979).  
  
 De forma nativa, C C++ y proporcionan solo maneras limitadas para que los desarrolladores expresen sistemáticamente la intención y la invarianza. Mediante el uso de anotaciones SAL, puede describir las funciones con mayor detalle para que los desarrolladores que las utilizan puedan comprender mejor cómo usarlas.  
  
## <a name="what-is-sal-and-why-should-you-use-it"></a>¿Qué es SAL y por qué debe usarlo?  
 En pocas palabras, SAL es una manera económica de permitir que el compilador Compruebe su código.  
  
### <a name="sal-makes-code-more-valuable"></a>SAL hace que el código sea más valioso  
 SAL puede ayudarle a simplificar el diseño del código, tanto a los usuarios como a las herramientas de análisis de código. Considere este ejemplo que muestra la función en tiempo de ejecución de C `memcpy`:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 ¿Se puede saber qué hace esta función? Cuando se implementa o se llama a una función, deben mantenerse ciertas propiedades para garantizar la corrección del programa. Simplemente examinando una declaración como la del ejemplo, no sabe lo que son. Sin anotaciones SAL, debería confiar en la documentación o en los comentarios de código. Esta es la documentación de MSDN para `memcpy` dice:  
  
> "Copia el número de bytes de src en el destino. Si el origen y el destino se superponen, el comportamiento de memcpy es indefinido. Use memmove para administrar regiones superpuestas.   
> **Nota de seguridad:** Asegúrese de que el búfer de destino tiene el mismo tamaño o mayor que el búfer de origen. Para obtener más información, vea evitar saturaciones del búfer.  
  
 La documentación contiene un par de bits de información que sugieren que el código tiene que mantener determinadas propiedades para garantizar la corrección del programa:  
  
- `memcpy` copia el `count` de bytes del búfer de origen en el búfer de destino.  
  
- El búfer de destino debe ser al menos tan grande como el búfer de origen.  
  
  Sin embargo, el compilador no puede leer la documentación o los comentarios informativos. No sabe que hay una relación entre los dos búferes y `count`, y tampoco puede adivinar en efecto una relación. SAL podría proporcionar más claridad sobre las propiedades y la implementación de la función, como se muestra aquí:  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 Observe que estas anotaciones son similares a la información de la documentación de MSDN, pero son más concisas y siguen un patrón semántico. Al leer este código, puede comprender rápidamente las propiedades de esta función y cómo evitar problemas de seguridad de saturación del búfer. Incluso mejor, los patrones semánticos que SAL proporciona pueden mejorar la eficacia y la eficacia de las herramientas de análisis de código automatizadas en la detección temprana de posibles errores. Imagine que alguien escribe esta implementación con errores de `wmemcpy`:  
  
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
  
 Esta implementación contiene un error común sin conexión. Afortunadamente, el autor del código incluyó la anotación de tamaño del búfer de SAL; una herramienta de análisis de código podría detectar el error analizando esta función por sí sola.  
  
### <a name="sal-basics"></a>Aspectos básicos de SAL  
 SAL define cuatro tipos básicos de parámetros, que se clasifican por patrón de uso.  
  
|Categoría|Anotación de parámetro|Descripción|  
|--------------|--------------------------|-----------------|  
|**Entrada a la función llamada**|`_In_`|Los datos se pasan a la función llamada y se tratan como de solo lectura.|  
|**Entrada a la función llamada y salida al llamador**|`_Inout_`|Los datos que se pueden usar se pasan a la función y es posible que se modifiquen.|  
|**Salida al llamador**|`_Out_`|El autor de la llamada solo proporciona espacio para escribir en la función a la que se ha llamado. La función llamada escribe datos en ese espacio.|  
|**Salida de puntero al llamador**|`_Outptr_`|Como la **salida al autor de la llamada**. El valor devuelto por la función llamada es un puntero.|  
  
 Estas cuatro anotaciones básicas se pueden hacer más explícitamente de varias maneras. De forma predeterminada, se supone que los parámetros de puntero anotados son obligatorios; deben ser no NULL para que la función se ejecute correctamente. La variación más usada de las anotaciones básicas indica que un parámetro de puntero es opcional; si es NULL, la función puede seguir teniendo éxito en el trabajo.  
  
 En esta tabla se muestra cómo distinguir entre los parámetros obligatorios y opcionales:  
  
||Los parámetros son obligatorios|Los parámetros son opcionales|  
|-|-----------------------------|-----------------------------|  
|**Entrada a la función llamada**|`_In_`|`_In_opt_`|  
|**Entrada a la función llamada y salida al llamador**|`_Inout_`|`_Inout_opt_`|  
|**Salida al llamador**|`_Out_`|`_Out_opt_`|  
|**Salida de puntero al llamador**|`_Outptr_`|`_Outptr_opt_`|  
  
 Estas anotaciones ayudan a identificar posibles valores no inicializados y punteros NULL no válidos de forma formal y precisa. Si se pasa NULL a un parámetro necesario, se podría producir un bloqueo o se devolvería un código de error "Failed". En cualquier caso, la función no puede realizar su trabajo correctamente.  
  
## <a name="sal-examples"></a>Ejemplos de SAL  
 En esta sección se muestran ejemplos de código para las anotaciones de SAL básicas.  
  
### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>Uso de la herramienta de análisis de Visual Studio Code para encontrar defectos  
 En los ejemplos, la herramienta de análisis de Visual Studio Code se usa junto con anotaciones SAL para encontrar defectos de código. Aquí se explica cómo hacerlo.  
  
##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>Para usar las herramientas de análisis de código de Visual Studio y SAL  
  
1. En Visual Studio, abra un C++ proyecto que contenga anotaciones sal.  
  
2. En la barra de menús, elija **compilar**, **Ejecutar Análisis de código en la solución**.  
  
    Tenga en cuenta el \_en\_ ejemplo de esta sección. Si ejecuta el análisis de código en él, se muestra esta ADVERTENCIA:  
  
   > **C6387 valor de parámetro no válido**   
   > ' pinta ' podría ser ' 0 ': no cumple con las especificaciones de la función ' incaller '.  
  
### <a name="example-the-_in_-annotation"></a>Ejemplo: \_en\_ anotación  
 La anotación `_In_` indica que:  
  
- El parámetro debe ser válido y no se modificará.  
  
- La función solo leerá desde el búfer de un solo elemento.  
  
- El autor de la llamada debe proporcionar el búfer e inicializarlo.  
  
- `_In_` especifica "solo lectura". Un error común es aplicar `_In_` a un parámetro que debería tener la anotación `_Inout_` en su lugar.  
  
- se permite el `_In_`, pero el analizador lo omite en escalares que no son de puntero.  
  
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
  
 Si usa Visual Studio Code Analysis en este ejemplo, valida que los llamadores pasen un puntero no nulo a un búfer inicializado para `pInt`. En este caso, `pInt` puntero no puede ser NULL.  
  
### <a name="example-the-_in_opt_-annotation"></a>Ejemplo: \_In_opt anotación\_  
 `_In_opt_` es igual que `_In_`, salvo que el parámetro de entrada puede ser NULL y, por lo tanto, la función debe comprobar esto.  
  
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
  
 El análisis de Visual Studio Code valida que la función comprueba si hay valores NULL antes de tener acceso al búfer.  
  
### <a name="example-the-_out_-annotation"></a>Ejemplo: la anotación de\_ de \_out  
 `_Out_` admite un escenario común en el que se pasa un puntero no nulo que apunta a un búfer de elementos y la función inicializa el elemento. El autor de la llamada no tiene que inicializar el búfer antes de la llamada. la función llamada promete inicializarla antes de que se devuelva.  
  
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
  
 Visual Studio Code herramienta de análisis valida que el autor de la llamada pasa un puntero no nulo a un búfer para `pInt` y que la función inicializa el búfer antes de que se devuelva.  
  
### <a name="example-the-_out_opt_-annotation"></a>Ejemplo: \_Out_opt anotación\_  
 `_Out_opt_` es igual que `_Out_`, salvo que el parámetro puede ser NULL y, por lo tanto, la función debe comprobar esto.  
  
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
  
 El análisis de Visual Studio Code valida que esta función comprueba si hay valores NULL antes de desreferenciar `pInt` y, si `pInt` no es NULL, el búfer lo inicializa la función antes de que se devuelva.  
  
### <a name="example-the-_inout_-annotation"></a>Ejemplo: la anotación \_INOUT\_  
 `_Inout_` se usa para anotar un parámetro de puntero que la función puede cambiar. El puntero debe apuntar a datos inicializados válidos antes de la llamada, e incluso si cambia, todavía debe tener un valor válido en la devolución. La anotación especifica que la función puede leer y escribir libremente en el búfer de un elemento. El autor de la llamada debe proporcionar el búfer e inicializarlo.  
  
> [!NOTE]
> Como `_Out_`, `_Inout_` debe aplicarse a un valor modificable.  
  
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
  
 El análisis de Visual Studio Code valida que los llamadores pasan un puntero no nulo a un búfer inicializado para `pInt`y que, antes de la devolución, `pInt` sigue siendo no NULL y se inicializa el búfer.  
  
### <a name="example-the-_inout_opt_-annotation"></a>Ejemplo: \_Inout_opt anotación\_  
 `_Inout_opt_` es igual que `_Inout_`, salvo que el parámetro de entrada puede ser NULL y, por lo tanto, la función debe comprobar esto.  
  
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
  
 El análisis de Visual Studio Code valida que esta función comprueba si hay valores NULL antes de tener acceso al búfer, y si `pInt` no es NULL, la función inicializa el búfer antes de que se devuelva.  
  
### <a name="example-the-_outptr_-annotation"></a>Ejemplo: la anotación \_Outptr\_  
 `_Outptr_` se usa para anotar un parámetro que está pensado para devolver un puntero.  El propio parámetro no debe ser NULL y la función llamada devuelve un puntero no nulo en él y ese puntero apunta a datos inicializados.  
  
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
  
 El análisis de Visual Studio Code valida que el autor de la llamada pasa un puntero no nulo para `*pInt`y que la función inicializa el búfer antes de que se devuelva.  
  
### <a name="example-the-_outptr_opt_-annotation"></a>Ejemplo: \_Outptr_opt anotación\_  
 `_Outptr_opt_` es igual que `_Outptr_`, salvo que el parámetro es opcional, el llamador puede pasar un puntero NULL para el parámetro.  
  
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
  
 El análisis de Visual Studio Code valida que esta función comprueba si hay valores NULL antes de que se desreferencia `*pInt` y que la función inicializa el búfer antes de que se devuelva.  
  
### <a name="example-the-_success_-annotation-in-combination-with-_out_"></a>Ejemplo: la anotación \_Success\_ en combinación con \_out\_  
 Las anotaciones se pueden aplicar a la mayoría de los objetos.  En concreto, puede anotar toda una función.  Una de las características más obvias de una función es que puede ejecutarse correctamente o producir un error. Pero, al igual que ocurre con la asociación entre un búfer yC++ su tamaño, C/no puede expresar correctamente la función o el error. Mediante el uso de la anotación `_Success_`, puede indicar qué es el éxito de una función como.  El parámetro de la anotación `_Success_` es simplemente una expresión que, cuando es true, indica que la función se ha realizado correctamente. La expresión puede ser cualquier cosa que pueda controlar el analizador de anotaciones. Los efectos de las anotaciones después de que se devuelva la función solo se aplican cuando la función se ejecuta correctamente. En este ejemplo se muestra cómo `_Success_` interactúa con `_Out_` para hacer lo correcto. Puede usar la palabra clave `return` para representar el valor devuelto.  
  
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
  
 La anotación `_Out_` hace que el análisis de Visual Studio Code valide que el llamador pasa un puntero no nulo a un búfer para `pInt`y que la función inicializa el búfer antes de que se devuelva.  
  
## <a name="sal-best-practice"></a>Procedimiento recomendado SAL  
  
### <a name="adding-annotations-to-existing-code"></a>Agregar anotaciones a código existente  
 SAL es una tecnología eficaz que puede ayudarle a mejorar la seguridad y la confiabilidad del código. Después de aprender SAL, puede aplicar la nueva habilidad a su trabajo diario. En el nuevo código, puede usar especificaciones basadas en SAL por diseño a lo largo de; en el código anterior, puede agregar anotaciones incrementalmente y, por tanto, aumentar las ventajas cada vez que se actualice.  
  
 Los encabezados públicos de Microsoft ya están anotados. Por lo tanto, se recomienda que en los proyectos Anote primero las funciones de nodo hoja y las funciones que llaman a las API de Win32 para sacar el máximo partido.  
  
### <a name="when-do-i-annotate"></a>¿Cuándo se anota?  
 Estas son algunas directrices:  
  
- Anotar todos los parámetros de puntero.  
  
- Anotar anotaciones de intervalo de valores para que el análisis de código pueda garantizar la seguridad de búferes y punteros.  
  
- Anotar reglas de bloqueo y bloquear los efectos secundarios. Para obtener más información, consulte [anotar el comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md).  
  
- Anotar propiedades de controlador y otras propiedades específicas del dominio.  
  
  O bien, puede anotar todos los parámetros para que su intención resulte clara en todo y para facilitar la comprobación de que se han realizado anotaciones.  
  
## <a name="related-resources"></a>Recursos relacionados  
 [Blog del equipo de análisis de código](https://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## <a name="see-also"></a>Vea también  
 [Uso de anotaciones sal para reducir defectos deC++ C/Code](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Anotar parámetros de función y valores Devueltos](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotar el comportamiento](../code-quality/annotating-function-behavior.md) de la función   
 [Anotar Structs y clases](../code-quality/annotating-structs-and-classes.md)   
 [Anotar el comportamiento de bloqueo](../code-quality/annotating-locking-behavior.md)   
 [Especificar Cuándo y dónde se aplica una anotación](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Procedimientos recomendados y ejemplos](../code-quality/best-practices-and-examples-sal.md)
