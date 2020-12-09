---
title: 'Cómo: agregar un parámetro a un método | Microsoft Docs'
description: Sepa cómo agregar un parámetro a un método de conectividad a datos profesionales (BDC), que le permite pasar información al método o devolver información del método.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 179109ff4c0def002dac45887fe9491196a70d3e
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915406"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Cómo: agregar un parámetro a un método
  Use un parámetro para pasar información al método o para devolver información de un método. Todos los métodos deben tener al menos un parámetro. Para obtener más información sobre cómo diseñar un parámetro para admitir el tipo de método que desea crear, vea [diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).

 Cuando se agrega un parámetro a un método, Visual Studio agrega el elemento de parámetro al XML del archivo de modelo en el proyecto. Para obtener más información sobre los atributos de un elemento Parameter, consulte [Parameter](/previous-versions/office/developer/sharepoint-2010/ee557705(v=office.14)).

### <a name="to-add-a-parameter-to-a-method"></a>Para agregar un parámetro a un método

1. Agregue un método a una entidad.

2. En la barra de menús, elija **Ver**  >  **otros**  >  **detalles del método BDC** de Windows.

     Se abre la ventana **detalles del método de BDC** . Para obtener más información, vea [información general sobre las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. En la ventana **detalles del método de BDC** , expanda el nodo del método y, a continuación, expanda el nodo **parámetros** .

4. En la lista **Agregar un parámetro** , elija **crear parámetro**.

     Aparece un nuevo parámetro debajo del nodo **parámetros** .

5. En la barra de menús, elija **Ver**  >  **ventana Propiedades**.

6. En la ventana **propiedades** , establezca la propiedad **nombre** en cualquier nombre que tenga sentido. Por ejemplo, si el método va a devolver clientes, podría asignar el nombre al método **GetCustomers**.

7. En la **ventana detalles del método de BDC** , abra la lista que aparece para la dirección del parámetro y, a continuación, elija **in**, **INOUT**, **out** o **Return**.

     Para obtener más información sobre la dirección que se debe elegir para el método de tipo que se está creando, vea [diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).

8. Modifique el descriptor de tipo del parámetro. Para obtener más información, vea [Cómo: definir el descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Consulte también
- [Introducción a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Cómo: agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Cómo: definir el descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Cómo: definir una instancia de método](../sharepoint/how-to-define-a-method-instance.md)
- [Diseño de un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)
