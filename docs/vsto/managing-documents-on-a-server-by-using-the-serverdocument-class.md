---
title: Administrar documentos en un servidor mediante la clase ServerDocument | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: ef676de4ff352a557019f68037203364a97834d1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="managing-documents-on-a-server-by-using-the-serverdocument-class"></a>Administrar documentos en un servidor mediante la clase ServerDocument
  Puede usar la clase ServerDocument en el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] para administrar varios aspectos de las personalizaciones de nivel de documento, incluso si no están instalado Microsoft Office Word y Microsoft Office Excel. Puede realizar las siguientes tareas:  
  
-   Acceder y modificar datos en la caché de datos de un documento o libro. Para obtener más información, consulte [trabajar con almacenado en memoria caché datos en el documento](#CachedData).  
  
-   Administrar el ensamblado de personalización que está asociado a un documento. Para obtener más información, consulte [administrar la personalización del documento](#CustomizationInfo).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understanding-the-serverdocument-class"></a>Descripción de la clase ServerDocument  
 La clase ServerDocument está diseñada para usarse en equipos que no tienen instalado Office. Por lo tanto, normalmente se utiliza esta clase en aplicaciones que no se integran con Office, como proyectos de consola o proyectos de Windows Forms, en lugar de proyectos de Office. Use la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase en el ensamblado Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
 La clase ServerDocument puede usarse para operar en personalizaciones de nivel de documento que se crearon mediante el uso de [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
 Para obtener más información acerca de Visual Studio 2010 Tools para Office Runtime y las extensiones de Office para .NET Framework, vea [Visual Studio Tools para Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  Si tiene una aplicación heredada que utiliza la clase ServerDocument en Visual Studio Tools para Office system (versión 3.0 Runtime), Visual Studio Tools para Office system (versión 3.0 Runtime) debe instalarse en equipos que ejecutan la aplicación. Visual Studio 2010 Tools para Office Runtime no se puede ejecutar estas aplicaciones.  
  
##  <a name="CachedData"></a> Trabajar con datos almacenados en caché en el documento  
 La clase ServerDocument proporciona a miembros que se puede utilizar para trabajar con la caché de datos en documentos personalizados. Para obtener más información acerca de los datos almacenados en caché, vea [almacenar datos en caché](../vsto/caching-data.md) y [acceso a datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 En la tabla siguiente se enumera a los miembros que se puede usar para trabajar con datos almacenados en caché.  
  
|Tarea|Miembro para usar|  
|----------|-------------------|  
|Para determinar si un documento tiene una caché de datos.|Método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A>.|  
|Para obtener acceso a los datos en caché en un documento.<br /><br /> Para obtener más información, consulta [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md).|Propiedad <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>|  
  
##  <a name="CustomizationInfo"></a> Administrar la personalización del documento  
 Puede utilizar a los miembros de la clase ServerDocument para administrar el ensamblado de personalización que está asociado a un documento. Por ejemplo, puede quitar mediante programación la personalización de un documento para que el documento ya no forma parte de una personalización.  
  
 En la tabla siguiente se enumera a los miembros que puede usar para administrar el ensamblado de personalización.  
  
|Tarea|Miembro para usar|  
|----------|-------------------|  
|Para determinar si un documento es parte de una personalización de nivel de documento.|Método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A>.|  
|Para asociar mediante programación una personalización a un documento en tiempo de ejecución.<br /><br /> Para obtener más información, vea [Cómo: Adjuntar extensiones de código administrado a documentos](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Uno de los <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> métodos.|  
|Para quitar mediante programación una personalización de un documento en tiempo de ejecución.<br /><br /> Para obtener más información, consulte [Cómo: quitar extensiones de código administrado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|Método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>.|  
|Para obtener la dirección URL del manifiesto de implementación que está asociado con el documento.|Propiedad <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>|  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Adjuntar extensiones de código administrado a documentos](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Cómo: quitar extensiones de código administrado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Almacenamiento de datos en caché](../vsto/caching-data.md)  
  