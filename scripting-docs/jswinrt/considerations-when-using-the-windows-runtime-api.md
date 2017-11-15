---
title: Consideraciones al usar la API de Windows Runtime | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: JavaScript, Windows Runtime API
ms.assetid: 2f56d70c-c80d-4876-8e6a-8ae031d31c22
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 693b3dac9def5533417638c3ec1c0de8db1d5fe3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="considerations-when-using-the-windows-runtime-api"></a>Consideraciones al usar la API de Windows Runtime
Puede usar casi todos los elementos de la API de Windows Runtime en JavaScript. Sin embargo, hay algunos aspectos de la representación de JavaScript de elementos de Windows Runtime que se deben tener en cuenta.  
  
> [!IMPORTANT]
>  Para obtener información sobre cómo crear componentes de Windows Runtime en C++, C# o Visual Basic y consumirlos en JavaScript, consulte [Crear componentes de Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp) y [Crear componentes de Windows Runtime en C# y Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).  
  
## <a name="special-cases-in-the-javascript-representation-of-windows-runtime-types"></a>Casos especiales en la representación de JavaScript de tipos de Windows Runtime  
  
-   Cadenas: una cadena sin inicializar se pasa a un método de Windows Runtime como la cadena "sin definir" y una cadena establecida en `null` se pasa como la cadena "null". (Esto es así siempre que un valor `null` o `undefined` se pasa a una cadena.) Antes de pasar una cadena a un método de Windows Runtime, debe inicializarla como la cadena vacía ("").  
  
-   Interfaces: no se puede implementar una interfaz de Windows Runtime en JavaScript.  
  
-   Matrices: las matrices de Windows Runtime no son redimensionables, así que los métodos que cambian de tamaño las matrices en JavaScript no funcionan en matrices de Windows Runtime.  
  
-   Matrices: si se pasa un valor de matriz de JavaScript a un método de Windows Runtime, la matriz se copia. El método de Windows Runtime no puede modificar la matriz, o sus miembros, y devolverla a la aplicación de JavaScript. Sin embargo, puede utilizar matrices con tipo (por ejemplo, [objetos Int32Array](../javascript/reference/int32array-object.md)), que no se copian.  
  
-   Estructuras: las estructuras de Windows Runtime son objetos en JavaScript. Si desea pasar una estructura de Windows Runtime a un método de Windows Runtime, no cree una instancia de la estructura con la palabra clave `new`. En su lugar, cree un objeto y agregue los miembros pertinentes y sus valores. Los nombres de los miembros deben estar en mayúsculas: `SomeStruct.firstMember`.  
  
-   Objetos: los objetos de JavaScript no son iguales a los objetos de código administrados (`System.Object`). No se puede pasar un objeto de JavaScript a un método de Windows Runtime que requiere un elemento `System.Object`.  
  
-   Identidad del objeto: en la mayoría de los casos, los objetos pasados una y otra vez entre Windows Runtime y JavaScript no cambian. El motor de JavaScript mantiene un mapa de objetos conocidos. Cuando un objeto se devuelve desde Windows Runtime, se hace coincidir con el mapa y, si no existe, se crea uno nuevo. El mismo procedimiento se sigue para objetos que representan interfaces que se devuelven mediante métodos de Windows Runtime. Hay dos tipos de excepciones:  
  
    -   Los objetos que se devuelven por una llamada de Windows Runtime y luego se les agregan nuevas propiedades (expando), no conservan sus nuevas propiedades cuando se pasan de vuelta a Windows Runtime. Sin embargo, cuando se devuelven a la aplicación de JavaScript, porque se hacen coincidir con el objeto existente, el objeto devuelto tiene las propiedades de expando.  
  
    -   Las estructuras y los delegados de Windows Runtime no se pueden identificar como idénticos a las estructuras o delegados anteriormente usados. Cada vez que se devuelve una estructura o un delegado, se obtiene una nueva referencia.  
  
-   Colisión de nombre: varias interfaces de Windows Runtime pueden tener miembros con los mismos nombres. Si se combinan en un único objeto de JavaScript (que puede ser una representación de una clase en tiempo de ejecución o una interfaz), los miembros se representan con nombres completos. Se puede llamar a estos miembros mediante la siguiente sintaxis: `Class["MemberName"](parameter)`.  
  
     En el código siguiente, dos interfaces tienen un método Draw y una clase en tiempo de ejecución implementa ambas interfaces.  
  
    ```cpp#  
    namespace CollisionExample {  
        interface InterfaceA  
        {  
            HRESULT Draw([in] Int32 a);  
        }  
        interface InterfaceB  
        {  
            HRESULT Draw([in] HString a);  
        }  
        runtimeclass ExampleObject {  
          interface InterfaceA  
          interface InterfaceB  
        }  
    }  
    ```  
  
     Así es como puede llamar al código anterior en JavaScript.  
  
    ```JavaScript  
    var example = new ExampleObject();  
    example["CollisionExample.InterfaceA.draw"](12);  
    example["CollisionExample.InterfaceB.draw"]("hello");  
    ```  
  
-   Parámetros `Out`: si un método de Windows Runtime tiene varios parámetros `out`, en JavaScript el método tiene un objeto de JavaScript como su valor devuelto, y el objeto tiene propiedades que corresponden al parámetro `out`. Por ejemplo, considere la siguiente firma de Windows Runtime en C++.  
  
    ```cpp#  
    void ExampleMethod(  
      [OutAttribute] char^ first,   
      [OutAttribute] char^ second  
    )  
    ```  
  
     La versión de JavaScript de esta firma es:  
  
    ```JavaScript  
    var returnValue = exampleMethod();  
  
    ```  
  
     En este ejemplo, `returnValue` es un objeto de JavaScript que tiene dos campos: `first` y `second`.  
  
-   Miembros estáticos: Windows Runtime define los miembros estáticos y los miembros de instancia. En JavaScript, los miembros estáticos se agregan al objeto que está asociado con la clase o la interfaz de Windows Runtime.  
  
    ```JavaScript  
    // Static method.   
    var accel = Windows.Devices.Sensors.Accelerometer.getDefault();   
    // Instance method.   
    var reading = accel.getCurrentReading();            
    ```  
  
 Para obtener más información sobre la representación de JavaScript de los tipos básicos de Windows Runtime, consulte [Representación de JavaScript de tipos de Windows Runtime](../jswinrt/javascript-representation-of-windows-runtime-types.md) (Representación de JavaScript de tipos de Windows Runtime).