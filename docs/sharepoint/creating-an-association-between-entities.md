---
title: Crear una asociación entre entidades | Microsoft Docs
description: Cree una asociación entre las entidades del modelo de conectividad a datos profesionales (BDC). Obtenga información sobre los métodos de asociación y los tipos de asociaciones.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Association_Dialog
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
ms.openlocfilehash: d40c4e5c5d61b9da3cdbdd3fe96f45c4a0cff929
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106213971"
---
# <a name="create-an-association-between-entities"></a>Crear una asociación entre entidades
  Puede definir las relaciones entre las entidades del modelo de conectividad a datos profesionales (BDC) mediante la creación de asociaciones. Visual Studio genera métodos que proporcionan a los consumidores del modelo información sobre cada asociación. Estos métodos pueden ser consumidos por elementos Web, listas o aplicaciones personalizadas de SharePoint para mostrar las relaciones de datos en una interfaz de usuario (UI).

## <a name="create-an-association"></a>Creación de una asociación
 Para crear una asociación, elija el control de **Asociación** en el **cuadro de herramientas** de Visual Studio, elija la primera entidad (denominada entidad de origen) y, a continuación, elija la segunda entidad (denominada entidad de destino). Puede definir los detalles de la asociación en el **Editor de asociaciones**. Para obtener más información, vea [Cómo: crear una asociación entre entidades](../sharepoint/how-to-create-an-association-between-entities.md).

## <a name="association-methods"></a>Métodos de asociación
 Las aplicaciones como los elementos Web de datos empresariales de SharePoint consumen asociaciones llamando a métodos en la clase de servicio de una entidad. Puede Agregar métodos a la clase de servicio de una entidad seleccionándolos en el editor de **asociaciones**.

 De forma predeterminada, el **Editor de asociaciones** agrega un método de navegación de asociación a las entidades de origen y de destino. Un método de navegación por Asociación de la entidad de origen permite a los consumidores recuperar una lista de entidades de destino. Un método de navegación por asociación en la entidad de destino permite a los consumidores recuperar la entidad de origen relacionada con una entidad de destino.

 Debe agregar el código a cada uno de estos métodos para devolver la información adecuada. También puede agregar otros tipos de métodos para admitir escenarios más avanzados. Para obtener más información sobre cada uno de estos métodos, consulte [operaciones admitidas](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14)).

## <a name="types-of-associations"></a>Tipos de asociaciones
 Puede crear dos tipos de asociaciones en el diseñador de BDC: asociaciones basadas en claves externas y asociaciones sin clave externa.

### <a name="foreign-key-based-association"></a>Asociación basada en clave externa
 Puede crear una asociación basada en clave externa relacionando un identificador de la entidad de origen con los descriptores de tipo definidos en la entidad de destino. Esta relación permite a los consumidores del modelo proporcionar una interfaz de usuario mejorada para sus usuarios. Por ejemplo, un formulario de Outlook que permite a un usuario crear un pedido de ventas que puede mostrar clientes en una lista desplegable. o una lista de pedidos de ventas en SharePoint que permite a los usuarios abrir una página de perfil para un cliente.

 Para crear una asociación basada en claves externas, relacione los identificadores y los descriptores de tipos que comparten el mismo nombre y tipo. Por ejemplo, puede crear una asociación basada en claves externas entre una `Contact` entidad y una `SalesOrder` entidad. La `SalesOrder` entidad devuelve un `ContactID` descriptor de tipo como parte del parámetro devuelto de los métodos Finder específicos o Finder. Ambos descriptores de tipo aparecen en el **Editor de asociaciones**. Para crear una relación basada en clave externa entre la `Contact` entidad y la `SalesOrder` entidad, elija el `ContactID` identificador junto a cada uno de estos campos.

 Agregue código al método de navegador de asociaciones de la entidad de origen que devuelve una colección de entidades de destino. En el ejemplo siguiente se devuelven los pedidos de ventas de un contacto.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet7":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet7":::

 Agregue código al método de navegador de asociaciones de la entidad de destino que devuelve una entidad de origen. En el ejemplo siguiente se devuelve el contacto relacionado con el pedido de venta.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs" id="Snippet8":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb" id="Snippet8":::

### <a name="foreign-keyless-association"></a>Asociación de entrada sin llave externa
 Puede crear una asociación sin asignar identificadores a los descriptores de tipo de campo. Cree este tipo de asociación cuando la entidad de origen no tenga una relación directa con la entidad de destino. Por ejemplo, una `SalesOrderDetail` tabla no tiene una clave externa que se asigna a una clave principal de una `Contact` tabla.

 Si desea mostrar información en la `SalesOrderDetail` tabla relacionada con una `Contact` , puede crear una asociación de sin llave externa entre la `Contact` entidad y la `SalesOrderDetail` entidad.

 En el método de navegación de Asociación de la `Contact` entidad, devuelva las `SalesOrderDetail` entidades combinando las tablas o llamando a un procedimiento almacenado.

 En el ejemplo siguiente se devuelven los detalles de todos los pedidos de ventas mediante la combinación de tablas.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet9":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet9":::

 En el método de navegación de Asociación de la `SalesOrderDetail` entidad, devuelva el relacionado `Contact` . En el siguiente ejemplo se muestra cómo hacerlo.
                                                                            
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs" id="Snippet10":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb" id="Snippet10":::

## <a name="see-also"></a>Consulte también
- [Diseño de un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Cómo: crear una asociación entre entidades](../sharepoint/how-to-create-an-association-between-entities.md)
