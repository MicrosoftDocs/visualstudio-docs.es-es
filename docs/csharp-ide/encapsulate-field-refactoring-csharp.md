---
title: "Encapsular campo (Refactorizaci&#243;n, C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.encapsulatefield"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Encapsular campo (operación de refactorización) [C#]"
  - "refactorización [C#], Encapsular campo"
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Encapsular campo (Refactorizaci&#243;n, C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La operación de refactorización **Encapsular campo** \(Encapsulate Field\) permite crear rápidamente una propiedad a partir de un campo existente y, a continuación, actualizar sin problemas el código con referencias a la nueva propiedad.  
  
 Cuando un [campo](/dotnet/csharp/programming-guide/classes-and-structs/fields) es [público](/dotnet/csharp/language-reference/keywords/public), los otros objetos tendrán acceso directo a ese campo y podrán modificarlo, sin que el objeto que posee el campo lo detecte.  Mediante [propiedades](/dotnet/csharp/programming-guide/classes-and-structs/properties) que encapsulen ese campo, se puede deshabilitar el acceso directo a los campos.  
  
 Para crear la nueva propiedad, la operación **Encapsular campo** cambia el modificador de acceso del campo que desea encapsular a [privado](/dotnet/csharp/language-reference/keywords/private) y, a continuación, genera descriptores de acceso [get](/dotnet/csharp/language-reference/keywords/get) y [set](/dotnet/csharp/language-reference/keywords/set) para ese campo.  En algunos casos solo se genera un descriptor de acceso `get`, como cuando el campo se declara de solo lectura.  
  
 El motor de refactorización actualiza el código con referencias a la nueva propiedad en las áreas especificadas en la sección **Actualizar referencias** del cuadro de diálogo **Encapsular campo**.  
  
### Para crear una propiedad a partir de un campo  
  
1.  Cree una aplicación de consola denominada `EncapsulateFieldExample` y, a continuación, reemplace `Program` por el siguiente código de ejemplo.  
  
    ```c#  
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
  
2.  En el [Editor de código](../ide/writing-code-in-the-code-and-text-editor.md), coloque el cursor sobre la declaración, en el nombre del campo que desea encapsular.  En el ejemplo siguiente, coloque el cursor sobre la palabra `width`:  
  
    ```c#  
    public int width, height;  
    ```  
  
3.  En el menú **Refactorizar**, haga clic en **Encapsular campo**.  
  
     Aparece el cuadro de diálogo **Encapsular campo**.  
  
     También puede usar el método abreviado de teclado CTRL \+ R, E para mostrar el cuadro de diálogo **Encapsular campo**.  
  
     O bien, puede hacer clic con el botón derecho en el cursor, apuntar a **Refactorizar** y, a continuación, hacer clic en **Encapsular campo** para mostrar el cuadro de diálogo **Encapsular campo**.  
  
4.  Especifique la configuración.  
  
5.  Presione ENTRAR o haga clic en el botón **Aceptar**.  
  
6.  Si seleccionó la opción **Vista previa de los cambios de referencia**, se abre la ventana **Vista previa de los cambios de referencia**.  Haga clic en el botón **Aplicar**.  
  
     El siguiente código de los descriptores de acceso `get` y `set` se muestra en el archivo de código fuente:  
  
    ```c#  
    public int Width  
    {  
        get { return width; }  
        set { width = value; }  
    }  
    ```  
  
     El código del método `Main` también se actualiza al nuevo nombre de propiedad `Width`.  
  
    ```c#  
    Square mySquare = new Square();  
    mySquare.Width = 110;  
    mySquare.height = 150;  
    // Output values for width and height.  
    Console.WriteLine("width = {0}", mySquare.Width);  
    ```  
  
## Comentarios  
 La operación **Encapsular campo** solo es posible cuando el cursor se coloca en la misma línea que la declaración de campo.  
  
 Para las declaraciones de varios campos, **Encapsular campo** usa la coma como límite de separación entre los campos e inicia la refactorización en el campo que está más cerca del cursor, en la misma línea que el cursor.  También puede especificar qué campo desea encapsular si selecciona el nombre de dicho campo en la declaración.  
  
 El código generado por esta operación de refactorización se modela mediante la característica de fragmentos de código de encapsular campo.  Los fragmentos de código son modificables.  Para obtener más información, vea [Fragmentos de código](../ide/code-snippets.md).  
  
## Vea también  
 [Refactorización \(C\#\)](../csharp-ide/refactoring-csharp.md)   
 [Fragmentos de código de Visual C\#](../ide/visual-csharp-code-snippets.md)