---
title: Refactorización de campo encapsulado (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b4f5ddbe7eab925b06584f00b04bed3c74e9811
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667572"
---
# <a name="encapsulate-field-refactoring-c"></a>Encapsular campo (Refactorización, C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La operación de refactorización **Encapsular campo** permite crear rápidamente una propiedad a partir de un campo existente y, a continuación, actualizar sin problemas el código con referencias a la nueva propiedad.

 Cuando un [campo](https://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7) es [público](https://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e), otros objetos tienen acceso directo a ese campo y pueden modificarlo, no detectado por el objeto que posee ese campo. Al usar [las propiedades](https://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8) para encapsular ese campo, puede denegar el acceso directo a los campos.

 Para crear la nueva propiedad, la operación **Encapsular campo** cambia el modificador de acceso del campo que desea encapsular a [privado](https://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8)y, a continuación, genera descriptores de acceso [Get](https://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71) y [set](https://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619) para ese campo. En algunos casos solo se genera un descriptor de acceso `get`, como cuando el campo se declara de solo lectura.

 El motor de refactorización actualiza el código con referencias a la nueva propiedad en las áreas especificadas en la sección **Actualizar referencias** del cuadro de diálogo **Encapsular campo** .

### <a name="to-create-a-property-from-a-field"></a>Para crear una propiedad a partir de un campo

1. Cree una aplicación de consola denominada `EncapsulateFieldExample` y, a continuación, reemplace `Program` por el siguiente código de ejemplo.

    ```csharp
    class Square
    {
        // Select the word 'width' and then use Encapsulate Field.
        public int width, height;
    }
    class MainClass
    {
        public static void Main()
        {
            Square mySquare = new Square();
            mySquare.width = 110;
            mySquare.height = 150;
            // Output values for width and height.
            Console.WriteLine("width = {0}", mySquare.width);
            Console.WriteLine("height = {0}", mySquare.height);
        }
    }
    ```

2. En el [Editor de código](../ide/writing-code-in-the-code-and-text-editor.md), coloque el cursor en la declaración, en el nombre del campo que desea encapsular. En el ejemplo siguiente, coloque el cursor sobre la palabra `width`:

    ```csharp
    public int width, height;
    ```

3. En el menú **refactorizar** , haga clic en **Encapsular campo**.

     Aparece el cuadro de diálogo **Encapsular campo** .

     También puede escribir el método abreviado de teclado CTRL + R, E para mostrar el cuadro de diálogo **Encapsular campo** .

     También puede hacer clic con el botón secundario en el cursor, seleccionar **refactorizar**y, a continuación, hacer clic en **Encapsular campo** para mostrar el cuadro de diálogo **Encapsular campo** .

4. Especifique la configuración.

5. Presione entrar o haga clic en el botón **Aceptar** .

6. Si ha seleccionado la opción **vista previa de los cambios de referencia** , se abre la ventana **vista previa** de los cambios de referencia. Haga clic en el botón **Aplicar**.

     El siguiente código de los descriptores de acceso `get` y `set` se muestra en el archivo de código fuente:

    ```csharp
    public int Width
    {
        get { return width; }
        set { width = value; }
    }
    ```

     El código del método `Main` también se actualiza al nuevo nombre de propiedad `Width`.

    ```csharp
    Square mySquare = new Square();
    mySquare.Width = 110;
    mySquare.height = 150;
    // Output values for width and height.
    Console.WriteLine("width = {0}", mySquare.Width);
    ```

## <a name="remarks"></a>Observaciones
 La operación **Encapsular campo** solo es posible cuando el cursor se coloca en la misma línea que la declaración de campo.

 En el caso de las declaraciones que declaran varios campos, **Encapsular campo** usa la coma como límite entre los campos e inicia la refactorización en el campo más próximo al cursor y en la misma línea que el cursor. También puede especificar qué campo desea encapsular si selecciona el nombre de dicho campo en la declaración.

 El código generado por esta operación de refactorización se modela mediante la característica de fragmentos de código de encapsular campo. Los fragmentos de código son modificables. Para obtener más información, vea [Fragmentos de código](../ide/code-snippets.md).

## <a name="see-also"></a>Consulte también
 [Refactorización (C#)](../csharp-ide/refactoring-csharp.md) [fragmentos de código de Visual c#](../ide/visual-csharp-code-snippets.md)