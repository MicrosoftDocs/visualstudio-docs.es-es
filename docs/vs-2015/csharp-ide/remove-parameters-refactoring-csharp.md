---
title: Quitar parámetros (C#refactorización) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40c373c3575f007952143e29c8dfc2cfac3d080f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667488"
---
# <a name="remove-parameters-refactoring-c"></a>Quitar parámetros (Refactorización, C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Remove Parameters` es una operación de refactorización que proporciona una manera sencilla de quitar parámetros de métodos, indizadores o delegados. Quitar parámetros cambia la declaración; en cualquier ubicación en la que se llame al miembro, el parámetro se quita para reflejar la nueva declaración.

 La operación quitar parámetros se realiza colocando primero el cursor en un método, indexador o delegado. Mientras el cursor está en posición, para invocar la operación quitar `Parameters`, haga clic en el menú **refactorizar** , presione el método abreviado de teclado o seleccione el comando en el menú contextual.

> [!NOTE]
> No se puede quitar el primer parámetro de un método de extensión.

### <a name="to-remove-parameters"></a>Para quitar parámetros

1. Cree una aplicación de consola denominada `RemoveParameters` y, a continuación, reemplace `Program` por el código siguiente.

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

2. Coloque el cursor en el `A` del método, ya sea en la declaración del método o en la llamada al método.

3. En el menú **refactorizar** , seleccione **quitar parámetros** para mostrar el cuadro de diálogo **quitar parámetros** .

     También puede escribir el método abreviado de teclado CTRL + R, V para mostrar el cuadro de diálogo **quitar parámetros** .

     También puede hacer clic con el botón secundario en el cursor, seleccionar **refactorizar**y, a continuación, hacer clic en **quitar parámetros** para mostrar el cuadro de diálogo **quitar parámetros** .

4. En el campo **Parameters** , coloque el cursor en `int i` y, a continuación, haga clic en **quitar**.

5. Haga clic en **Aceptar**.

6. En el cuadro de diálogo **vista previa de los cambios: quitar parámetros** , haga clic en **aplicar**.

## <a name="remarks"></a>Comentarios
 Puede quitar parámetros de una declaración de método o una llamada al método. Coloque el cursor en la declaración de método o nombre de delegado e invoque parámetros de eliminación.

> [!CAUTION]
> Quitar parámetros permite quitar un parámetro al que se hace referencia en el cuerpo del miembro, pero no quita las referencias a ese parámetro en el cuerpo del método. Esto puede introducir errores de compilación en el código. Sin embargo, puede usar el cuadro de diálogo **vista previa de los cambios** para revisar el código antes de ejecutar la operación de refactorización.

 Si se modifica un parámetro que se va a quitar durante la llamada a un método, la eliminación del parámetro también quitará la modificación. Por ejemplo, si se cambia una llamada al método de

```csharp
MyMethod(param1++, param2);
```

 por

```csharp
MyMethod(param2);
```

 mediante la operación de refactorización, `param1` no se incrementarán.

## <a name="see-also"></a>Vea también
 [Refactorización (C#)](../csharp-ide/refactoring-csharp.md)