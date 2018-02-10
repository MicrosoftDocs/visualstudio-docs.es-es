---
title: "Controlar el Color, estilo de línea y otras propiedades de forma | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5903c6cc79e637514b75c9e44cb4cbe5c0342ee7
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Controlar el color, el estilo de línea y otras propiedades de forma
Algunas propiedades de forma como color puede 'expondrán': es decir, vinculada a una propiedad de dominio de la forma. Otras personas deben controlarse directamente.  
  
## <a name="exposing-a-property"></a>Exponer una propiedad  
 Algunas propiedades de forma como color se pueden vincular al valor de una propiedad de dominio.  
  
 En la definición DSL, seleccione una forma, conector o clase del diagrama. En el menú contextual, elija **agregar expone**y, a continuación, elija la propiedad que desee, como el Color de relleno.  
  
 La forma ahora tiene una propiedad de dominio que se puede establecer en el código de programa o como un usuario.  
  
## <a name="dynamically-updating-an-exposed-property"></a>Actualizar dinámicamente una propiedad expuesta  
 Normalmente desea hacer que la propiedad expuesta dependa de otra propiedad. Por ejemplo, conviene una forma de color rojo, siempre que una propiedad de dominio en particular es menor que cero. Para realizar esta dependencia, crearía una [regla](../modeling/rules-propagate-changes-within-the-model.md). Por ejemplo:  
  
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