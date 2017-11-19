---
redirect_url: /visualstudio/csharp-ide/refactoring/change-method-signature
title: "Quitar parámetros de refactorización (C#) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.csharp.refactoring.remove
dev_langs: CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d5e53d813d9b2dcefd2b2d19da2a76b6c0d1f989
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="remove-parameters-refactoring-c"></a>Quitar parámetros (Refactorización, C#)
`Remove Parameters`es una operación de refactorización que proporciona una manera sencilla para quitar parámetros de métodos, indizadores o delegados. Quitar parámetros cambia la declaración; en todas las ubicaciones donde se llama al miembro, se quita el parámetro para reflejar la nueva declaración.  
  
 Realizar la operación de quitar parámetros colocando primero el cursor en un método, indizador o delegado. Mientras el cursor está en la posición, para invocar la quitar `Parameters` operación, haga clic en el **refactorizar** menú, presione el método abreviado de teclado o seleccione el comando en el menú contextual.  
  
> [!NOTE]
>  No se puede quitar el primer parámetro en un método de extensión.  
  
### <a name="to-remove-parameters"></a>Para quitar los parámetros  
  
1.  Cree una aplicación de consola denominada `RemoveParameters`y, a continuación, reemplace `Program` con el código siguiente.  
  
    ```csharp  
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
  
2.  Coloque el cursor en el método `A`, en la declaración del método o la llamada al método.  
  
3.  Desde el **refactorizar** menú, seleccione **quitar parámetros** para mostrar la **quitar parámetros** cuadro de diálogo.  
  
     También puede escribir el método abreviado de teclado CTRL + R, V para mostrar la **quitar parámetros** cuadro de diálogo.  
  
     También puede hacer clic el cursor, seleccione **refactorizar**y, a continuación, haga clic en **quitar parámetros** para mostrar la **quitar parámetros** cuadro de diálogo.  
  
4.  Mediante el **parámetros** , a continuación, sitúe el cursor en `int i`y, a continuación, haga clic en **quitar**.  
  
5.  Haga clic en **Aceptar**.  
  
6.  En el **vista previa de cambios: quitar parámetros** cuadro de diálogo, haga clic en **aplicar**.  
  
## <a name="remarks"></a>Comentarios  
 Puede quitar parámetros de una declaración de método o una llamada al método. Sitúe el cursor en el nombre del método de declaración o delegado y quitar parámetros de invocación.  
  
> [!CAUTION]
>  Quitar permite parámetros para quitar un parámetro que se hace referencia en el cuerpo de los miembros, pero no quita las referencias a ese parámetro en el cuerpo del método. Esto puede producir errores de compilación en el código. Sin embargo, puede usar el **vista previa de cambios** cuadro de diálogo para revisar el código antes de ejecutar la operación de refactorización.  
  
 Si se modifica un parámetro que se va a quitar durante la llamada a un método, la eliminación del parámetro también quitará la modificación. Por ejemplo, si llama un método se cambia de  
  
```csharp  
MyMethod(param1++, param2);  
```  
  
 por  
  
```csharp  
MyMethod(param2);  
```  
  
 la operación de refactorización, `param1` no se incrementará.  
  
## <a name="see-also"></a>Vea también  
 [Refactorización (C#)](refactoring-csharp.md)