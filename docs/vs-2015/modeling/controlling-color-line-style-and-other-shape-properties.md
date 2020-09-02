---
title: Controlar el color, el estilo de línea y otras propiedades de forma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: c06d0066-24aa-4c65-b91c-c2089b81ec8d
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5d296f5ab3f5c584558b373b57c175fb2bacef4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667855"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Controlar el color, el estilo de línea y otras propiedades de forma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Algunas propiedades de forma, como el color, se pueden "exponer", es decir, están vinculadas a una propiedad de dominio de la forma. Otros deben controlarse directamente.

## <a name="exposing-a-property"></a>Exponer una propiedad
 Algunas propiedades de forma, como el color, se pueden vincular al valor de una propiedad de dominio.

 En la definición de DSL, seleccione una forma, conector o clase de diagrama. En el menú contextual, elija **Agregar expuesto**y, a continuación, elija la propiedad que desee, como color de relleno.

 La forma ahora tiene una propiedad de dominio que se puede establecer en el código del programa o como usuario.

## <a name="dynamically-updating-an-exposed-property"></a>Actualizar dinámicamente una propiedad expuesta
 Normalmente, desea que la propiedad expuesta dependa de otra propiedad. Por ejemplo, puede que desee que una forma se convierta en rojo siempre que una propiedad de dominio determinada sea menor que cero. Para hacer esta dependencia, cree una [regla](../modeling/rules-propagate-changes-within-the-model.md). Por ejemplo:

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
