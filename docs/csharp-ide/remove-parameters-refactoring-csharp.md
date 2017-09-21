---
title: "Quitar par&#225;metros (Refactorizaci&#243;n, C#) | Microsoft Docs"
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
  - "vs.csharp.refactoring.remove"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "parámetros [C#], movimiento"
  - "refactorización [C#], quitar parámetros"
  - "Quitar parámetros (refactorización) [C#]"
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Quitar par&#225;metros (Refactorizaci&#243;n, C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`Remove Parameters` es una operación de refactorización que proporciona una manera sencilla de quitar parámetros de los métodos, indizadores o delegados.  Quitar parámetros cambia la declaración; en todas las ubicaciones donde se llama al miembro, el parámetro se quita para reflejar la nueva declaración.  
  
 La operación de quitar parámetros se realiza colocando primero el cursor en un método, indizador o delegado.  Cuando el cursor esté en la posición correcta, para invocar la operación Quitar `Parameters`, haga clic en el menú **Refactorizar**, presione el método abreviado de teclado o seleccione el comando en el menú contextual.  
  
> [!NOTE]
>  No se puede quitar el primer parámetro de un método de extensión.  
  
### Para quitar los parámetros  
  
1.  Cree una aplicación de consola denominada `RemoveParameters` y, a continuación, reemplace `Program` por el ejemplo siguiente.  
  
    ```c#  
    class A  
    {  
        // Invoke on 'A'.  
        public A(string s, int i) { }  
    }  
  
    class B  
    {  
        void C()  
        {  
            // Invoke on 'A'.  
            A a = new A("a", 2);  
        }  
    }  
    ```  
  
2.  Coloque el cursor en el método `A`, bien en la declaración de método o bien en la llamada al método.  
  
3.  En el menú **Refactorizar**, seleccione **Quitar parámetros** para mostrar el cuadro de diálogo **Quitar parámetros**.  
  
     También puede presionar CTRL\+R, V, que es el método abreviado de teclado para mostrar el cuadro de diálogo **Quitar parámetros**.  
  
     O bien, puede hacer clic con el botón secundario en el cursor, señalar **Refactorizar** y, a continuación, hacer clic en **Quitar parámetros** para mostrar el cuadro de diálogo **Quitar parámetros**.  
  
4.  Utilizando el campo **Parámetros**, sitúe el cursor en `int i` y, a continuación, haga clic en **Quitar**.  
  
5.  Haga clic en **Aceptar**.  
  
6.  En el cuadro de diálogo **Obtener vista previa de cambios \- Quitar parámetros**, haga clic en **Aplicar**.  
  
## Comentarios  
 Es posible quitar los parámetros de una declaración de método o de una llamada al método.  Coloque el cursor en la declaración de método o en el nombre de delegado e invoque a Quitar parámetros.  
  
> [!CAUTION]
>  Quitar parámetros permite eliminar un parámetro al que se hace referencia en el cuerpo del miembro, pero no quita las referencias a dicho parámetro en el cuerpo del método.  Esto puede producir errores de compilación en el código.  Sin embargo, puede usar el cuadro de diálogo **Vista previa de los cambios** para revisar el código antes de ejecutar la operación de refactorización.  
  
 Si un parámetro que se está quitando se modifica durante la llamada a un método, la eliminación del parámetro también quitará la modificación.  Por ejemplo, si se cambia una llamada a un método de  
  
```c#  
MyMethod(param1++, param2);  
```  
  
 por  
  
```c#  
MyMethod(param2);  
```  
  
 no se incrementará `param1` mediante la operación de refactorización.  
  
## Vea también  
 [Refactorización \(C\#\)](../csharp-ide/refactoring-csharp.md)