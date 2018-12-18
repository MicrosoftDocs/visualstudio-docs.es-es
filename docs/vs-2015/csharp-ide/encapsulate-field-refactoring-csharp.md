---
title: Encapsular campo (refactorización, C#) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 35d7e03e30aa5301ee65f15a8591fbccd1de3fcd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223553"
---
# <a name="encapsulate-field-refactoring-c"></a>Encapsular campo (Refactorización, C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El **encapsular campo** operación de refactorización le permite crear rápidamente una propiedad de un campo existente y, a continuación, actualizar sin problemas el código con referencias a la nueva propiedad.  
  
 Cuando un [campo](http://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7) es [pública](http://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e), otros objetos tendrán acceso directo a ese campo y puede modificarlo, sin ser detectados por el objeto que posee el campo. Mediante el uso de [propiedades](http://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8) que encapsulen ese campo, se puede deshabilitar el acceso directo a los campos.  
  
 Para crear la nueva propiedad, el **encapsular campo** operación cambia el modificador de acceso para el campo que desea encapsular a [privada](http://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8)y, a continuación, genera [obtener](http://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71)y [establecer](http://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619) descriptores de acceso para ese campo. En algunos casos solo se genera un descriptor de acceso `get`, como cuando el campo se declara de solo lectura.  
  
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
  
     También puede haga clic en el cursor, apuntar a **refactorizar**y, a continuación, haga clic en **encapsular campo** para mostrar el **encapsular campo** cuadro de diálogo.  
  
4.  Especifique la configuración.  
  
5.  Presione ENTRAR o haga clic en el **Aceptar** botón.  
  
6.  Si ha seleccionado la **vista previa de cambios de referencia** opción, el **vista previa de cambios de referencia** abre la ventana. Haga clic en el **aplicar** botón.  
  
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
 El **encapsular campo** operación solo es posible cuando el cursor está situado en la misma línea que la declaración de campo.  
  
 Para las declaraciones de varios campos, **encapsular campo** utiliza la coma como límite entre los campos e inicia la refactorización en el campo que está más cerca del cursor y en la misma línea que el cursor. También puede especificar qué campo desea encapsular si selecciona el nombre de dicho campo en la declaración.  
  
 El código generado por esta operación de refactorización se modela mediante la característica de fragmentos de código de encapsular campo. Los fragmentos de código son modificables. Para obtener más información, vea [Fragmentos de código](../ide/code-snippets.md).  
  
## <a name="see-also"></a>Vea también  
 [Refactorización (C#)](../csharp-ide/refactoring-csharp.md)   
 [Fragmentos de código de Visual C#](../ide/visual-csharp-code-snippets.md)