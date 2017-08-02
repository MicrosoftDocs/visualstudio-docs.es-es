---
title: "Incrustaci&#243;n simplificada | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores personalizados de [Visual Studio SDK], - sencillo ver incrustación"
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Incrustaci&#243;n simplificada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La incrustación simplificada está habilitada en un editor cuando el objeto de vista del documento \(es decir, se crea un elemento secundario de\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]relacionada con, y la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> se implementa para controlar los comandos de la ventana.  Simplificado insertar editores no puede hospedar controles activos del host.  Los objetos utilizados para crear un editor con la incrustación simplificada se muestran en la siguiente ilustración.  
  
 ![Gráfico del Editor de elementos incrustado simplificado](~/extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
editor con la incrustación simplificada  
  
> [!NOTE]
>  De los objetos en esta ilustración, solo el objeto de `CYourEditorFactory` es necesario crear un editor basado en archivos estándar.  Si está creando un editor personalizado, no es necesario implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>, como el editor tendrá probablemente su propio mecanismo privado de persistencia.  Para los editores de categorías no personalizados, sin embargo, debe hacerlo.  
  
 Todas las interfaces implementadas para crear un editor con la incrustación simplificada contenidas en el objeto de `CYourEditorDocument` .  Sin embargo, para admitir varias vistas de los datos del documento, divida las interfaces sobre datos independientes y objetos de vista como se indica en la tabla siguiente.  
  
|Interfaz|Ubicación de interfaz|Utilice|  
|--------------|---------------------------|-------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|View|proporciona la conexión a la ventana primaria.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|View|Controla comandos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|View|Actualizaciones de la barra de estado de permisos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|View|Elementos de **Cuadro de herramientas** de permisos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Datos|Envía notificaciones cuando cambie el archivo.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Datos|Habilita el Guardar como característica para un tipo de archivo.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Datos|Habilita la persistencia del documento.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Datos|Permite la supresión de eventos de cambio del archivo, como desencadenar reload.|