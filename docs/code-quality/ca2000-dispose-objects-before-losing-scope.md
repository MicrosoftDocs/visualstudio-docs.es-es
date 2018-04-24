---
title: 'CA2000: Eliminar objetos antes de perder el ámbito'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 436dec37598aac31d0de2e7cb495f49b2a0bf41e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: Eliminar objetos antes de perder el ámbito
|||
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|Identificador de comprobación|CA2000|
|Categoría|Microsoft.Reliability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Se crea un objeto local de un tipo <xref:System.IDisposable>, pero el objeto no se elimina antes de que todas las referencias al mismo estén fuera de ámbito.

## <a name="rule-description"></a>Descripción de la regla
 Si un objeto que se puede eliminar (método Dispose) no se elimina de forma explícita antes de que todas las referencias a él estén fuera de ámbito, el objeto se eliminará en algún momento indeterminado cuando el recolector de elementos no utilizados ejecute el finalizador del objeto. Puesto que podría producirse un evento excepcional que impida que se ejecute el finalizador del objeto, el objeto debe eliminarse de forma explícita.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llame a <xref:System.IDisposable.Dispose%2A> en el objeto antes de que todas las referencias a este estén fuera de ámbito.

 Observe que puede usar la instrucción `using` (`Using` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) para ajustar objetos que implementan `IDisposable`. Los objetos que se ajustan de esta manera se eliminarán automáticamente al cerrar el bloque `using`.

 A continuación se indican algunas situaciones donde la instrucción using no es suficiente para proteger objetos IDisposable, lo que puede hacer que se produzca la advertencia CA2000.

-   Devolver un objeto descartable requiere que el objeto se construya en un bloque try/finally fuera de un bloque using.

-   No deben inicializarse miembros de un objeto descartable en el constructor de una instrucción using.

-   Anidar constructores únicamente protegidos por un controlador de excepciones. Por ejemplo,

    ```csharp
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
    { ... }
    ```

     hace que se produzca CA2000 porque un error en la construcción del objeto StreamReader puede hacer que el objeto FileStream nunca se cierre.

-   Los objetos dinámicos deben usar un objeto de sombra para implementar el patrón Dispose de los objetos IDisposable.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una advertencia de esta regla a menos que haya llamado a un método del objeto que llama a `Dispose`, como <xref:System.IO.Stream.Close%2A>, o si el método que generó la advertencia devuelve un objeto IDisposable que ajusta el objeto.

## <a name="related-rules"></a>Reglas relacionadas
 [CA2213: Aplique Dispose a los campos a los que se pueda](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2202: No usar Dispose varias veces en objetos](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Ejemplo
 Si implementa un método que devuelve un objeto descartable, use un bloque try/finally sin un bloque catch para asegurarse de que el objeto se elimina. Al usar un bloque try/finally, permite la generación de excepciones en el momento del error y se asegura de que se elimine el objeto.

 En el método OpenPort1, se puede producir un error en la llamada para abrir el elemento SerialPort del objeto ISerializable o en la llamada a SomeMethod. En esta implementación se desencadena una advertencia CA2000.

 En el método OpenPort2, dos objetos SerialPort se declaran y establecen en NULL:

-   `tempPort`, que se usa para probar la correcta realización de las operaciones del método.

-   `port`, que se usa para el valor devuelto del método.

 `tempPort` se construye y abre en un bloque `try` y cualquier otro trabajo que sea necesario se realiza en el mismo bloque `try`. Al final del bloque `try`, el puerto abierto se asigna al objeto `port` que se devolverá y el objeto `tempPort` se establece en `null`.

 El bloque `finally` comprueba el valor de `tempPort`. Si no es NULL, se ha producido un error en una operación del método y `tempPort` se cierra para garantizar la liberación de los recursos. El objeto Port devuelto contendrá el objeto SerialPort abierto si las operaciones del método se han realizado correctamente o será NULL si se produce un error en una operación.

```csharp
public SerialPort OpenPort1(string portName)
{
   SerialPort port = new SerialPort(portName);
   port.Open();  //CA2000 fires because this might throw
   SomeMethod(); //Other method operations can fail
   return port;
}

public SerialPort OpenPort2(string portName)
{
   SerialPort tempPort = null;
   SerialPort port = null;
   try
   {
      tempPort = new SerialPort(portName);
      tempPort.Open();
      SomeMethod();
      //Add any other methods above this line
      port = tempPort;
      tempPort = null;

   }
   finally
   {
      if (tempPort != null)
      {
         tempPort.Close();
      }
   }
   return port;
}
```

```vb
Public Function OpenPort1(ByVal PortName As String) As SerialPort

   Dim port As New SerialPort(PortName)
   port.Open()    'CA2000 fires because this might throw
   SomeMethod()   'Other method operations can fail
   Return port

End Function


Public Function OpenPort2(ByVal PortName As String) As SerialPort

   Dim tempPort As SerialPort = Nothing
   Dim port As SerialPort = Nothing

   Try
      tempPort = New SerialPort(PortName)
      tempPort.Open()
      SomeMethod()
      'Add any other methods above this line
      port = tempPort
      tempPort = Nothing

   Finally
      If Not tempPort Is Nothing Then
         tempPort.Close()
      End If


   End Try

   Return port

End Function
```

## <a name="example"></a>Ejemplo
 De forma predeterminada, el compilador de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] comprueba el desbordamiento en todos los operadores aritméticos. Por consiguiente, cualquier operación aritmética de Visual Basic puede producir una excepción de tipo <xref:System.OverflowException>. Esto podría dar lugar a infracciones inesperadas de reglas como CA2000. Por ejemplo, la siguiente función CreateReader1 producirá una infracción de CA2000 porque el compilador de Visual Basic emite una instrucción de comprobación de desbordamiento para la suma que podría producir una excepción que provocaría que StreamReader no se eliminase.

 Para corregir este problema, puede deshabilitar la emisión de comprobaciones de desbordamiento mediante el compilador de Visual Basic en el proyecto o puede modificar el código como en la siguiente función CreateReader2.

 Para deshabilitar la emisión de comprobaciones de desbordamiento, haga clic en el nombre del proyecto en el Explorador de soluciones y, a continuación, haga clic en **propiedades**. Haga clic en **compilar**, haga clic en **opciones de compilación avanzadas**y, a continuación, comprobar **Quitar comprobaciones de desbordamiento con enteros**.

  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>Vea también
 <xref:System.IDisposable> [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)