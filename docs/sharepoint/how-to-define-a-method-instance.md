---
title: Procedimiento Definir una instancia de método | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 630709bd674677d636abe471b8ff63b7f7339abc
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867928"
---
# <a name="how-to-define-a-method-instance"></a>Procedimiento Definir una instancia de método
  Debe definir al menos una instancia de método para cada método en el modelo.  
  
 Agregar una instancia de método con el **detalles del método de BDC** ventana. Cuando se agrega a la instancia de método, Visual Studio agrega un `<MethodInstance>` elemento al XML del archivo del modelo en el proyecto. Para obtener más información acerca de los atributos de un `<MethodInstance>` elemento, vea [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
### <a name="to-define-a-method-instance"></a>Para definir una instancia de método  
  
1.  En el **detalles del método de BDC** , expanda el nodo de un método y, a continuación, expanda el **instancias** nodo.  
  
2.  En el **agregar una instancia de método** elija **crear instancia de Finder**.  
  
     Aparecerá una nueva instancia de método bajo el **instancias** nodo.  
  
3.  En la barra de menús, elija **vista** > **ventana propiedades**.  
  
4.  En el **propiedades** ventana, establezca las propiedades de la instancia de método. Para obtener más información sobre cada propiedad, vea [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
## <a name="see-also"></a>Vea también
 [Introducción a las herramientas de diseño de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Cómo: Agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Cómo: Agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: Definir el descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md)  
