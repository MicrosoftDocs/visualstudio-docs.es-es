---
title: "Cómo: agregar un parámetro a un método | Documentos de Microsoft"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
ms.assetid: c5b6fd32-bf85-4b2a-a01e-f9199f0fb26e
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f6810d69628c66a011123250b8e0efb8622f0be7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Cómo: Agregar un parámetro a un método
  Usar un parámetro para pasar información en el método o para devolver información de un método. Todos los métodos deben tener al menos un parámetro. Para obtener más información sobre cómo diseñar un parámetro para admitir el tipo de método que se va a crear, vea [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Cuando se agrega un parámetro a un método, Visual Studio agrega el `<Parameter>` elemento en el XML del archivo del modelo en el proyecto. Para obtener más información sobre los atributos de un `<Parameter>` elemento, vea [parámetro](http://go.microsoft.com/fwlink/?LinkId=169284).  
  
### <a name="to-add-a-parameter-to-a-method"></a>Para agregar un parámetro a un método  
  
1.  Agregar un método a una entidad.  
  
2.  En la barra de menús, elija **vista**, **otras ventanas**, **detalles del método de BDC**.  
  
     El **detalles del método de BDC** abre la ventana. Para obtener más información, consulte [herramientas información general del diseño de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  En el **detalles del método de BDC** ventana, expanda el nodo del método y, a continuación, expanda el **parámetros** nodo.  
  
4.  En el **agregar un parámetro** elija **crear parámetro**.  
  
     Aparece un nuevo parámetro debajo la **parámetros** nodo.  
  
5.  En la barra de menús, elija **vista**, **ventana propiedades**.  
  
6.  En el **propiedades** ventana, establezca el **nombre** propiedad a cualquier nombre que tenga sentido. Por ejemplo, si el método devolverá los clientes, podría denominar el método **GetCustomers**.  
  
7.  En el **detalles del método de BDC** ventana, abra la lista que aparece en la dirección del parámetro y, a continuación, elija **en**, **InOut**, **Out**, o **devolver**.  
  
     Para obtener más información sobre la dirección que elegir para el método de tipo que está creando, consulte [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
8.  Modificar el descriptor de tipo del parámetro. Para obtener más información, consulte [Cómo: definir el Descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general de herramientas del diseño de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Cómo: agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Cómo: definir el Descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Cómo: definir una instancia de método](../sharepoint/how-to-define-a-method-instance.md)   
 [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  