---
redirect_url: /visualstudio/csharp-ide/refactoring/change-method-signature
title: "Reordenar parámetros de refactorización (C#) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.csharp.refactoring.reorder
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3469e9ae7101c9e180fba5558fce389c6dfcc72d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="reorder-parameters-refactoring-c"></a>Reordenar parámetros de refactorización (C#)
`Reorder Parameters`es Visual C# operación de refactorización que proporciona una manera sencilla para cambiar el orden de los parámetros de métodos, indizadores y delegados. `Reorder Parameters`cambia la declaración, y en todas las ubicaciones donde se llama al miembro, los parámetros se reorganizan para reflejar el nuevo orden.  
  
 Para realizar la `Reorder Parameters` operación, coloque el cursor en o junto a un método, indizador o delegado. Cuando el cursor está en posición, invoque la `Reorder Parameters` operación presionando el método abreviado de teclado o haciendo clic en el comando en el menú contextual.  
  
> [!NOTE]
>  No puede reordenar el primer parámetro de un método de extensión.  
  
### <a name="to-reorder-parameters"></a>Para volver a ordenar parámetros  
  
1.  Crear una biblioteca de clases denominada `ReorderParameters`y, a continuación, reemplace `Class1` con el código de ejemplo siguiente.  
  
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
  
2.  Coloque el cursor en `MethodB`, en la declaración del método o la llamada al método.  
  
3.  En el **refactorizar** menú, haga clic en **Reordenar parámetros**.  
  
     El **Reordenar parámetros** aparece el cuadro de diálogo.  
  
4.  En el **Reordenar parámetros** cuadro de diálogo, seleccione `int i` en el **parámetros** lista y, a continuación, haga clic en el botón abajo.  
  
     Como alternativa, puede arrastrar `int i` después `bool b` en el **parámetros** lista.  
  
5.  En el **Reordenar parámetros** cuadro de diálogo, haga clic en **Aceptar**.  
  
     Si el **vista previa de cambios de referencia** opción está seleccionada en el **Reordenar parámetros** cuadro de diálogo, el **vista previa de cambios - Reordenar parámetros** aparecerá el cuadro de diálogo. Proporciona una vista previa de los cambios en la lista de parámetros para `MethodB` en la firma y la llamada al método.  
  
    1.  Si el **vista previa de cambios - Reordenar parámetros** aparece el cuadro de diálogo, haga clic en **aplicar**.  
  
         En este ejemplo, la declaración del método y el método de todos los sitios para de llamada `MethodB` se actualizan.  
  
## <a name="remarks"></a>Comentarios  
 Puede reordenar los parámetros de una declaración de método o una llamada al método. Coloque el cursor en o junto a la declaración de método o el delegado, pero no en el cuerpo.  
  
## <a name="see-also"></a>Vea también  
 [Refactorización (C#)](refactoring-csharp.md)