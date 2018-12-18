---
title: Crear una asociación entre entidades | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 22ac00ac48f4fe907e4fb4215992b49227f39961
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325468"
---
# <a name="create-an-association-between-entities"></a>Crear una asociación entre entidades
  Puede definir las relaciones entre entidades en el modelo de conectividad de datos profesionales (BDC) mediante la creación de asociaciones. Visual Studio genera los métodos que proporcionan información sobre cada asociación de los consumidores del modelo. Estos métodos pueden usarse en aplicaciones personalizadas para mostrar las relaciones de datos en una interfaz de usuario (UI), listas o elementos web de SharePoint.  
  
## <a name="create-an-association"></a>Crear una asociación
 Para crear una asociación, seleccione el **asociación** control en Visual Studio **cuadro de herramientas**, elija la primera entidad (llama a la entidad de origen) y, a continuación, elija la segunda entidad (denominado el entidad de destino). Puede definir los detalles de la asociación en el **Editor de asociaciones**. Para obtener más información, consulte [Cómo: crear una asociación entre entidades](../sharepoint/how-to-create-an-association-between-entities.md).  
  
## <a name="association-methods"></a>Métodos de asociación
 Las aplicaciones como elementos web de SharePoint business datos consumir asociaciones llamando a métodos en la clase de servicio de una entidad. Puede agregar métodos a la clase de servicio de una entidad seleccionándolos en el **Editor de asociaciones**.  
  
 De forma predeterminada, el **Editor de asociaciones** agrega un método de navegación de la asociación a las entidades de origen y destino. Un método de navegación de la asociación en la entidad de origen permite a los consumidores recuperar una lista de entidades de destino. Un método de navegación de la asociación en la entidad de destino permite a los consumidores recuperar la entidad de origen que se relaciona con una entidad de destino.  
  
 Debe agregar el código a cada uno de estos métodos para devolver la información apropiada. También puede agregar otros tipos de métodos para admitir escenarios más avanzados. Para obtener más información sobre cada uno de estos métodos, consulte [admite operaciones](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
## <a name="types-of-associations"></a>Tipos de asociaciones
 Puede crear dos tipos de asociaciones en el Diseñador de BDC: asociaciones basada en claves externas y las asociaciones sin clave externa.  
  
### <a name="foreign-key-based-association"></a>Asociación basada en claves externa
 Puede crear una asociación basada en claves externa relacionando un identificador de la entidad de origen en descriptores de tipo definidos en la entidad de destino. Esta relación permite a los consumidores del modelo proporcionar una interfaz de usuario mejorada para sus usuarios. Por ejemplo, un formulario de Outlook que permite al usuario crear un pedido de ventas que puede mostrar a los clientes en una lista desplegable; o una lista de pedidos de venta de SharePoint que permite a los usuarios abrir una página de perfil para un cliente.  
  
 Para crear una asociación basada en claves externa, se relacionan con los identificadores y descriptores de tipos que comparten el mismo nombre y tipo. Por ejemplo, podría crear una asociación basada en claves externa entre un `Contact` entidad y un `SalesOrder` entidad. El `SalesOrder` entidad devuelve una `ContactID` descriptor de tipos como parte del parámetro devuelto de los métodos Finder o Finder específico. Ambos descriptores de tipo aparecen en la **Editor de asociaciones**. Para crear una relación basada en claves externa entre el `Contact` entidad y `SalesOrder` entidades, elija el `ContactID` identificador situado junto a cada uno de estos campos.  
  
 Agregue código para el método de navegación de la asociación de la entidad de origen que devuelve una colección de entidades de destino. El ejemplo siguiente devuelve los pedidos de venta para un contacto.  
  
 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]  
  
 Agregue código para el método de navegación de la asociación de la entidad de destino que devuelve una entidad de origen. El ejemplo siguiente devuelve el contacto que está relacionado con el pedido de ventas.  
  
 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]  
  
### <a name="foreign-keyless-association"></a>Asociación sin clave externa
 Puede crear una asociación sin asignar identificadores a los descriptores de tipo de campo. Cree este tipo de asociación cuando la entidad de origen no tiene una relación directa con la entidad de destino. Por ejemplo, un `SalesOrderDetail` tabla no tiene una clave externa que se asigna a una clave principal en un `Contact` tabla.  
  
 Si desea mostrar información en el `SalesOrderDetail` tabla que se relaciona con un `Contact`, puede crear una asociación sin clave externa entre la `Contact` entidad y `SalesOrderDetail` entidad.  
  
 En el método de navegación de la asociación de la `Contact` entidad, el valor devuelto del `SalesOrderDetail` entidades mediante la combinación de tablas, o mediante una llamada a un procedimiento almacenado.  
  
 El ejemplo siguiente devuelve los detalles de todos los pedidos de ventas mediante la combinación de tablas.  
  
 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]  
  
 En el método de navegación de la asociación de la `SalesOrderDetail` entidad, devolver relacionado `Contact`. En el siguiente ejemplo se muestra cómo hacerlo.  
  
 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## <a name="see-also"></a>Vea también
 [Diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Cómo: crear una asociación entre entidades](../sharepoint/how-to-create-an-association-between-entities.md)  
  
 
