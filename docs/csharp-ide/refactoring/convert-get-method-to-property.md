---
title: "Convertir el método Get en propiedad - refactorización (C#) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
f1_keywords: vs.csharp.refactoring.convertmethodtoproperty
dev_langs: csharp
ms.openlocfilehash: d034b8835caf0a5e56a9ef32599cf9197f1e3e16
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/29/2017
---
# <a name="convert-get-method-to-property--convert-property-to-get-method"></a>Convertir el método Get para la propiedad / convertir la propiedad en Get (método)
## <a name="convert-get-method-to-property"></a>Convertir el método Get para la propiedad
**¿Qué:** le permite convertir un método Get en una propiedad (y, opcionalmente, el método Set) y viceversa.

**Cuándo:** tiene un método Get, que no contiene ninguna lógica.

**Cómo:**

1. Coloque el cursor en el nombre del método Get.

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **Replace (método) con la propiedad** de la ventana emergente de ventana de vista previa. Si tiene un método Set, también puede convertir el método Set en este momento seleccionando **método reemplazar Get y Set (método) con la propiedad**.
   * **Mouse**
     * Haga clic en el código, seleccione la **acciones rápidas y refactorizaciones** menú y seleccione **Replace (método) con la propiedad** de la ventana emergente de ventana de vista previa. Si tiene un método Set, también puede convertir el método Set en este momento seleccionando **método reemplazar Get y Set (método) con la propiedad**.

1. Si está satisfecho con el cambio en la vista previa del código, presione **ENTRAR** o haga clic en la solución en el menú y los cambios se confirmarán.

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

## <a name="convert-property-to-get-method"></a>Convertir la propiedad en Get (método)
**¿Qué:** le permite convertir una propiedad en un método Get

**Cuándo:** tiene una propiedad que implica establecer u obtener un valor de más de inmediato 

**Cómo:**

1. Coloque el cursor en el nombre del método Get.

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **reemplazar propiedades con métodos** desde la ventana emergente de ventana de vista previa.
   * **Mouse**
     * Haga clic en el código, seleccione la **acciones rápidas y refactorizaciones** menú y seleccione **reemplazar propiedades con métodos** desde la ventana emergente de ventana de vista previa.

1. Si está satisfecho con el cambio en la vista previa del código, presione **ENTRAR** o haga clic en la solución en el menú y los cambios se confirmarán.

## <a name="see-also"></a>Vea también  
[Refactorización (C#)](../refactoring-csharp.md)  
[Vista previa de cambios](../../ide/preview-changes.md)