---
title: "Los datos en las personalizaciones de nivel de documento en caché | Documentos de Microsoft"
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
helpviewer_keywords:
- data islands [Office development in Visual Studio]
- view [Office development in Visual Studio]
- caching data [Office development in Visual Studio], about caching data
- data caching [Office development in Visual Studio], about data caching
- data [Office development in Visual Studio], cache
- data [Office development in Visual Studio], document-level solutions
- document-level customizations [Office development in Visual Studio], data model
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1fe9465c3f238941ace0d5b6fc438c7d5d93ec64
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="cached-data-in-document-level-customizations"></a>Datos almacenados en caché en las personalizaciones de nivel de documento
  Es un objetivo principal de las personalizaciones de nivel de documento separar los datos de vista de documentos de Office. Los datos hacen referencia a la información que se almacena en el documento, incluidos números y texto. Vista hace referencia a la interfaz de usuario y el modelo de objetos de Microsoft Office Word y Microsoft Office Excel.  
  
 Visual Studio separa los datos de la vista en las personalizaciones de nivel de documento permitiendo que los datos que se incrusta como un *isla de datos*, también denominado el *memoria caché de datos*. Puede leer o modificar los datos directamente sin iniciar Word o Excel. Esto es útil cuando necesita modificar datos de documentos en un servidor que no tiene instalado Microsoft Office. Word y Excel están diseñados para su uso en entornos de cliente; no están diseñados para ejecutarse en un servidor.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Para obtener más información acerca de las personalizaciones de nivel de documento, consulte [información general sobre el desarrollo de soluciones de Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md) y [arquitectura de las personalizaciones de nivel de documento de](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="understanding-the-cached-data-programming-model"></a>Descripción del modelo de programación de datos almacenados en caché  
 La isla de datos puede contener cualquier objeto de la solución que cumpla ciertos requisitos. Estos objetos incluyen <xref:System.Data.DataSet> objetos, <xref:System.Data.DataTable> objetos y cualquier otro objeto que se puede serializar mediante el <xref:System.Xml.Serialization.XmlSerializer> clase. Para obtener más información, consulte vea [almacenar datos en caché](../vsto/caching-data.md).  
  
 Para proporcionar la vista de los datos en caché, puede enlazar controles de formularios Windows Forms y *controles host* en el documento a los objetos de la isla de datos. Enlace de datos entre la isla de datos y los controles enlazados a datos mantiene a ambos sincronizados. También puede agregar código de validación a los datos que son independientes de los controles. Para obtener más información, consulte [enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Controles host son versiones extendidos de objetos nativos de los modelos de objetos de Excel y Word. A diferencia de los objetos nativos, los controles de host se pueden enlazar directamente a los objetos de datos administrados. Para obtener más información, vea [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md) y [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## <a name="accessing-cached-data-on-the-server"></a>Obtener acceso a datos almacenados en caché en el servidor  
 Para obtener acceso a datos almacenados en caché en un documento, puede usar el <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase. Esta clase forma parte de la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], y se puede utilizar en un servidor sin ejecutar Excel o Word. Cuando el usuario abre el documento después de modificar los datos en caché, todos los controles que están enlazados a los datos se sincronizan automáticamente con los cambios y se presenta al usuario con los datos actualizados. Para obtener más información, consulta [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 Excel y Word no son necesarios para escribir en los datos en el servidor, sólo para verlos en el cliente. Excel y Word no es necesario esté instalado en el servidor. Esto proporciona una mayor escalabilidad y la capacidad para realizar el rápido procesamiento por lotes de documentos que contienen islas de datos.  
  
## <a name="data-caching-for-offline-use"></a>Datos en caché para su uso sin conexión  
 Almacenar datos en la isla de datos permite escenarios sin conexión. Cuando un usuario primero abre un documento o solicita el documento del servidor, la isla de datos se rellena con los datos más recientes. La isla de datos se almacena en caché en el documento y, a continuación, está disponible sin conexión. El usuario (y el código) pueden manipular los datos, incluso si no hay ninguna conexión activa. Cuando el usuario vuelve a conectarse, se pueden propagar los cambios a los datos en un origen de datos del servidor.  
  
## <a name="cached-data-and-custom-xml-parts-compared"></a>Datos almacenados en caché y los elementos XML personalizados en comparación con  
 Elementos XML personalizados se introdujeron en 2007 Microsoft Office system como una manera de almacenar fragmentos arbitrarios de XML en un documento. Aunque los elementos XML personalizados son útiles en muchos de los mismos escenarios como la caché de datos, hay algunas diferencias entre la isla de datos y elementos XML personalizados. Para obtener más información acerca de los elementos XML personalizados, vea [información general sobre elementos XML personalizados](../vsto/custom-xml-parts-overview.md).  
  
 En la tabla siguiente se enumera algunas de las diferencias y similitudes.  
  
||Memoria caché de datos|Elementos XML personalizados|  
|-|----------------|----------------------|  
|¿Las aplicaciones de Office pueden utilizarlos?|Personalizaciones de nivel de documento para las siguientes aplicaciones:<br /><br /> -Excel<br />-Word|Soluciones de nivel de documento y de nivel de aplicación para las siguientes aplicaciones:<br /><br /> -Excel<br />-PowerPoint<br />-Word|  
|¿Qué tipos de datos puede almacenar?|Cualquier objeto público en el ensamblado de personalización que cumpla ciertos requisitos. Para obtener más información, consulta [Caching Data](../vsto/caching-data.md).|Los datos XML.|  
|¿Puede tener acceso a los datos sin iniciar aplicaciones de Microsoft Office?|Sí, mediante el uso de la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase proporcionada por el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|Sí, mediante clases en el <xref:System.IO.Packaging> espacio de nombres, o mediante el SDK de formato XML abierto.|  
  
## <a name="see-also"></a>Vea también  
 [Datos en soluciones de Office](../vsto/data-in-office-solutions.md)   
 [Arquitectura de las soluciones de Office en Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  