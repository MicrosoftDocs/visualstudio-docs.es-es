---
title: "Crear una asociaci&#243;n entre entidades | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.BDC.Association_Dialog"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [desarrollo de SharePoint en Visual Studio], asociar tipos de contenido externos"
  - "BDC [desarrollo de SharePoint en Visual Studio], asociaciones entre entidades"
  - "BDC [desarrollo de SharePoint en Visual Studio], crear una asociación"
  - "BDC [desarrollo de SharePoint en Visual Studio], relacionar entidades"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], asociar tipos de contenido externos"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], asociaciones entre entidades"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], crear una asociación"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], relacionar entidades"
ms.assetid: c908448c-13d3-4d2f-89ad-8d709b2958fb
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Crear una asociaci&#243;n entre entidades
  Puede definir las relaciones entre las entidades del Modelo de conectividad a datos profesionales \(BDC\) creando asociaciones.  Visual Studio genera métodos que proporcionan a los consumidores del modelo información sobre cada asociación.  Estos métodos se pueden utilizar en elementos web de SharePoint, listas, o aplicaciones personalizadas de mostrar las relaciones de datos en una interfaz de usuario \(UI\).  
  
## Crear una asociación  
 Crear una asociación mediante el control de **Asociación** en Visual Studio **Cuadro de herramientas**, elegir la primera entidad \(denominada entidad de origen\), y elige la segunda entidad \(denominada entidad de destino\).  Puede definir los detalles de la asociación en el **Editor de asociaciones**.  Para obtener más información, vea [Cómo crear una asociación entre entidades](../sharepoint/how-to-create-an-association-between-entities.md).  
  
## Métodos de asociación  
 Las aplicaciones como elementos web de datos profesionales de SharePoint utilizan las asociaciones llamando a métodos de la clase de servicio de una entidad.  Puede agregar métodos a la clase de servicio de una entidad seleccionándolos en el **Editor de asociaciones**.  
  
 De forma predeterminada, el **Editor de asociaciones** agrega un método de navegación mediante asociaciones a las entidades de origen y destino.  Un método de navegación mediante asociaciones en la entidad de origen permite a los consumidores recuperar una lista de las entidades de destino.  Un método de navegación mediante asociaciones en la entidad de destino permite a los consumidores recuperar la entidad de origen que se relaciona con una entidad de destino.  
  
 Debe agregar código a cada uno de estos métodos para que devuelvan la información adecuada.  También puede agregar otros tipos de métodos para escenarios más avanzados.  Para obtener más información sobre cada uno de estos métodos, vea [Operaciones admitidas](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
## Tipos de asociaciones  
 Puede crear dos tipos de asociaciones en el diseñador de BDC: asociaciones basadas en clave externa y asociaciones sin clave externa.  
  
### Asociación basada en clave externa  
 Puede crear una asociación basada en clave externa relacionando un identificador de la entidad de origen con los descriptores de tipo definidos en la entidad de destino.  Esta relación permite a los consumidores del modelo proporcionar una interfaz de usuario mejorada a sus usuarios.  Por ejemplo, un formulario de Outlook que permite a un usuario crear un pedido de ventas que puede mostrar los clientes en una lista desplegable; o una lista de pedidos de ventas de SharePoint que permite a los usuarios abrir una página de perfiles para un cliente.  
  
 Para crear una asociación basada en clave externa, relacione los identificadores y descriptores de tipos que comparten el mismo nombre y tipo.  Por ejemplo, podría crear una asociación basada en clave externa entre una entidad `Contact` y una entidad `SalesOrder`.  La entidad `SalesOrder` devuelve un descriptor de tipos `ContactID` como parte del parámetro devuelto de los métodos Finder o Finder específico.  Ambos descriptores de tipos aparecen en el **Editor de asociaciones**.  Para crear una relación tecla\- basada externa entre la entidad de `Contact` y la entidad de `SalesOrder` , elija el identificador de `ContactID` junto a cada uno de estos campos.  
  
 En el método de navegación mediante asociaciones de la entidad de origen, agregue código que devuelva una colección de entidades de destino.  En el siguiente ejemplo se devuelven los pedidos de ventas de un contacto.  
  
 [!code-csharp[SP_BDC#7](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#7)]  
  
 En el método de navegación mediante asociaciones de la entidad de destino, agregue código que devuelva la entidad de origen.  En el siguiente ejemplo se devuelve el contacto que se relaciona con el pedido de ventas.  
  
 [!code-csharp[SP_BDC#8](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderservice.vb#8)]  
  
### Asociación sin clave externa  
 Puede crear una asociación sin asignar identificadores a los descriptores de tipos de campo.  Cree este tipo de asociación cuando la entidad de origen no tenga relación directa con la entidad de destino.  Por ejemplo, una tabla `SalesOrderDetail` no tiene ninguna clave externa asignada a una clave principal de una tabla `Contact`.  
  
 Si desea mostrar la información de la tabla `SalesOrderDetail` que está relacionada con un `Contact`, puede crear una asociación de clave externa entre la entidad `Contact` y la entidad `SalesOrderDetail`.  
  
 En el método de navegación mediante asociaciones de la entidad `Contact`, devuelva las entidades `SalesOrderDetail` uniendo las tablas o llamando a un procedimiento almacenado.  
  
 En el siguiente ejemplo se devuelven detalles de todos los pedidos de ventas mediante la unión de las tablas.  
  
 [!code-csharp[SP_BDC#9](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#9)]  
  
 En el método de navegación mediante asociaciones de la entidad `SalesOrderDetail`, devuelva el `Contact` relacionado.  En el siguiente ejemplo se muestra cómo.  
  
 [!code-csharp[SP_BDC#10](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## Vea también  
 [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Cómo crear una asociación entre entidades](../sharepoint/how-to-create-an-association-between-entities.md)  
  
  