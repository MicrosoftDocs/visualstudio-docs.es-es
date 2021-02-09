---
title: 'Cómo: crear una asociación entre entidades | Microsoft Docs'
description: Defina las relaciones entre entidades en el modelo de conectividad a datos profesionales (BDC) mediante la creación de asociaciones en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- AssociationGroupTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e726e8b5702a656b340401c9a2db26e40be1a37d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925567"
---
# <a name="how-to-create-an-association-between-entities"></a>Cómo: crear una asociación entre entidades
  Puede definir las relaciones entre las entidades del modelo de conectividad a datos profesionales (BDC) mediante la creación de asociaciones. Visual Studio genera métodos que proporcionan a los consumidores del modelo información sobre cada asociación. Estos métodos pueden ser consumidos por elementos Web, listas o aplicaciones personalizadas de SharePoint para mostrar las relaciones de datos en una interfaz de usuario (UI).

 Puede crear dos tipos de asociaciones en el diseñador de BDC: asociaciones basadas en claves externas y asociaciones sin clave externa. Para obtener más información, vea [crear una asociación entre entidades](../sharepoint/creating-an-association-between-entities.md).

### <a name="to-create-an-association-between-entities"></a>Para crear una asociación entre entidades

1. En la pestaña **BusinessDataConnectivity** del **cuadro de herramientas**, elija el elemento de **Asociación** .

2. En el diseñador de BDC, elija la entidad de origen y, a continuación, elija la entidad de destino.

     Aparece el **Editor de asociaciones** .

3. Si desea crear una asociación basada en claves externas, active la casilla **es una asociación de clave externa** .

    1. En la columna **ID. de origen** de la tabla de **asignación de identificadores** , elija el identificador situado junto a cada descriptor de tipo coincidente que aparece en la columna **campo** .

         Por ejemplo, en la columna ID. de **origen** , seleccione `ContactID` junto al `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` descriptor de tipos y el `ReadItem.salesOrder.SalesOrder.ContactID` descriptor de tipos.

4. Si desea crear una asociación de entrada sin llave externa, desactive la casilla **es la Asociación de clave externa** .

5. Elija el botón **Aceptar** .

6. En el diseñador de BDC, se muestra una línea que representa la asociación entre la entidad de origen y la entidad de destino.

     Visual Studio agrega un método de navegador de asociaciones a la clase de servicio de la entidad de destino y la clase de servicio de la entidad de origen. Para obtener más información acerca de los métodos de navegación por asociaciones, vea [operaciones admitidas](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14)).

7. En el método de navegador de asociaciones de la entidad de origen, agregue código que devuelva una colección de entidades de destino.

8. En el método del navegador de asociaciones de la entidad de destino, agregue el código que devuelve la entidad de origen relacionada.

     Para obtener ejemplos de métodos del navegador de asociaciones, vea [crear una asociación entre entidades](../sharepoint/creating-an-association-between-entities.md).

## <a name="see-also"></a>Vea también
- [Crear una asociación entre entidades](../sharepoint/creating-an-association-between-entities.md)
- [Diseño de un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Cómo: agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Cómo: agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Cómo: agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Cómo: agregar un método de eliminación](../sharepoint/how-to-add-a-deleter-method.md)
- [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Introducción a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Cómo: agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Cómo: definir una instancia de método](../sharepoint/how-to-define-a-method-instance.md)
- [Cómo: definir el descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Tutorial: crear una lista externa en SharePoint con datos económicos](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
