---
title: Datos almacenados en caché en las personalizaciones de nivel de documento
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: c17c24dda11ea210c190a31197b783036357f2de
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248301"
---
# <a name="cached-data-in-document-level-customizations"></a>Datos almacenados en caché en las personalizaciones de nivel de documento
  Un objetivo principal de las personalizaciones de nivel de documento es separar los datos de vista de documentos de Office. Datos hacen referencia a la información que se almacena en el documento, incluidos números y texto. La vista hace referencia a la interfaz de usuario y el modelo de objetos de Microsoft Office Word y Microsoft Office Excel.  
  
 Visual Studio separa los datos de la vista en las personalizaciones de nivel de documento habilitando los datos que se incrusta como un *isla de datos*, también denominado el *memoria caché de datos*. Puede leer o modificar los datos directamente sin iniciar Word o Excel. Esto es útil cuando necesite modificar los datos de documentos en un servidor que no tiene instalado Microsoft Office. Word y Excel están diseñados para su uso en entornos de cliente; no están diseñados para ejecutarse en un servidor.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Para obtener más información acerca de las personalizaciones de nivel de documento, consulte [información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) y [arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="understand-the-cached-data-programming-model"></a>Comprender el modelo de programación de datos en caché  
 La isla de datos puede contener cualquier objeto de la solución que cumpla determinados requisitos. Estos objetos incluyen <xref:System.Data.DataSet> objetos, <xref:System.Data.DataTable> objetos y cualquier otro objeto que se puede serializar el <xref:System.Xml.Serialization.XmlSerializer> clase. Para obtener más información, consulte [almacenar en caché datos](../vsto/caching-data.md).  
  
 Para proporcionar la vista de los datos en caché, puede enlazar controles de formularios Windows Forms y *controles host* en el documento a los objetos de la isla de datos. Enlace de datos entre la isla de datos y los controles enlazados a datos mantiene a ambos sincronizados. También puede agregar código de validación a los datos que son independientes de los controles. Para obtener más información, consulte [enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Los controles host son versiones extendidos de objetos nativos en los modelos de objetos de Excel y Word. A diferencia de los objetos nativos, los controles host se pueden enlazar directamente a objetos de datos administrados. Para obtener más información, consulte [elementos Host y hospedar información general sobre controles](../vsto/host-items-and-host-controls-overview.md) y [Windows Forms a los controles de información general sobre documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## <a name="access-cached-data-on-the-server"></a>Acceso a los datos en el servidor en caché  
 Para obtener acceso a datos almacenados en caché en un documento, puede usar el <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase. Esta clase forma parte de la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], y se puede usar en un servidor sin ejecutar Excel o Word. Cuando el usuario abre el documento después de modificar los datos en caché, todos los controles que están enlazados a los datos se sincronizan automáticamente con los cambios y se presenta al usuario con los datos actualizados. Para obtener más información, consulte [tener acceso a datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Excel y Word no son necesarios para escribir en los datos en el servidor, sólo para verlo en el cliente. Excel y Word no incluso deben instalarse en el servidor. Esto proporciona una mejor escalabilidad y la capacidad para realizar el rápido procesamiento por lotes de documentos que contienen las Islas de datos.  
  
## <a name="data-caching-for-offline-use"></a>Almacenamiento en caché para su uso sin conexión de datos  
 Almacenar datos en la isla de datos permite escenarios sin conexión. Cuando un usuario en primer lugar abre un documento o solicita el documento del servidor, la isla de datos se rellena con los datos más recientes. La isla de datos se almacena en caché en el documento y, a continuación, está disponible sin conexión. El usuario (y el código) pueden manipular los datos, aunque no está disponible ninguna conexión activa. Cuando el usuario vuelve a conectar, se pueden propagar los cambios a los datos en un origen de datos del servidor.  
  
## <a name="cached-data-and-custom-xml-parts-compared"></a>Datos almacenados en caché y en comparación con los elementos XML personalizados  
 Elementos XML personalizados se introdujeron en 2007 Microsoft Office system como una forma de almacenar fragmentos arbitrarios de XML en un documento. Aunque los elementos XML personalizados son útiles en muchos de los mismos escenarios que la caché de datos, hay algunas diferencias entre la isla de datos y elementos XML personalizados. Para obtener más información acerca de los elementos XML personalizados, vea [información general de elementos XML personalizados](../vsto/custom-xml-parts-overview.md).  
  
 En la tabla siguiente se enumera algunas de las diferencias y similitudes.  
  
||Caché de datos|Elementos XML personalizados|  
|-|----------------|----------------------|  
|¿Las aplicaciones de Office pueden usarlas?|Personalizaciones de nivel de documento para las siguientes aplicaciones:<br /><br /> -Excel<br />-Word|Soluciones de nivel de documento y el nivel de aplicación para las siguientes aplicaciones:<br /><br /> -Excel<br />-PowerPoint<br />-Word|  
|¿Qué tipos de datos puede almacenar?|Cualquier objeto público en el ensamblado de personalización que cumple determinados requisitos. Para obtener más información, consulte [almacenar en caché datos](../vsto/caching-data.md).|Los datos XML.|  
|¿Puede obtener acceso a los datos sin iniciar aplicaciones de Microsoft Office?|Sí, mediante el uso de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase proporcionada por el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|Sí, mediante las clases en el <xref:System.IO.Packaging> espacio de nombres, o mediante el SDK de formato XML abierto.|  
  
## <a name="see-also"></a>Vea también  
 [Datos en soluciones de Office](../vsto/data-in-office-solutions.md)   
 [Arquitectura de soluciones de Office en Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  