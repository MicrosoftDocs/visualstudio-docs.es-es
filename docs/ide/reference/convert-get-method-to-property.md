---
title: Conversión del método Get en propiedad y de propiedad en el método Get
ms.date: 01/26/2018
ms.topic: reference
ms.devlang: csharp
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 87fc623f781c54267fa70da7c5d2a341823e35ae
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263098"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Refactorizaciones de conversión del método Get en propiedad y de propiedad en método Get

Estas refactorizaciones se aplican a:

- C#

## <a name="convert-get-method-to-property"></a>Conversión del método Get en una propiedad

**Qué:** Permite convertir un método Get en una propiedad (y, opcionalmente, el método Set).

**Cuándo:** Hay un método Get que no contiene ninguna lógica.

### <a name="how-to"></a>Procedimiento

1. Coloque el cursor en el nombre del método Get.

1. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Replace method with property** (Reemplazar método por propiedad) en el menú emergente de la ventana Vista previa.
   - **Mouse**
      - Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Replace method with property** (Reemplazar método por propiedad) en el menú emergente de la ventana Vista previa.

1. (Opcional) Si tiene un método Set, también puede convertirlo en este momento seleccionando **Replace Get method and Set method with property** (Reemplazar método Get y método Set por propiedad).

1. Si está satisfecho con el cambio en la vista previa del código, presione **Entrar** o haga clic en la solución en el menú y los cambios se confirmarán.

Ejemplo:

```csharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

## <a name="convert-property-to-get-method"></a>Convertir propiedad a método Get

**Qué:** Permite convertir una propiedad en un método Get

**Cuándo:** Hay una propiedad que implica más que establecer y obtener un valor de inmediato

### <a name="how-to"></a>Procedimiento

1. Coloque el cursor en el nombre del método Get.

1. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Replace property with methods** (Reemplazar propiedad por métodos) en el menú emergente de la ventana Vista previa.
   - **Mouse**
      - Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Replace property with methods** (Reemplazar propiedad por métodos) en el menú emergente de la ventana Vista previa.

1. Si está satisfecho con el cambio en la vista previa del código, presione **Entrar** o haga clic en la solución en el menú y los cambios se confirmarán.

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)