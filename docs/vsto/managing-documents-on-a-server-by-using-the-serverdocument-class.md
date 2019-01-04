---
title: Administrar documentos en un servidor mediante la clase ServerDocument
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bcaebef3edcdf742bc56915d0209f3f61ee63df8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53903255"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>Administrar documentos en un servidor mediante la clase ServerDocument
  Puede usar el `ServerDocument` clase en el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] para administrar varios aspectos de las personalizaciones de nivel de documento, incluso si no están instalado Microsoft Office Word y Microsoft Office Excel. Puede realizar las siguientes tareas:  
  
- Acceso y modificar datos en la caché de datos de un documento o libro. Para obtener más información, consulte [trabajar con datos almacenados en caché en el documento](#CachedData).  
  
- Administrar el ensamblado de personalización que está asociado a un documento. Para obtener más información, consulte [administrar la personalización del documento](#CustomizationInfo).  
  
  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understand-the-serverdocument-class"></a>Averigüe la clase ServerDocument  
 La `ServerDocument` clase está diseñada para usarse en equipos que no tienen instalado Office. Por lo tanto, normalmente se utiliza esta clase en las aplicaciones que no se integran con Office, como proyectos de consola o los proyectos de Windows Forms, en lugar de los proyectos de Office. Use la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase en el *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* ensamblado.  
  
 El `ServerDocument` clase puede usarse para operar en personalizaciones de nivel de documento que se crearon mediante el uso de [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
 Para obtener más información acerca de Visual Studio 2010 Tools para Office Runtime y las extensiones de Office para .NET Framework, vea [Visual Studio Tools para Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  Si tiene una aplicación heredada que usa el `ServerDocument` clase en el `Visual Studio Tools for Office` system (versión 3.0 en tiempo de ejecución), el `Visual Studio Tools for Office` system (versión 3.0 runtime) debe instalarse en equipos que ejecutan la aplicación. El `Visual Studio 2010 Tools for Office runtime` no se puede ejecutar estas aplicaciones.  
  
##  <a name="CachedData"></a> Trabajar con datos almacenados en caché en el documento  
 La `ServerDocument` clase proporciona miembros que se puede utilizar para trabajar con la caché de datos de documentos personalizados. Para obtener más información acerca de los datos almacenados en caché, consulte [almacenar en caché datos](../vsto/caching-data.md) y [tener acceso a datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 En la tabla siguiente se enumera a los miembros que se puede usar para trabajar con datos almacenados en caché.  
  
|Tarea|Miembro para usar|  
|----------|-------------------|  
|Para determinar si un documento tiene una caché de datos.|El método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> .|  
|Para obtener acceso a los datos en caché en un documento.<br /><br /> Para obtener más información, consulte [tener acceso a datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md).|Propiedad <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>|  
  
##  <a name="CustomizationInfo"></a> Administrar la personalización del documento  
 Puede usar miembros de la `ServerDocument` clase para administrar el ensamblado de personalización que está asociado a un documento. Por ejemplo, puede quitar mediante programación la personalización de un documento para que el documento ya no forma parte de una personalización.  
  
 En la tabla siguiente se enumera a los miembros que se puede usar para administrar el ensamblado de personalización.  
  
|Tarea|Miembro para usar|  
|----------|-------------------|  
|Para determinar si un documento forma parte de una personalización de nivel de documento.|El método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> .|  
|Para adjuntar una personalización a un documento en tiempo de ejecución mediante programación.<br /><br /> Para obtener más información, vea [Cómo: Adjuntar extensiones de código administrado a documentos](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Uno de los <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> métodos.|  
|Para quitar mediante programación una personalización de un documento en tiempo de ejecución.<br /><br /> Para obtener más información, vea [Cómo: Quitar extensiones de código administrado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|El método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> .|  
|Para obtener la dirección URL del manifiesto de implementación que está asociado con el documento.|Propiedad <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>|  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Adjuntar extensiones de código administrado a documentos](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Cómo: Quitar extensiones de código administrado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio Tools para Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Almacenar datos en caché](../vsto/caching-data.md)  
