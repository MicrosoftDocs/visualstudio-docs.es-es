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
ms.openlocfilehash: 06d9e8059db8daa1c27b8c1d5fecc50940b7facb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986389"
---
# <a name="integrate-business-data-into-sharepoint"></a>Integrar datos profesionales en SharePoint
  Puede integrar los datos empresariales en SharePoint. Los datos empresariales pueden provienen de aplicaciones de servidor back-end, como [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel y SAP, o un servicio Web. Los usuarios pueden ver, agregar, actualizar o eliminar datos empresariales mediante listas externas o datos empresariales elementos web en SharePoint.  Los usuarios también pueden tener acceso a estos datos sin conexión en una aplicación Microsoft Office como Microsoft Outlook. Para obtener más información, consulte [dónde puede mostrar los datos externos](/previous-versions/office/developer/sharepoint-2010/ee558737(v=office.14)).

 Para integrar los datos en SharePoint, cree un modelo para el servicio de conectividad a datos profesionales (BDC). El servicio BDC es una aplicación de SharePoint que almacena información acerca de los datos de las aplicaciones empresariales. Para obtener más información, vea [servicio de conectividad a datos profesionales (BDC)](/previous-versions/office/developer/sharepoint-2010/ee556407(v=office.14)).

## <a name="models-in-visual-studio"></a>Modelos en Visual Studio
 Los modelos de Visual Studio le permiten escribir código personalizado para recuperar y actualizar los datos de los orígenes de datos de back-end. También puede agregar datos de varios orígenes de datos. Por ejemplo, puede mostrar una lista de clientes que contienen datos de una base de datos de [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] y un servicio Web.

 También puede importar modelos que ya están implementados en SharePoint. Después de importar un modelo, puede agregar código personalizado o simplemente usar Visual Studio para empaquetar e implementar el modelo en varias granjas de servidores de SharePoint. Para obtener más información, vea [crear un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="design-a-model-in-visual-studio"></a>Diseño de un modelo en Visual Studio
 Puede diseñar un modelo mediante un diseñador y varias ventanas de herramientas. Al diseñar el modelo, Visual Studio genera el XML del modelo. Para obtener más información, vea [información general sobre las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).

 Un modelo contiene entidades y métodos.

### <a name="entities"></a>Entidades
 Una entidad describe una colección de campos. Por ejemplo, una entidad puede representar una tabla en una base de datos. Una entidad aparece como un tipo de contenido externo en SharePoint. Para obtener más información sobre los tipos de contenido externo, vea [¿Qué son los tipos de contenido externo?](/previous-versions/office/developer/sharepoint-2010/ee556391(v=office.14))

### <a name="methods"></a>Métodos
 Un método permite a los consumidores de un tipo de contenido externo realizar una acción en los campos de una entidad. Por ejemplo, un método Updater puede permitir a los usuarios cambiar la dirección y la fecha de nacimiento de un cliente donde `Address` y `BirthDate` son campos de la entidad `Customer`.

 Visual Studio genera un archivo de código de servicio para cada entidad del modelo. Al agregar un método al modelo, Visual Studio genera un método correspondiente en el archivo de código de servicio. Agregue código a cada método para realizar la tarea adecuada. Por ejemplo, si agrega un método Creator al modelo, Visual Studio genera un método Creator en el archivo de código de servicio. El servicio BDC llama a este método cuando un usuario hace clic en el botón **nuevo elemento** de una lista que se basa en el modelo. Por lo tanto, agregue código al método Creator que agrega nuevos datos a un origen de datos. Para obtener más información, vea [diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Crear un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md)|Muestra cómo crear un nuevo modelo o importar un modelo que se exporta desde SharePoint.|
|[Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)|Explica cómo diseñar los elementos de un modelo con las herramientas de diseño de Visual Studio.|
|[Cuándo usar SharePoint Designer frente a Visual Studio al compilar soluciones con BCS](/previous-versions/office/developer/sharepoint-2010/ee558875(v=office.14))|Ayuda a decidir si utilizar Visual Studio o SharePoint Designer para crear un modelo para el BDC.|
