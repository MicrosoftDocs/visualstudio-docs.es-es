---
title: Controlar el Color, estilo de línea y otras propiedades de forma | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c06d0066-24aa-4c65-b91c-c2089b81ec8d
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: b5694e81721bcc16b13c1857a07072fcaef00a08
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285485"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Controlar el color, el estilo de línea y otras propiedades de forma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Algunas propiedades de la forma como color puede ser 'expuesto:', es decir, vinculan a una propiedad de dominio de la forma. Otros tienen que se puede controlar directamente.  
  
## <a name="exposing-a-property"></a>Exponer una propiedad  
 Algunas propiedades de la forma como color se pueden vincular al valor de una propiedad de dominio.  
  
 En la definición de DSL, seleccione una forma, conector o clase del diagrama. En el menú contextual, elija **agregar expuestos**y, a continuación, elija la propiedad que desee, como el Color de relleno.  
  
 Ahora, la forma tiene una propiedad de dominio que se puede establecer en el código de programa o como un usuario.  
  
## <a name="dynamically-updating-an-exposed-property"></a>Actualizar dinámicamente una propiedad expuesta  
 Normalmente, desea hacer que la propiedad expuesta que dependa de otra propiedad. Por ejemplo, es posible que desee una forma de color rojo, siempre que una propiedad de dominio en particular es menor que cero. Para que esta dependencia, cree un [regla](../modeling/rules-propagate-changes-within-the-model.md). Por ejemplo:  
  
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



