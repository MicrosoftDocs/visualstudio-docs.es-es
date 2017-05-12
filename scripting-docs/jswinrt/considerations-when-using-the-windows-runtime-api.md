---
title: "Consideraciones al utilizar la API de Windows en tiempo de ejecuci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, API de Windows en tiempo de ejecución"
ms.assetid: 2f56d70c-c80d-4876-8e6a-8ae031d31c22
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Consideraciones al utilizar la API de Windows en tiempo de ejecuci&#243;n
Puede utilizar casi todos los elementos de la API de Windows en tiempo de ejecución en JavaScript.  Sin embargo, hay algunos aspectos de la representación JavaScript de elementos de Windows en tiempo de ejecución que se deben tener en cuenta.  
  
> [!IMPORTANT]
>  Para obtener información sobre cómo crear componentes de Windows en tiempo de ejecución en C\+\+, C\# o Visual Basic y consumirlos en JavaScript, vea [Crear componentes de Windows en tiempo de ejecución en](http://msdn.microsoft.com/library/9a6b8f0a-7d5e-40a0-a9c5-a59b4908e133).  
  
## Casos especiales en representación de JavaScript de tipos de Windows en tiempo de ejecución  
  
-   Cadenas: una cadena no inicializada se pasa a un método de Windows en tiempo de ejecución como la cadena “undefined” y un conjunto de cadenas se pasa a `null` como la cadena “null”. \(Esto es true cuando un valor `null` o `undefined` se fuerza a una cadena.\) Antes de pasar una cadena a un método de Windows en tiempo de ejecución, debe inicializarla como la cadena vacía \(""\).  
  
-   Interfaces: no puede implementar una interfaz de Windows en tiempo de ejecución en JavaScript.  
  
-   Matrices: las matrices de Windows en tiempo de ejecución son de tamaño fijo, por lo que los métodos que cambian el tamaño de matrices en JavaScript no funcionan en las matrices de Windows en tiempo de ejecución.  
  
-   Matrices: si se pasa un valor de matriz de JavaScript a un método de Windows en tiempo de ejecución, se copia la matriz.  El método de Windows en tiempo de ejecución no puede modificar la matriz o sus miembros y devolverlos a la aplicación de JavaScript.  Sin embargo, puede utilizar matrices con tipo \(por ejemplo, [Int32Array \(Objeto\)](../javascript/reference/int32array-object.md)\), que no se copian.  
  
-   Estructuras: las estructuras de Windows en tiempo de ejecución son objetos en JavaScript.  Si desea pasar una estructura de Windows en tiempo de ejecución a un método de Windows en tiempo de ejecución, no cree una instancia de la estructura con la palabra clave `new`.  En su lugar, cree un objeto y agregue los miembros pertinentes y sus valores.  Los nombres de los miembros deben estar en la grafía Camel: `SomeStruct.firstMember`.  
  
-   Objetos: los objetos JavaScript no son iguales que los objetos de código administrado \(`System.Object`\).  No puede pasar un objeto de JavaScript a un método de Windows en tiempo de ejecución que requiere un `System.Object`.  
  
-   Identidad de objetos: en la mayoría de los casos, los objetos que pasan hacia delante y hacia atrás entre Windows en tiempo de ejecución y JavaScript no cambian.  El motor de JavaScript mantiene un mapa de objetos conocidos.  Cuando un objeto se devuelve desde Windows en tiempo de ejecución se compara con el mapa y, si no existe, se crea un nuevo objeto.  El mismo procedimiento se realiza para objetos que representan las interfaces devueltas por métodos de Windows en tiempo de ejecución.  Hay dos tipos de excepciones:  
  
    -   Los objetos que se devuelven desde una llamada de Windows en tiempo de ejecución y después tienen nuevas propiedades \(expando\) agregadas, no conservan sus nuevas propiedades cuando se pasan a Windows en tiempo de ejecución.  Sin embargo, cuando se devuelven a la aplicación JavaScript, porque se corresponden con el objeto existente, el objeto devuelto tiene propiedades expando.  
  
    -   Las estructuras y los delegados de Windows en tiempo de ejecución no se pueden identificar como idénticos a estructuras o delegados anteriormente utilizados.  Cada vez que se devuelve una estructura o un delegado, se obtiene una nueva referencia.  
  
-   Conflictos de nombre: varias interfaces de Windows en tiempo de ejecución pueden tener miembros con los mismos nombres.  Si se combinan en un único objeto de JavaScript \(que puede ser una representación de una clase en tiempo de ejecución o interfaz\), los miembros se representan con nombres completos.  Puede llamar a estos miembros mediante la sintaxis siguiente: `Class["MemberName"](parameter)`.  
  
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
  
     Aquí se muestra cómo se puede llamar al código anterior en JavaScript.  
  
    ```javascript  
    var example = new ExampleObject();  
    example["CollisionExample.InterfaceA.draw"](12);  
    example["CollisionExample.InterfaceB.draw"]("hello");  
    ```  
  
-   Parámetros `Out`: si un método de Windows en tiempo de ejecución tiene varios parámetros `out`, en JavaScript el método tiene un objeto JavaScript como su valor devuelto y el objeto tiene propiedades que corresponden al parámetro `out`.  Por ejemplo, considere la siguiente signatura de Windows en tiempo de ejecución en C\+\+.  
  
    ```cpp#  
    void ExampleMethod(  
      [OutAttribute] char^ first,   
      [OutAttribute] char^ second  
    )  
    ```  
  
     La versión de JavaScript de esta signatura es:  
  
    ```javascript  
    var returnValue = exampleMethod();  
  
    ```  
  
     En este ejemplo, `returnValue` es un objeto JavaScript que tiene dos campos: `first` y `second`.  
  
-   Miembros estáticos: Windows en tiempo de ejecución define los miembros estáticos y los miembros de instancia.  En JavaScript, agregue miembros estáticos al objeto asociado a la clase o interfaz de Windows en tiempo de ejecución.  
  
    ```javascript  
    // Static method.   
    var accel = Windows.Devices.Sensors.Accelerometer.getDefault();   
    // Instance method.   
    var reading = accel.getCurrentReading();            
    ```  
  
 Para obtener más información acerca de la representación JavaScript de los tipos básicos de Windows en tiempo de ejecución, vea [Representación de JavaScript de tipos de Windows Runtime](../jswinrt/javascript-representation-of-windows-runtime-types.md).