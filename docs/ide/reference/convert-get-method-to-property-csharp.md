---
title: "Conversión del método Get en propiedad y conversión de una propiedad en un método Get en C# | Microsoft Docs"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
f1_keywords: vs.csharp.refactoring.convertmethodtoproperty
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: a23af31c5099908ed0b6fed07404216a57975f75
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="convert-get-method-to-property--convert-property-to-get-method"></a>Conversión del método Get en propiedad y de propiedad en el método Get

## <a name="convert-get-method-to-property"></a>Conversión del método Get en una propiedad

**Qué:** le permite convertir un método Get en una propiedad (y, opcionalmente, el método Set) y viceversa.

**Cuándo:** Tiene un método Get que no contiene ninguna lógica.

**Cómo**:

1. Coloque el cursor en el nombre del método Get.

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Replace method with property** (Reemplazar método por propiedad) en el menú emergente de la ventana Vista previa. Si tiene un método Set, también puede convertir el método Set en este momento seleccionando **Replace Get method and Set method with property** (Reemplazar método Get y método Set por propiedad).
   * **Mouse**
     * Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Replace method with property** (Reemplazar método por propiedad) en el menú emergente de la ventana Vista previa. Si tiene un método Set, también puede convertir el método Set en este momento seleccionando **Replace Get method and Set method with property** (Reemplazar método Get y método Set por propiedad).

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

**Cómo**:

1. Coloque el cursor en el nombre del método Get.

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Replace property with methods** (Reemplazar propiedad por métodos) en el menú emergente de la ventana Vista previa.
   * **Mouse**
     * Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Replace property with methods** (Reemplazar propiedad por métodos) en el menú emergente de la ventana Vista previa.

1. Si está satisfecho con el cambio en la vista previa del código, presione **Entrar** o haga clic en la solución en el menú y los cambios se confirmarán.

## <a name="see-also"></a>Vea también

[Refactorización](../refactoring-in-visual-studio.md)  
[Vista previa de cambios](../../ide/preview-changes.md)