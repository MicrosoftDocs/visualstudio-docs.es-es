---
title: 'Cómo: definir una instancia de método | Microsoft Docs'
description: Aprenda a definir una instancia de método para un método en el modelo de conectividad a datos profesionales (BDC).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 055193123f99825027238166d762ce54b288d716
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885669"
---
# <a name="how-to-define-a-method-instance"></a>Cómo: definir una instancia de método
  Debe definir al menos una instancia de método para cada método del modelo.

 Agregue una instancia de método mediante la ventana **detalles del método de BDC** . Al agregar la instancia de método, Visual Studio agrega un `<MethodInstance>` elemento al XML del archivo de modelo en el proyecto. Para obtener más información sobre los atributos de un `<MethodInstance>` elemento, vea [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

### <a name="to-define-a-method-instance"></a>Para definir una instancia de método

1. En la ventana **detalles del método de BDC** , expanda el nodo de un método y, a continuación, expanda el nodo **instancias** .

2. En la lista **Agregar instancia de método** , elija **Crear instancia de Finder**.

     Aparece una nueva instancia del método debajo del nodo **instancias** .

3. En la barra de menús, elija **Ver**  >  **ventana Propiedades**.

4. En la ventana **propiedades** , establezca las propiedades de la instancia de método. Para obtener más información sobre cada propiedad, vea [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

## <a name="see-also"></a>Vea también
- [Introducción a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Cómo: agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Cómo: definir el descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Diseño de un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)
