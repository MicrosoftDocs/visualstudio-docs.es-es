---
title: "Administrar documentos en un servidor mediante la clase ServerDocument | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "documentos [desarrollo de Office en Visual Studio], administrar en servidor"
  - "documentos de Office [desarrollo de Office en Visual Studio], administrar en servidor"
  - "ServerDocument (clase), administrar documentos en servidores"
ms.assetid: 1ac90e89-d07d-4874-9d24-6741d6679a21
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Administrar documentos en un servidor mediante la clase ServerDocument
  Puede utilizar la clase ServerDocument en el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] para administrar varios aspectos de la personalización de nivel de documento, aun cuando Microsoft Office Word y Microsoft Office Excel no estén instalados.  Puede realizar las tareas siguientes:  
  
-   Tener acceso a datos en la caché de datos de un documento o libro o modificarlos.  Para obtener más información, vea [Trabajar en el documento con datos almacenados en la memoria caché](#CachedData).  
  
-   Administrar el ensamblado de personalización asociado a un documento.  Para obtener más información, vea [Administrar la personalización de documentos](#CustomizationInfo).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Descripción de la clase ServerDocument  
 La clase ServerDocument está diseñada para usarla en los equipos que no tienen Office instalado.  Por tanto, esta clase se utiliza habitualmente en aplicaciones que no se integran con Microsoft Office, como proyectos de consola o proyectos de Windows Forms, en lugar de proyectos de Office.  Utilice la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> en el ensamblado Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
 La clase ServerDocument se puede utilizar para las personalizaciones de nivel de documento creadas mediante [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
 Para obtener más información sobre Visual Studio 2010 Tools para Office Runtime y las extensiones de Office para .NET Framework, vea [Información general sobre el Motor en tiempo de ejecución de Microsoft Visual Studio Tools para Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  Si tiene una aplicación heredada que utilice la clase ServerDocument en el sistema de Visual Studio Tools para Office \(versión 3.0 del runtime\), el sistema de Visual Studio Tools para Office \(versión 3.0 del runtime\) debe estar instalado en los equipos que ejecuten la aplicación.  Visual Studio 2010 Tools para Office Runtime no puede ejecutar estas aplicaciones.  
  
##  <a name="CachedData"></a> Trabajar en el documento con datos almacenados en la memoria caché  
 La clase ServerDocument proporciona miembros que se pueden usar para trabajar con la memoria caché de datos en documentos personalizados.  Para obtener más información sobre los datos en caché, vea [Almacenar datos en caché](../vsto/caching-data.md) y [Acceso a datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 En la tabla siguiente se enumeran los miembros que puede usar para trabajar con datos en caché.  
  
|Tarea|Miembro que se utiliza|  
|-----------|----------------------------|  
|Determinar si un documento tiene una caché de datos.|Método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A>.|  
|Tener acceso a los datos en caché en un documento.<br /><br /> Para obtener más información, vea [Acceso a datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md).|Propiedad <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>.|  
  
##  <a name="CustomizationInfo"></a> Administrar la personalización de documentos  
 Puede usar miembros de la clase ServerDocument para administrar el ensamblado de personalización asociado a un documento.  Por ejemplo, puede quitar mediante programación la personalización de un documento de forma que este ya no forme parte de una personalización.  
  
 En la tabla siguiente se enumeran los miembros que puede usar para administrar el ensamblado de personalización.  
  
|Tarea|Miembro que se utiliza|  
|-----------|----------------------------|  
|Determinar si un documento forma parte de una personalización de nivel de documento.|Método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A>.|  
|Asociar mediante programación una personalización a un documento en tiempo de ejecución.<br /><br /> Para obtener más información, vea [Cómo: Adjuntar extensiones de código administrado a documentos](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Uno de los métodos <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>.|  
|Quitar mediante programación una personalización de un documento en tiempo de ejecución.<br /><br /> Para obtener más información, vea [Cómo: Quitar extensiones de código administrado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|Método <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>.|  
|Obtener la dirección URL del manifiesto de implementación asociado con el documento.|Propiedad <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>.|  
  
## Vea también  
 [Cómo: Adjuntar extensiones de código administrado a documentos](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Cómo: Quitar extensiones de código administrado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Información general sobre el Motor en tiempo de ejecución de Microsoft Visual Studio Tools para Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Almacenar datos en caché](../vsto/caching-data.md)  
  
  