---
title: Integrar datos profesionales en SharePoint | Documentos de Microsoft
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
- Business Data Connectivity service [SharePoint development in Visual Studio], business data
- BDC [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], business data
- Business Data Connectivity service [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], data
- BDC [SharePoint development in Visual Studio], data
ms.assetid: e092e3d6-2c5f-4060-ae86-d37db8967559
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ece3128c2d6850a1d1dd22d0328a4ee2c46da2b1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="integrating-business-data-into-sharepoint"></a>Integrar Datos profesionales en SharePoint
  Puede integrar datos profesionales en SharePoint. Datos profesionales pueden proceder de aplicaciones de servidor back-end, como [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel y SAP, o un servicio Web. Los usuarios pueden ver, agregar, actualizar o eliminar datos empresariales mediante listas externas o elementos Web de datos profesionales en SharePoint.  Los usuarios también pueden tener acceso a estos datos sin conexión en una aplicación de Microsoft Office, como Microsoft Outlook. Para obtener más información, consulte [donde puede You Show External Data](http://go.microsoft.com/fwlink/?LinkId=169295).  
  
 Para integrar datos en SharePoint, cree un modelo para el servicio de conectividad de datos profesionales (BDC). El servicio BDC es una aplicación de SharePoint que almacena información sobre datos de aplicaciones empresariales. Para obtener más información, consulte [servicio de conectividad de datos profesionales (BDC)](http://go.microsoft.com/fwlink/?LinkID=169276).  
  
## <a name="models-in-visual-studio"></a>Modelos en Visual Studio  
 Los modelos en Visual Studio le permiten escribir código personalizado para recuperar y actualizar datos de orígenes de datos back-end. También puede agregar los datos de varios orígenes de datos. Por ejemplo, puede mostrar una lista de clientes que contiene los datos de un [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] base de datos y un servicio Web.  
  
 También puede importar modelos que ya se han implementado en SharePoint. Después de importar un modelo, puede agregar código personalizado o simplemente usar Visual Studio para empaquetar e implementar el modelo en varias granjas de servidores de SharePoint. Para obtener más información, consulte [crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="designing-a-model-in-visual-studio"></a>Diseñar un modelo en Visual Studio  
 Puede diseñar un modelo utilizando un diseñador y varias ventanas de herramientas. Al diseñar el modelo, Visual Studio genera el XML del modelo. Para obtener más información, consulte [herramientas información general del diseño de modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
 Un modelo contiene entidades y métodos.  
  
### <a name="entities"></a>Entidades  
 Una entidad describe una colección de campos. Por ejemplo, una entidad puede representar una tabla en una base de datos. Una entidad aparece como un tipo de contenido externo en SharePoint. Para obtener más información acerca de los tipos de contenido externos, vea [¿cuáles son los tipos de contenido externos?](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### <a name="methods"></a>Métodos  
 Un método permite a los consumidores de un tipo de contenido externo para realizar una acción en los campos de una entidad. Por ejemplo, un método Updater podría permitir a los usuarios cambiar la dirección y fecha de un cliente de nacimiento donde `Address` y `BirthDate` son campos de la `Customer` entidad.  
  
 Visual Studio genera un archivo de código de servicio para cada entidad en el modelo. Cuando se agrega un método al modelo, Visual Studio genera un método correspondiente en el archivo de código de servicio. Agregue código a cada método para realizar la tarea adecuada. Por ejemplo, si agrega un método Creator al modelo, Visual Studio genera un método Creator en el archivo de código de servicio. El servicio BDC llama a este método cuando un usuario hace clic en el **nuevo elemento** botón en una lista que se basa en el modelo. Por lo tanto, agregue código al método Creator que agrega nuevos datos a un origen de datos. Para obtener más información, consulte [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Crea un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md)|Le muestra cómo crea un nuevo modelo o importa un modelo que se exporta de SharePoint.|  
|[Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)|Explica cómo diseñar los elementos de un modelo mediante herramientas de diseño de Visual Studio.|  
|[Cuando usa SharePoint Designer frente a. Soluciones de Visual Studio cuando creación mediante BCS](http://go.microsoft.com/fwlink/?LinkID=183448)|Le ayuda a decidir si desea utilizar Visual Studio o usar SharePoint Designer para crear un modelo de BDC.|  
  
  