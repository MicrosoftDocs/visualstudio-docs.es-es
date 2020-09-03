---
title: Reordenación de los parámetros de refactorización (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e39564fb108b63859620e2c4a650608cdf1e7e82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673148"
---
# <a name="reorder-parameters-refactoring-c"></a>Reordenar parámetros de refactorización (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` es una operación de refactorización de Visual C# que proporciona una manera sencilla de cambiar el orden de los parámetros de los métodos, indizadores y delegados. `Reorder Parameters` cambia la declaración y, en cualquier ubicación en la que se llame al miembro, los parámetros se reorganizan para reflejar el nuevo pedido.

 Para realizar la `Reorder Parameters` operación, coloque el cursor en o junto a un método, indizador o delegado. Cuando el cursor esté en posición, invoque la `Reorder Parameters` operación presionando el método abreviado de teclado o haciendo clic en el comando del menú contextual.

> [!NOTE]
> No se puede reordenar el primer parámetro de un método de extensión.

### <a name="to-reorder-parameters"></a>Para reordenar los parámetros

1. Cree una biblioteca de clases denominada `ReorderParameters` y, a continuación, reemplace `Class1` con el siguiente código de ejemplo.

    ```csharp
    class ProtoClassA
    {
        // Invoke on 'MethodB'.
        public void MethodB(int i, bool b) { }
    }

    class ProtoClassC
    {
        void D()
        {
            ProtoClassA MyClassA = new ProtoClassA();

            // Invoke on 'MethodB'.
            MyClassA.MethodB(0, false);
        }
    }
    ```

2. Coloque el cursor en `MethodB` , ya sea en la declaración del método o en la llamada al método.

3. En el menú **refactorizar** , haga clic en **Reordenar parámetros**.

     Aparecerá el cuadro de diálogo **Reordenar parámetros** .

4. En el cuadro de diálogo **Reordenar parámetros** , seleccione `int i` en la lista de **parámetros** y, a continuación, haga clic en el botón abajo.

     Como alternativa, puede arrastrar `int i` después `bool b` de en la lista de **parámetros** .

5. En el cuadro de diálogo **Reordenar parámetros** , haga clic en **Aceptar**.

     Si la opción **vista previa de los cambios de referencia** está seleccionada en el cuadro de diálogo **Reordenar parámetros** , aparecerá el cuadro de diálogo **vista previa de los cambios: reordenar** . Proporciona una vista previa de los cambios en la lista de parámetros de `MethodB` en la firma y en la llamada al método.

    1. Si aparece el cuadro de diálogo **vista previa de los cambios y reordenar los parámetros** , haga clic en **aplicar**.

         En este ejemplo, se actualizan la declaración de método y todos los sitios de llamada de método para `MethodB` .

## <a name="remarks"></a>Observaciones
 Puede reordenar los parámetros de una declaración de método o una llamada al método. Coloque el cursor en o junto a la declaración de método o delegado, pero no en el cuerpo.

## <a name="see-also"></a>Consulte también
 [Refactorización (C#)](../csharp-ide/refactoring-csharp.md)