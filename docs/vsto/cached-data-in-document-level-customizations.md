---
title: Datos almacenados en caché en personalizaciones de nivel de documento
description: Obtenga información sobre cómo Visual Studio separa los datos de la vista en las personalizaciones de nivel de documento habilitando los datos que se van a incrustar como caché de datos.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data islands [Office development in Visual Studio]
- view [Office development in Visual Studio]
- caching data [Office development in Visual Studio], about caching data
- data caching [Office development in Visual Studio], about data caching
- data [Office development in Visual Studio], cache
- data [Office development in Visual Studio], document-level solutions
- document-level customizations [Office development in Visual Studio], data model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: be4229c179ec6c5640ab612d28991fe476363a53
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847902"
---
# <a name="cached-data-in-document-level-customizations"></a>Datos almacenados en caché en personalizaciones de nivel de documento
  Un objetivo principal de las personalizaciones de nivel de documento es separar los datos de la vista en los documentos de Office. Los datos hacen referencia a la información que se almacena en el documento, incluidos los números y el texto. La vista hace referencia a la interfaz de usuario y al modelo de objetos de Microsoft Office Word y Microsoft Office Excel.

 Visual Studio separa los datos de la vista en las personalizaciones de nivel de documento al permitir que los datos se incrusten como una *isla de datos*, también denominada *caché de datos*. Puede leer o modificar los datos directamente sin iniciar Word o Excel. Esto resulta útil si necesita modificar datos en documentos en un servidor que no tiene Microsoft Office instalado. Word y Excel están diseñados para usarse en entornos de cliente; no están diseñados para ejecutarse en un servidor.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Para obtener más información sobre las personalizaciones de nivel de documento, vea [información general sobre el desarrollo de soluciones de Office &#40;&#41;de VSTO ](../vsto/office-solutions-development-overview-vsto.md) y [la arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md).

## <a name="understand-the-cached-data-programming-model"></a>Descripción del modelo de programación de datos almacenados en caché
 La isla de datos puede contener cualquier objeto de la solución que cumpla determinados requisitos. Estos objetos incluyen <xref:System.Data.DataSet> objetos, <xref:System.Data.DataTable> objetos y cualquier otro objeto que se pueda serializar mediante la <xref:System.Xml.Serialization.XmlSerializer> clase. Para obtener más información, vea [almacenar datos en caché](../vsto/caching-data.md).

 Para proporcionar la vista de los datos en caché, puede enlazar los controles de Windows Forms y los *controles host* del documento a los objetos de la isla de datos. El enlace de datos entre la isla de datos y los controles enlazados a datos mantiene los dos sincronizados. También puede agregar código de validación a los datos que son independientes de los controles. Para obtener más información, vea [enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 Los controles host son versiones extendidas de los objetos nativos de los modelos de objetos de Excel y Word. A diferencia de los objetos nativos, los controles host se pueden enlazar directamente a objetos de datos administrados. Para obtener más información, vea [información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md) y [Windows Forms controles en documentos de Office información general](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="access-cached-data-on-the-server"></a>Acceder a los datos almacenados en caché en el servidor
 Para tener acceso a los datos en caché de un documento, puede utilizar la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase. Esta clase forma parte de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] y se puede usar en un servidor sin ejecutar Excel o Word. Cuando el usuario abre el documento después de modificar los datos en caché, los controles que están enlazados a los datos se sincronizan automáticamente con los cambios y el usuario recibe los datos actualizados. Para obtener más información, vea [obtener acceso a los datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md).

 Excel y Word no son necesarios para escribir en los datos del servidor, solo para verlos en el cliente. No es necesario que Excel y Word estén instalados en el servidor. Esto proporciona una mejor escalabilidad y la capacidad de realizar un procesamiento por lotes rápido de documentos que contienen islas de datos.

## <a name="data-caching-for-offline-use"></a>Almacenamiento en caché de datos para uso sin conexión
 El almacenamiento de datos en la isla de datos permite escenarios sin conexión. Cuando un usuario abre por primera vez un documento o solicita el documento del servidor, la isla de datos se rellena con los datos más recientes. La isla de datos se almacena en caché en el documento y, a continuación, está disponible sin conexión. El usuario (y el código) puede manipular los datos, aunque no haya ninguna conexión dinámica disponible. Cuando el usuario se vuelve a conectar, los cambios en los datos se pueden propagar de nuevo a un origen de datos del servidor.

## <a name="cached-data-and-custom-xml-parts-compared"></a>Comparación de los datos almacenados en caché y los elementos XML personalizados
 Los elementos XML personalizados se introdujeron en el sistema Microsoft Office de 2007 como una manera de almacenar fragmentos arbitrarios de XML en un documento. Aunque los elementos XML personalizados son útiles en muchos de los mismos escenarios que la memoria caché de datos, existen algunas diferencias entre la isla de datos y los elementos XML personalizados. Para obtener más información sobre los elementos XML personalizados, vea [información general sobre los elementos XML personalizados](../vsto/custom-xml-parts-overview.md).

 En la tabla siguiente se enumeran algunas de las diferencias y similitudes.

|Pregunta o característica|Caché de datos|Elementos XML personalizados|
|-|----------------|----------------------|
|¿Qué aplicaciones de Office pueden usarlos?|Personalizaciones de nivel de documento para las siguientes aplicaciones:<br /><br /> -Excel<br />-Word|Soluciones de nivel de documento y de nivel de aplicación para las siguientes aplicaciones:<br /><br /> -Excel<br />-PowerPoint<br />-Word|
|¿Qué tipos de datos se pueden almacenar?|Cualquier objeto público del ensamblado de personalización que cumpla determinados requisitos. Para obtener más información, vea [almacenar datos en caché](../vsto/caching-data.md).|Cualquier dato XML.|
|¿Se puede tener acceso a los datos sin iniciar Microsoft Office aplicaciones?|Sí, mediante la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase proporcionada por [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .|Sí, mediante el uso de clases en el <xref:System.IO.Packaging> espacio de nombres o mediante el SDK de formato Open XML.|

## <a name="see-also"></a>Vea también
- [Datos en soluciones de Office](../vsto/data-in-office-solutions.md)
- [Arquitectura de las soluciones de Office en Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
