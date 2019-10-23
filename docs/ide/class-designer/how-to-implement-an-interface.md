---
title: Procedimiento Implementar una interfaz (Diseñador de clases)
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf03046abcf79933044cfb01bf079aee64d09077
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647716"
---
# <a name="how-to-implement-an-interface-in-class-designer"></a>Procedimiento Implementar una interfaz en el Diseñador de clases

En el **Diseñador de clases**, puede implementar una interfaz en el diagrama de clases si la conecta a una clase que proporcione código para los métodos de interfaz. El **Diseñador de clases** genera una implementación de interfaz y muestra la relación entre la interfaz y la clase como una relación de herencia. Para implementar una interfaz, dibuje una línea de herencia entre la interfaz y la clase, o bien arrastre la interfaz desde la Vista de clases.

> [!TIP]
> Puede crear interfaces de la misma manera que se crean otros tipos. Si la interfaz existe pero no aparece en el diagrama de clases, primero muéstrela. Para obtener más información, vea [Cómo: Crear tipos con el Diseñador de clases](how-to-create-types.md) y [Cómo: Ver los tipos existentes](how-to-view-existing-types.md).

## <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Para implementar una interfaz mediante el dibujo de una línea de herencia

1. En el diagrama de clases, muestre la interfaz y la clase que implementará la interfaz.

2. Dibuje una línea de herencia entre la clase y la interfaz.

     Aparece un círculo conectado a la clase y una etiqueta con el nombre de interfaz identifica la relación de herencia. Visual Studio genera código auxiliar para todos los miembros de interfaz.

Para obtener más información, vea [Cómo: Crear herencia entre tipos](how-to-create-inheritance-between-types.md).

## <a name="to-implement-an-interface-from-the-class-view-window"></a>Para implementar una interfaz desde la ventana Vista de clases

1. En el diagrama de clases, muestre la clase que quiere que implemente la interfaz.

2. Abra la **Vista de clases** y busque la interfaz.

    > [!TIP]
    > Si la **Vista de clases** no está abierta, abra la **Vista de clases** desde el menú **Ver** o presione **Ctrl**+**Mayús**+**C**.

3. Arrastre el nodo de interfaz a la forma de clase en el diagrama.

     Aparece un círculo conectado a la clase y una etiqueta con el nombre de interfaz identifica la relación de herencia. Visual Studio genera código auxiliar para todos los miembros de interfaz; en este momento, se implementa la interfaz.

## <a name="see-also"></a>Vea también

- [Cómo: Crear tipos con el Diseñador de clases](how-to-create-types.md)
- [Cómo: Ver tipos existentes](how-to-view-existing-types.md)
- [Cómo: Crear herencia entre tipos](how-to-create-inheritance-between-types.md)
- [Refactorización de clases y tipos](refactoring-classes-and-types.md)