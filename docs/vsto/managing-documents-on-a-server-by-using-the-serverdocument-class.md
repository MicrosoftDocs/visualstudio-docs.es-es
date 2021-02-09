---
title: Administrar documentos en un servidor mediante la clase ServerDocument
description: Obtenga información sobre cómo puede usar la clase ServerDocument en el Visual Studio Tools para Office Runtime para administrar varios aspectos de las personalizaciones de nivel de documento.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 17a25ca382cfbbc762731afacaa628de616cfe1c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879480"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>Administrar documentos en un servidor mediante la clase ServerDocument
  Puede utilizar la `ServerDocument` clase en [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] para administrar varios aspectos de las personalizaciones de nivel de documento, incluso si Microsoft Office Word y Microsoft Office Excel no están instalados. Puede realizar las siguientes tareas:

- Obtener acceso y modificar los datos de la memoria caché de datos de un documento o un libro. Para obtener más información, vea [trabajar con datos almacenados en caché en el documento](#CachedData).

- Administrar el ensamblado de personalización que está asociado a un documento. Para obtener más información, vea [administrar la personalización de documentos](#CustomizationInfo).

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="understand-the-serverdocument-class"></a>Descripción de la clase ServerDocument
 La `ServerDocument` clase está diseñada para usarse en equipos que no tienen instalado Office. Por lo tanto, esta clase se utiliza normalmente en aplicaciones que no se integran con Office, como proyectos de consola o proyectos de Windows Forms, en lugar de proyectos de Office. Utilice la <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> clase en el ensamblado de *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* .

 La `ServerDocument` clase se puede utilizar para operar en las personalizaciones de nivel de documento que se crearon con [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] .

 Para obtener más información sobre el tiempo de ejecución de las herramientas de Visual Studio 2010 para Office y las extensiones de Office para el .NET Framework, consulte [información general sobre el tiempo de ejecución de Visual Studio Tools para Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

> [!NOTE]
> Si tiene una aplicación heredada que utiliza la `ServerDocument` clase en el `Visual Studio Tools for Office` sistema (versión 3,0 en tiempo de ejecución), el `Visual Studio Tools for Office` sistema (tiempo de ejecución de la versión 3,0) debe estar instalado en los equipos que ejecutan la aplicación. `Visual Studio 2010 Tools for Office runtime`No puede ejecutar estas aplicaciones.

## <a name="work-with-cached-data-in-the-document"></a><a name="CachedData"></a> Trabajar con los datos en caché del documento
 La `ServerDocument` clase proporciona miembros que se pueden usar para trabajar con la memoria caché de datos en documentos personalizados. Para obtener más información sobre los datos en caché, vea [almacenar datos en caché](../vsto/caching-data.md) y [obtener acceso a los datos de los documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md).

 En la tabla siguiente se enumeran los miembros que se pueden usar para trabajar con datos almacenados en caché.

|Tarea|Miembro para usar|
|----------|-------------------|
|Para determinar si un documento tiene una memoria caché de datos.|El método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> .|
|Para tener acceso a los datos almacenados en caché de un documento.<br /><br /> Para obtener más información, vea [obtener acceso a los datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md).|Propiedad <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>|

## <a name="manage-the-document-customization"></a><a name="CustomizationInfo"></a> Administrar la personalización de documentos
 Puede utilizar miembros de la `ServerDocument` clase para administrar el ensamblado de personalización que está asociado a un documento. Por ejemplo, puede quitar mediante programación la personalización de un documento para que el documento ya no forme parte de una personalización.

 En la tabla siguiente se enumeran los miembros que se pueden usar para administrar el ensamblado de personalización.

|Tarea|Miembro para usar|
|----------|-------------------|
|Para determinar si un documento forma parte de una personalización de nivel de documento.|El método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> .|
|Para adjuntar mediante programación una personalización a un documento en tiempo de ejecución.<br /><br /> Para obtener más información, vea [Cómo: adjuntar extensiones de código administrado a documentos](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Uno de los <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> métodos.|
|Para quitar mediante programación una personalización de un documento en tiempo de ejecución.<br /><br /> Para obtener más información, vea [Cómo: quitar extensiones de código administrado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|El método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> .|
|Para obtener la dirección URL del manifiesto de implementación que está asociado al documento.|Propiedad <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>|

## <a name="see-also"></a>Vea también
- [Cómo: adjuntar extensiones de código administrado a documentos](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
- [Cómo: quitar extensiones de código administrado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Información general sobre el tiempo de ejecución de Visual Studio Tools para Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Datos de caché](../vsto/caching-data.md)
