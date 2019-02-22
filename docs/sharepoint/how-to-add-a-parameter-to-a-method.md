---
title: Filtrar Agregar un parámetro a un método | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 1bec6daa92d4e5b58b97c47a45fa32c410aced5a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619959"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Filtrar Agregar un parámetro a un método
  Usar un parámetro para pasar información al método o para devolver información de un método. Todos los métodos deben tener al menos un parámetro. Para obtener más información sobre cómo diseñar un parámetro para admitir el tipo de método que se va a crear, ver [diseñar un modelo de conectividad de datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).

 Cuando se agrega un parámetro a un método, Visual Studio agrega el elemento de parámetro para el XML del archivo del modelo en el proyecto. Para obtener más información acerca de los atributos de un elemento de parámetro, vea [parámetro](http://go.microsoft.com/fwlink/?LinkId=169284).

### <a name="to-add-a-parameter-to-a-method"></a>Para agregar un parámetro a un método

1.  Agregue un método a una entidad.

2.  En la barra de menús, elija **vista** > **Other Windows** > **detalles del método de BDC**.

     El **detalles del método de BDC** abre la ventana. Para obtener más información, consulte [Introducción a las herramientas de diseño de modelo de BDC](../sharepoint/bdc-model-design-tools-overview.md).

3.  En el **detalles del método de BDC** , expanda el nodo del método y, a continuación, expanda el **parámetros** nodo.

4.  En el **agregar un parámetro** elija **crear parámetro**.

     Aparecerá un nuevo parámetro bajo la **parámetros** nodo.

5.  En la barra de menús, elija **vista** > **ventana propiedades**.

6.  En el **propiedades** ventana, establezca el **nombre** propiedad para cualquier nombre que tenga sentido. Por ejemplo, si el método devolverá a los clientes, podría denominar el método **GetCustomers**.

7.  En el **detalles del método de BDC** , abra la lista que aparece para la dirección del parámetro y, a continuación, elija **en**, **InOut**, **Out**, o **devolver**.

     Para obtener más información acerca de la dirección que elegir para el método de tipo que está creando, consulte [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).

8.  Modificar el descriptor de tipo del parámetro. Para obtener más información, vea [Cómo: Definir el descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Vea también
- [Introducción a las herramientas de diseño de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Cómo: Agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Cómo: Definir el descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Cómo: Definir una instancia de método](../sharepoint/how-to-define-a-method-instance.md)
- [Diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md)
