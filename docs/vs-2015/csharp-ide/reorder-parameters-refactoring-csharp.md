---
title: Reordenar parámetros de refactorización (C#) | Documentos de Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9bec38846f7703ff3958aa1c0fcc9a660a5e080d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997005"
---
# <a name="reorder-parameters-refactoring-c"></a>Reordenar parámetros de refactorización (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` es Visual C# operación de refactorización que proporciona una manera fácil de cambiar el orden de los parámetros de métodos, indizadores y delegados. `Reorder Parameters` cambia la declaración, y en todas las ubicaciones donde se llama al miembro, los parámetros se reorganizan para reflejar el nuevo orden.  
  
 Para realizar la `Reorder Parameters` operación, coloque el cursor en o junto a un método, indizador o delegado. Cuando el cursor está en posición, invocar el `Reorder Parameters` operación presionando el método abreviado de teclado, o haga clic en el comando en el menú contextual.  
  
> [!NOTE]
>  No puede reordenar el primer parámetro de un método de extensión.  
  
### <a name="to-reorder-parameters"></a>Reordenar parámetros  
  
1.  Crear una biblioteca de clases denominada `ReorderParameters`y, a continuación, reemplace `Class1` con el siguiente código de ejemplo.  
  
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
  
2.  Coloque el cursor en `MethodB`, ya sea en la declaración de método o la llamada al método.  
  
3.  En el **refactorizar** menú, haga clic en **Reordenar parámetros**.  
  
     El **Reordenar parámetros** aparece el cuadro de diálogo.  
  
4.  En el **Reordenar parámetros** cuadro de diálogo, seleccione `int i` en el **parámetros** lista y, a continuación, haga clic en el botón de abajo.  
  
     Como alternativa, puede arrastrar `int i` después `bool b` en el **parámetros** lista.  
  
5.  En el **Reordenar parámetros** cuadro de diálogo, haga clic en **Aceptar**.  
  
     Si el **vista previa de cambios de referencia** opción está seleccionada en el **Reordenar parámetros** cuadro de diálogo, el **vista previa de cambios - Reordenar parámetros** aparecerá el cuadro de diálogo. Proporciona una vista previa de los cambios en la lista de parámetros `MethodB` en la firma y la llamada al método.  
  
    1.  Si el **vista previa de cambios - Reordenar parámetros** aparece el cuadro de diálogo, haga clic en **aplicar**.  
  
         En este ejemplo, la declaración de método y todas la llamada al método sitios para `MethodB` se actualizan.  
  
## <a name="remarks"></a>Comentarios  
 Puede reordenar los parámetros de una declaración de método o una llamada al método. Coloque el cursor en o junto a la declaración de método o delegado, pero no en el cuerpo.  
  
## <a name="see-also"></a>Vea también  
 [Refactorización (C#)](../csharp-ide/refactoring-csharp.md)