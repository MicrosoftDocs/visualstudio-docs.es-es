---
title: "Cómo: definir una instancia de método | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
ms.assetid: f0c8a686-c0de-414e-8de9-f228f59d1eb3
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 61338f61bf9fad301a62e7790ef5dc23b66a094d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-method-instance"></a>Cómo: Definir la instancia de un método
  Debe definir al menos una instancia de método para cada método en el modelo.  
  
 Agregar una instancia de método mediante el **detalles del método de BDC** ventana. Cuando se agrega la instancia de método, Visual Studio agrega un `<MethodInstance>` elemento en el XML del archivo del modelo en el proyecto. Para obtener más información sobre los atributos de un `<MethodInstance>` elemento, vea [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
### <a name="to-define-a-method-instance"></a>Para definir una instancia de método  
  
1.  En el **detalles del método de BDC** ventana, expanda el nodo de un método y, a continuación, expanda el **instancias** nodo.  
  
2.  En el **agregar una instancia del método** elija **crear instancia de buscador**.  
  
     Aparecerá una nueva instancia de método bajo la **instancias** nodo.  
  
3.  En la barra de menús, elija **vista**, elija **ventana propiedades**.  
  
4.  En el **propiedades** ventana, establezca las propiedades de la instancia de método. Para obtener más información sobre cada propiedad, vea [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
## <a name="see-also"></a>Vea también  
 [Información general de herramientas del diseño de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Cómo: agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: definir el Descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  