---
redirect_url: /visualstudio/csharp-ide/refactoring/encapsulate-field
title: "Encapsular campo (refactorización, C#) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7bd9e255b35ffb843c15d5ffa9c1547891bf437d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="encapsulate-field-refactoring-c"></a>Encapsular campo (Refactorización, C#)
El **encapsular campo** operación de refactorización le permite crear rápidamente una propiedad de un campo existente y, a continuación, actualice el código de sin problemas con las referencias a la nueva propiedad.  
  
 Cuando un [campo](/dotnet/csharp/programming-guide/classes-and-structs/fields) es [público](/dotnet/csharp/language-reference/keywords/public), otros objetos tienen acceso directo a ese campo y pueden modificarlo, sin ser detectados por el objeto que posee ese campo. Mediante el uso de [propiedades](/dotnet/csharp/programming-guide/classes-and-structs/properties) para encapsular ese campo, puede denegar el acceso directo a los campos.  
  
 Para crear la nueva propiedad, el **encapsular campo** operación cambia el modificador de acceso para el campo que desea encapsular a [privada](/dotnet/csharp/language-reference/keywords/private)y, a continuación, genera [obtener](/dotnet/csharp/language-reference/keywords/get)y [establecer](/dotnet/csharp/language-reference/keywords/set) descriptores de acceso para ese campo. En algunos casos solo se genera un descriptor de acceso `get`, como cuando el campo se declara de solo lectura.  
  
 El motor de refactorización actualiza el código con referencias a la nueva propiedad en las áreas especificadas en el **actualizar referencias** sección de la **encapsular campo** cuadro de diálogo.  
  
### <a name="to-create-a-property-from-a-field"></a>Para crear una propiedad a partir de un campo  
  
1.  Cree una aplicación de consola denominada `EncapsulateFieldExample` y, a continuación, reemplace `Program` por el siguiente código de ejemplo.  
  
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
  
2.  En el [Editor de código](../ide/writing-code-in-the-code-and-text-editor.md), coloque el cursor en la declaración, en el nombre del campo que desea encapsular. En el ejemplo siguiente, coloque el cursor sobre la palabra `width`:  
  
    ```csharp  
    public int width, height;  
    ```  
  
3.  En el **refactorizar** menú, haga clic en **encapsular campo**.  
  
     El **encapsular campo** aparece el cuadro de diálogo.  
  
     También puede escribir el método abreviado de teclado CTRL + R, E para mostrar el **encapsular campo** cuadro de diálogo.  
  
     También puede hacer clic el cursor, seleccione **refactorizar**y, a continuación, haga clic en **encapsular campo** para mostrar la **encapsular campo** cuadro de diálogo.  
  
4.  Especifique la configuración.  
  
5.  Presione ENTRAR o haga clic en el **Aceptar** botón.  
  
6.  Si ha seleccionado la **vista previa de cambios de referencia** opción, la **vista previa de cambios de referencia** abre la ventana. Haga clic en el **aplicar** botón.  
  
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
  
## <a name="remarks"></a>Comentarios  
 El **encapsular campo** operación sólo es posible cuando el cursor se sitúa en la misma línea que la declaración del campo.  
  
 Para las declaraciones que declaran varios campos, **encapsular campo** utiliza la coma como un límite entre los campos y se inicia la refactorización en el campo que está más cerca del cursor y en la misma línea que el cursor. También puede especificar qué campo desea encapsular si selecciona el nombre de dicho campo en la declaración.  
  
 El código generado por esta operación de refactorización se modela mediante la característica de fragmentos de código de encapsular campo. Los fragmentos de código son modificables. Para obtener más información, vea [Fragmentos de código](../ide/visual-csharp-code-snippets.md).  
  
## <a name="see-also"></a>Vea también  
 [Refactorización (C#)](refactoring-csharp.md)   
 [Fragmentos de código de Visual C#](../ide/visual-csharp-code-snippets.md)