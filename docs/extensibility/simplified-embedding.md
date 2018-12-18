---
title: Simplifica la incrustación | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 01b06a0a63059c39035d15221feb201d3674d4a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142937"
---
# <a name="simplified-embedding"></a>Simplifica la incrustación de objetos
Incrustación simplificada está habilitada en un editor cuando su objeto de vista de documento tiene un elemento primario (es decir, realizar un elemento secundario de) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]y el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaz se implementa para controlar su ventana de comandos. Editores de incrustación simplificados no pueden hospedar otros controles activos. Los objetos usados para crear un editor con la incrustación simplificada se muestran en la siguiente ilustración.  
  
 ![Gráfico de Editor de elementos incrustado simplificado](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
Editor con la incrustación simplificada  
  
> [!NOTE]
>  De los objetos en esta ilustración, solo la `CYourEditorFactory` objeto es necesario para crear un editor basado en archivos estándar. Si va a crear un editor personalizado, no se debe implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>, ya que el editor tendrá probablemente su propio mecanismo de persistencia privado. Para los editores no personalizado, sin embargo, debe hacerlo.  
  
 Todas las interfaces implementadas para crear un editor con la incrustación simplificada se encuentran en la `CYourEditorDocument` objeto. Sin embargo, para admitir varias vistas de datos del documento, divida las interfaces en objetos independientes de datos y la vista como se indica en la tabla siguiente.  
  
|Interfaz|Ubicación de interfaz|Usar|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Ver|Proporciona la conexión a la ventana primaria.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Ver|Controla los comandos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Ver|Habilita las actualizaciones de la barra de estado.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Ver|Permite **cuadro de herramientas** elementos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Datos|Envía notificaciones cuando los cambios del archivo.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Datos|Habilita la característica Guardar como para un tipo de archivo.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Datos|Habilita la persistencia del documento.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Datos|Permite la supresión de eventos de cambio de archivo, como activar volver a cargar.|