---
title: Controlar el color, el estilo de línea y otras propiedades de forma
description: Proporciona información sobre cómo controlar las propiedades de forma, como el color y el estilo de línea.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 836c77f3651b7686e9366fe75ea7922a248fd28f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389636"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Controlar el color, el estilo de línea y otras propiedades de forma

Algunas propiedades de forma, como el color, se pueden "exponer". Es decir, las propiedades se pueden vincular a una propiedad de dominio de la forma . Otros tienen que controlarse directamente.

## <a name="exposing-a-property"></a>Exposición de una propiedad
 Algunas propiedades de forma, como el color, se pueden vincular al valor de una propiedad de dominio.

 En definición de DSL, seleccione una forma, un conector o una clase de diagrama. En el menú contextual, elija **Agregar** expuesto y, a continuación, elija la propiedad que desee, como Color de relleno.

 La forma ahora tiene una propiedad de dominio que puede establecer en el código del programa o como usuario.

## <a name="dynamically-updating-an-exposed-property"></a>Actualización dinámica de una propiedad expuesta
 Normalmente, quiere que la propiedad expuesta dependa de otra propiedad. Por ejemplo, puede que desee que una forma se vuelva roja siempre que una propiedad de dominio determinada sea menor que cero. Para crear esta dependencia, cree una [regla](../modeling/rules-propagate-changes-within-the-model.md). Por ejemplo:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
namespace ExampleNamespace
{
 // Attribute associates the rule with class:
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class CarShapeAddRule : AddRule
 {
 // Override the abstract method:
 public override void ElementAdded(ElementAddedEventArgs e)
 {
 base.ElementAdded(e);
 CarShape shape = e.ModelElement as CarShape;
 Store store = shape.Store;
 // Ignore this call if we're currently loading a model:
 if (store.TransactionManager.CurrentTransaction.IsSerializing)
  return;
 Car car = shape.ModelElement as Car;
 // Code here propagates change as required - for example:
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;
 }
}
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
 protected override Type[] GetCustomDomainModelTypes()
 {
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
  types.Add(typeof(CarShapeAddRule));
  // If you add more rules, list them here.
  return types.ToArray();
 }
 }
}
```