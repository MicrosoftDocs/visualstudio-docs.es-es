---
title: Acerca de la ventana registros | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, about Registers window
- debugging [Visual Studio], Registers window
ms.assetid: ab354047-053e-4f94-8ac1-26e761442b6f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5364bf8ba45e4b569649920175c6e94fc46128ed
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561806"
---
# <a name="about-the-registers-window-in-visual-studio-c-c-visual-basic-f"></a>Acerca de la ventana de registros en Visual Studio (C#, C++, Visual Basic, F#)

La ventana **Registros** solo está disponible si está habilitada la depuración de nivel de dirección en el cuadro de diálogo **Opciones**, nodo **Depuración**.  
  
 Los registros son ubicaciones especiales dentro de un procesador (CPU) en las que se almacenan pequeñas cantidades de datos con los que el procesador trabaja de forma activa en cada momento. Cuando el código fuente se compila o se interpreta, se generan instrucciones que transfieren datos de la memoria a los registros y viceversa, según sea necesario. El acceso a los datos de los registros es muy rápido en comparación con el acceso a la memoria, de modo que el código que permite al procesador mantener datos en un registro para el acceso repetido a ellos suele ejecutarse más rápidamente que el código que requiere que el procesador cargue y descargue constantemente los registros. Para facilitar el que el compilador mantenga los datos en los registros y realice otras optimizaciones, debe evitar el uso de variables globales y usar variables locales siempre que sea posible. Del código escrito de este modo se dice que tiene una buena localidad de referencia. En algunos lenguajes, como C/C++, el programador puede declarar una variable de registro, lo que indica al compilador que haga lo posible por mantener la variable en un registro en todo momento. Para más información, consulte [Palabra clave Register](https://msdn.microsoft.com/library/5b66905a-2f7f-4918-bb55-5e66d4bc50f9).  
  
 Los registros pueden dividirse en dos tipos: de propósito general y de propósito especial. Los registros de propósito general contienen datos para operaciones generales, como sumar dos números o referirse a un elemento de una matriz. Los registros de propósito especial tienen un fin específico y un significado especializado. Un buen ejemplo es el registro puntero de pila, que el procesador utiliza para hacer un seguimiento de la pila de llamadas del programa. Como programador, probablemente no controlará directamente el puntero de pila. Sin embargo, este registro es esencial para el correcto funcionamiento del programa, ya que sin el puntero de pila el procesador no sabría a dónde regresar al terminar una llamada a una función.  
  
 La mayoría de los registros de uso general contienen sólo un elemento de datos único. Por ejemplo un entero único, un número en punto flotante o un elemento de una matriz. Algunos de los procesadores más actuales cuentan con unos registros de mayor tamaño, llamados registros vectoriales, que pueden contener una pequeña matriz de datos. Debido a su mayor capacidad, los registros vectoriales permiten realizar operaciones con matrices a gran velocidad. Los registros vectoriales comenzaron a utilizarse en equipos de gran tamaño, caros y de alto rendimiento, pero comienzan a estar disponibles en los microprocesadores, donde se usan con gran provecho en las operaciones gráficas intensivas.  
  
 Normalmente, un procesador tiene dos conjuntos de registros de propósito general, unos optimizado para operaciones en coma flotante, y otros para operaciones con números enteros. Como es lógico, los registros de estos grupos reciben el nombre de registros de coma flotante y registros de enteros, respectivamente.  
  
 El código administrado se compila en tiempo de ejecución en código nativo que obtiene acceso a los registros físicos del microprocesador. La ventana **Registros** muestra estos registros físicos para el código nativo o Common Language Runtime. La ventana **Registros** no muestra información para las aplicaciones de script o SQL, ya que estos lenguajes no contemplan el concepto de registros.  
  
 Para más información sobre cómo mostrar la ventana **Registros**, consulte [Using the Registers Window](../debugger/how-to-use-the-registers-window.md) (Uso de la ventana Registros).  
  
 Cuando observa la **registra** ventana, podrá ver entradas como `EAX = 003110D8`.  
  
 El símbolo a la izquierda de la `=` inicio de sesión es el nombre del registro, `EAX`, en este caso. El número a la derecha del signo `=` representa el contenido del registro.  
  
 La ventana **Registros** permite algo más que simplemente ver el contenido de un registro. Cuando el programa está en modo de interrupción en el código nativo, puede hacer clic en el contenido de un registro y modificar el valor. Esto no es algo que deba hacerse a la ligera. Si no comprende la función del registro que modifica y los datos que contiene, el resultado del cambio será probablemente el bloqueo del programa, u otra consecuencia no deseada. Desgraciadamente, una explicación detallada de los conjuntos de registros de los diversos procesadores Intel y compatibles queda muy lejos del alcance de esta breve introducción.  
  
## <a name="register-groups"></a>Grupos de registros  
 Por motivos de claridad, los registros se organizan en grupos en la ventana **Registros**. Si hace clic con el botón derecho en la ventana **Registros**, aparecerá un menú contextual con una lista de grupos que puede mostrar u ocultar según su conveniencia.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Utilice la ventana registros](../debugger/how-to-use-the-registers-window.md)   
 [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)