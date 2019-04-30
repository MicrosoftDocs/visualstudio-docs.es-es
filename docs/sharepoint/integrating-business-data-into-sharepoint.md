---
title: Integrar datos profesionales en SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fbbdba27b5ccc52e64575aad018af4ca20cf2e14
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008810"
---
# <a name="integrate-business-data-into-sharepoint"></a>Integrar datos profesionales en SharePoint
  Puede integrar datos profesionales en SharePoint. Datos profesionales pueden proceder de aplicaciones de servidor back-end, como [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel y SAP, o un servicio Web. Los usuarios pueden ver, agregar, actualizar o eliminar los datos empresariales mediante el uso de listas externas o elementos Web de datos profesionales en SharePoint.  Los usuarios también pueden tener acceso a estos datos sin conexión en una aplicación de Microsoft Office como Microsoft Outlook. Para obtener más información, consulte [donde puede que muestran datos externos](http://go.microsoft.com/fwlink/?LinkId=169295).

 Para integrar datos en SharePoint, cree un modelo para el servicio de conectividad de datos profesionales (BDC). El servicio BDC es una aplicación de SharePoint que almacena información acerca de los datos en aplicaciones empresariales. Para obtener más información, consulte [servicio conectividad de datos profesionales (BDC)](http://go.microsoft.com/fwlink/?LinkID=169276).

## <a name="models-in-visual-studio"></a>Modelos en Visual Studio
 Los modelos en Visual Studio le permiten escribir código personalizado para recuperar y actualizar datos de orígenes de datos back-end. También puede agregar los datos de varios orígenes de datos. Por ejemplo, puede mostrar una lista de clientes que contiene los datos de un [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] base de datos y un servicio Web.

 También puede importar los modelos que ya están implementados en SharePoint. Después de importar un modelo, puede agregar código personalizado o simplemente usar Visual Studio para empaquetar e implementar el modelo en varias granjas de servidores de SharePoint. Para obtener más información, consulte [crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="design-a-model-in-visual-studio"></a>Diseñar un modelo en Visual Studio
 Puede diseñar un modelo utilizando un diseñador y varias ventanas de herramientas. Al diseñar el modelo, Visual Studio genera el XML del modelo. Para obtener más información, consulte [información general de las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).

 Un modelo contiene entidades y métodos.

### <a name="entities"></a>Entidades
 Una entidad describe una colección de campos. Por ejemplo, una entidad puede representar una tabla en una base de datos. Una entidad aparece como un tipo de contenido externo en SharePoint. Para obtener más información sobre los tipos de contenido externo, consulte [¿cuáles son los tipos de contenido externos?](http://go.microsoft.com/fwlink/?LinkId=169293)

### <a name="methods"></a>Métodos
 Un método permite a los consumidores de un tipo de contenido externo para realizar una acción en los campos de una entidad. Por ejemplo, un método Updater podría permitir que los usuarios cambiar la dirección y la fecha de un cliente de nacimiento donde `Address` y `BirthDate` son campos de la `Customer` entidad.

 Visual Studio genera un archivo de código de servicio para cada entidad en el modelo. Cuando se agrega un método al modelo, Visual Studio genera un método correspondiente en el archivo de código de servicio. Agregue código a cada método para realizar la tarea adecuada. Por ejemplo, si agrega un método Creator al modelo, Visual Studio genera un método Creator en el archivo de código de servicio. El servicio BDC llama a este método cuando un usuario hace clic en el **nuevo elemento** botón en una lista que se basa en el modelo. Por lo tanto, agregue código al método Creator que agrega nuevos datos a un origen de datos. Para obtener más información, consulte [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).

## <a name="related-topics"></a>Temas relacionados

|Título|Descripción|
|-----------|-----------------|
|[Crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md)|Muestra cómo crear un nuevo modelo o importa un modelo que desea exportar desde SharePoint.|
|[Diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md)|Explica cómo diseñar los elementos de un modelo mediante las herramientas de diseño de Visual Studio.|
|[Cuándo se debe usar SharePoint Designer vs. Soluciones de Visual Studio al compilar con BCS](http://go.microsoft.com/fwlink/?LinkID=183448)|Le ayuda a decidir si desea usar Visual Studio o usar SharePoint Designer para crear un modelo de BDC.|
