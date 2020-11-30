---
title: Integración de datos profesionales en SharePoint | Microsoft Docs
description: Lea un resumen detallado sobre cómo integrar datos profesionales en SharePoint mediante la creación de un modelo para el servicio de conectividad a datos profesionales (BDC).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
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
ms.openlocfilehash: f3156adc286222282ae63f70f70838bc6b7155a8
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304352"
---
# <a name="integrate-business-data-into-sharepoint"></a>Integración de datos profesionales en SharePoint
  Puede integrar datos profesionales en SharePoint. Los datos profesionales pueden proceder de aplicaciones de servidor back-end, como [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel y SAP, o bien un servicio web. Los usuarios pueden ver, agregar, actualizar o eliminar datos profesionales mediante listas externas o elementos web de datos profesionales en SharePoint.  Los usuarios también pueden acceder a estos datos sin conexión en una aplicación de Microsoft Office como Microsoft Outlook. Para obtener más información, vea [¿Dónde se pueden mostrar datos externos?](/previous-versions/office/developer/sharepoint-2010/ee558737(v=office.14)).

 Para integrar datos en SharePoint, cree un modelo para el servicio Conectividad a datos profesionales (BDC). El servicio BDC es una aplicación de SharePoint que almacena información sobre los datos de las aplicaciones empresariales. Para obtener más información, vea [Servicio Conectividad a datos profesionales (BDC)](/previous-versions/office/developer/sharepoint-2010/ee556407(v=office.14)).

## <a name="models-in-visual-studio"></a>Modelos en Visual Studio
 Los modelos de Visual Studio le permiten escribir código personalizado para recuperar y actualizar datos de orígenes de datos de back-end. También puede agregar datos de varios orígenes de datos. Por ejemplo, puede mostrar una lista de clientes que contenga datos de una base de datos de [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] y un servicio web.

 También puede importar modelos que ya están implementados en SharePoint. Después de importar un modelo, puede agregar código personalizado o simplemente usar Visual Studio para empaquetar e implementar el modelo en varias granjas de servidores de SharePoint. Para obtener más información, vea [Creación de un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="design-a-model-in-visual-studio"></a>Diseño de un modelo en Visual Studio
 Puede diseñar un modelo mediante un diseñador y varias ventanas de herramientas. Mientras se diseña el modelo, Visual Studio genera el XML del modelo. Para obtener más información, vea [Introducción general a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).

 Un modelo contiene entidades y métodos.

### <a name="entities"></a>Entidades
 Un entidad describe una colección de campos. Por ejemplo, una entidad puede representar una tabla de una base de datos. Una entidad aparece como un tipo de contenido externo en SharePoint. Para obtener más información sobre los tipos de contenido externo, vea [¿Qué son los tipos de contenido externo?](/previous-versions/office/developer/sharepoint-2010/ee556391(v=office.14))

### <a name="methods"></a>Métodos
 Un método permite a los consumidores de un tipo de contenido externo realizar una acción en los campos de una entidad. Por ejemplo, un método Updater puede permitir a los usuarios cambiar la dirección y la fecha de nacimiento de un cliente donde `Address` y `BirthDate` son campos de la entidad `Customer`.

 Visual Studio genera un archivo de código de servicio para cada entidad del modelo. Al agregar un método al modelo, Visual Studio genera un método correspondiente en el archivo de código de servicio. Agregue código a cada método para realizar la tarea adecuada. Por ejemplo, si agrega un método Creator al modelo, Visual Studio genera un método Creator en el archivo de código de servicio. El servicio BDC llama a este método cuando un usuario hace clic en el botón **Nuevo elemento** de una lista que se basa en el modelo. Por tanto, agregue código al método Creator que agrega nuevos datos a un origen de datos. Para obtener más información, vea [Diseño de un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Creación de un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md)|Se muestra cómo crear un modelo, o importar un modelo que se exporta desde SharePoint.|
|[Diseño de un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)|Se explica cómo diseñar los elementos de un modelo con las herramientas de diseño de Visual Studio.|
|[Diferencias entre usar SharePoint Designer y Visual Studio al compilar soluciones con BCS](/previous-versions/office/developer/sharepoint-2010/ee558875(v=office.14))|Le ayuda a decidir si debe usar Visual Studio o SharePoint Designer para crear un modelo para el BDC.|
