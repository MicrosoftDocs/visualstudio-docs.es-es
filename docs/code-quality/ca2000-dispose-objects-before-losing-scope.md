---
title: 'CA2000: Desechar objetos antes de perder el ámbito'
ms.date: 05/14/2019
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 732b3d683802c50042ee40fee1549a9d247e2470
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2019
ms.locfileid: "65804975"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: Desechar objetos antes de perder el ámbito

|||
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|Identificador de comprobación|CA2000|
|Categoría|Microsoft.Reliability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo

Un objeto local de un <xref:System.IDisposable> se crea el tipo, pero no se elimina el objeto antes de que todas las referencias al objeto están fuera del ámbito.

## <a name="rule-description"></a>Descripción de la regla

Si un objeto que se puede eliminar (método Dispose) no se elimina de forma explícita antes de que todas las referencias a él estén fuera de ámbito, el objeto se eliminará en algún momento indeterminado cuando el recolector de elementos no utilizados ejecute el finalizador del objeto. Puesto que podría producirse un evento excepcional que impida que se ejecute el finalizador del objeto, el objeto debe eliminarse de forma explícita.

### <a name="special-cases"></a>Casos especiales

No se desencadena la regla CA2000 para objetos locales de los siguientes tipos incluso si no se elimina el objeto:

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Pasar un objeto de uno de estos tipos a un constructor y, a continuación, asignarlo a un campo indican un *dispose de transferencia de la propiedad* para el tipo construido recientemente. Es decir, el tipo construido recién ahora es responsable de desechar el objeto. Si el código pasa un objeto de uno de estos tipos a un constructor, ninguna infracción de regla CA2000 ocurre incluso si no se elimina el objeto antes de todas las referencias a ella están fuera del ámbito.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, llame a <xref:System.IDisposable.Dispose%2A> en el objeto antes de que todas las referencias a este estén fuera de ámbito.

Puede usar el [ `using` instrucción](/dotnet/csharp/language-reference/keywords/using-statement) ([ `Using` ](/dotnet/visual-basic/language-reference/statements/using-statement) en Visual Basic) para ajustar objetos que implementan <xref:System.IDisposable>. Los objetos que se ajustan de esta manera se eliminan automáticamente al final de la `using` bloque. Sin embargo, las situaciones siguientes no deben o no se pueden controlar con un `using` instrucción:

- Para devolver un objeto descartable, debe construir el objeto en un `try/finally` bloquear fuera de un `using` bloque.

- No inicializa los miembros de un objeto descartable en el constructor de un `using` instrucción.

- Cuando se anidan los constructores que están protegidos por un solo controlador de excepciones en el [parte de la adquisición de un `using` instrucción](/dotnet/csharp/language-reference/language-specification/statements#the-using-statement), puede dar lugar a un error en el constructor externo en el objeto creado por el constructor anidado nunca está cerrando. En el ejemplo siguiente, un error en la <xref:System.IO.StreamReader> constructor puede provocar la <xref:System.IO.FileStream> objeto nunca se cierre. CA2000 marcadores en este caso una infracción de la regla.

   ```csharp
   using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
   { ... }
   ```

- Objetos dinámicos deben usar un objeto de sombra para implementar el patrón de dispose de <xref:System.IDisposable> objetos.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima una advertencia de esta regla a menos que:

- Se ha llamado a un método en el objeto que llama a `Dispose`, como <xref:System.IO.Stream.Close%2A>
- El método que se genera la advertencia de devuelve un <xref:System.IDisposable> objeto que encapsula el objeto
- El método de asignación no tiene la propiedad dispose; es decir, la responsabilidad de desechar el objeto se transfiere a otro objeto o un contenedor que ha creado en el método y devuelve al llamador

## <a name="related-rules"></a>Reglas relacionadas

- [CA2213: los campos descartables deben ser descartables](../code-quality/ca2213-disposable-fields-should-be-disposed.md)
- [CA2202: No desechar objetos varias veces](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Ejemplo

Si va a implementar un método que devuelve un objeto descartable, utilice un bloque try/finally sin un bloque catch para asegurarse de que el objeto se elimina. Al usar un bloque try/finally, permite la generación de excepciones en el momento del error y se asegura de que se elimine el objeto.

En el método OpenPort1, se puede producir un error en la llamada para abrir el elemento SerialPort del objeto ISerializable o en la llamada a SomeMethod. En esta implementación se desencadena una advertencia CA2000.

En el método OpenPort2, dos objetos SerialPort se declaran y establecen en NULL:

- `tempPort`, que se usa para probar la correcta realización de las operaciones del método.

- `port`, que se usa para el valor devuelto del método.

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

De forma predeterminada, el compilador de Visual Basic tiene todos los operadores aritméticos comprueba el desbordamiento. Por consiguiente, cualquier operación aritmética de Visual Basic puede producir una excepción de tipo <xref:System.OverflowException>. Esto podría dar lugar a infracciones inesperadas de reglas como CA2000. Por ejemplo, la siguiente función CreateReader1 producirá una infracción de CA2000 porque el compilador de Visual Basic emite una instrucción de comprobación de desbordamiento para la suma que podría producir una excepción que provocaría que StreamReader no se eliminase.

Para corregir este problema, puede deshabilitar la emisión de comprobaciones de desbordamiento mediante el compilador de Visual Basic en el proyecto o puede modificar el código como en la siguiente función CreateReader2.

Para deshabilitar la emisión de comprobaciones de desbordamiento, haga clic en el nombre del proyecto en el Explorador de soluciones y, a continuación, haga clic en **propiedades**. Haga clic en **compilar**, haga clic en **Advanced Compile Options**y, a continuación, compruebe **Quitar comprobaciones de desbordamiento con enteros**.

[!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>Vea también

- <xref:System.IDisposable>
- [Patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)