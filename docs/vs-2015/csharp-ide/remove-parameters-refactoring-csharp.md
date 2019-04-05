---
title: Quitar parámetros (refactorización, C#) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.remove
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8962dd95aa46ae75a2d214738e7713ae9da42534
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995683"
---
# <a name="remove-parameters-refactoring-c"></a>Quitar parámetros (Refactorización, C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Remove Parameters` es una operación de refactorización que proporciona una manera sencilla para quitar los parámetros de métodos, indizadores o delegados. Quite los cambios de los parámetros de la declaración; en todas las ubicaciones donde se llama al miembro, se quita el parámetro para reflejar la nueva declaración.  
  
 Realizar la operación de quitar parámetros, coloque primero el cursor en un método, indizador o delegado. Mientras el cursor está en posición, para invocar la quitar `Parameters` operación, haga clic en el **refactorizar** menú, utilice el método abreviado de teclado, o seleccione el comando en el menú contextual.  
  
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
  
2.  Coloque el cursor en el método `A`, ya sea en la declaración de método o la llamada al método.  
  
3.  Desde el **refactorizar** menú, seleccione **quitar parámetros** para mostrar el **quitar parámetros** cuadro de diálogo.  
  
     También puede escribir el método abreviado de teclado CTRL + R, V para mostrar el **quitar parámetros** cuadro de diálogo.  
  
     También puede haga clic en el cursor, apuntar a **refactorizar**y, a continuación, haga clic en **quitar parámetros** para mostrar el **quitar parámetros** cuadro de diálogo.  
  
4.  Mediante el **parámetros** , a continuación, coloque el cursor en `int i`y, a continuación, haga clic en **quitar**.  
  
5.  Haga clic en **Aceptar**.  
  
6.  En el **vista previa de cambios: quitar parámetros** cuadro de diálogo, haga clic en **aplicar**.  
  
## <a name="remarks"></a>Comentarios  
 Puede quitar los parámetros de una declaración de método o una llamada al método. Coloque el cursor en el nombre del delegado o de declaración de método y quitar los parámetros de invocación.  
  
> [!CAUTION]
>  Quitar permite parámetros para quitar un parámetro que se hace referencia en el cuerpo de miembro, pero no quita las referencias a ese parámetro en el cuerpo del método. Esto puede producir errores de compilación en el código. Sin embargo, puede usar el **vista previa de cambios** cuadro de diálogo para revisar el código antes de ejecutar la operación de refactorización.  
  
 Si se modifica un parámetro que se va a quitar durante la llamada a un método, la eliminación del parámetro también quitará la modificación. Por ejemplo, si llama un método se cambia de  
  
```csharp  
MyMethod(param1++, param2);  
```  
  
 por  
  
```csharp  
MyMethod(param2);  
```  
  
 mediante la operación de refactorización, `param1` no se incrementará.  
  
## <a name="see-also"></a>Vea también  
 [Refactorización (C#)](../csharp-ide/refactoring-csharp.md)