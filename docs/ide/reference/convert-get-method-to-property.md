---
title: Conversión del método Get en y desde una propiedad
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para convertir un método Get (y, opcionalmente, el método Set) en una propiedad.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
ms.devlang: csharp
author: mikadumont
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 3aa7831c56068c826c9bbecf97d7115331243251
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039828"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Refactorizaciones de conversión del método Get en propiedad y de propiedad en método Get

Estas refactorizaciones se aplican a:

- C#

- Visual Basic

## <a name="convert-get-method-to-property"></a>Conversión del método Get en una propiedad

**Qué:** le permite convertir un método Get en una propiedad (y, opcionalmente, el método Set).

**Cuándo:** Tiene un método Get que no contiene ninguna lógica.

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

**Qué:** Le permite convertir una propiedad en un método Get

**Cuándo:** Tiene una propiedad que implica más que establecer y obtener un valor de inmediato

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
