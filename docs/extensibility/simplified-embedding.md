---
title: Incrustación simplificada | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c7ef7e297b834d03d5b7b29013cbe9f18fecbc31
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54921965"
---
# <a name="simplified-embedding"></a>Inserción simplificada
Incrustación simplificada está habilitada en el editor cuando su objeto de vista de documento es un elemento principal (es decir, realiza un elemento secundario) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]y el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaz se implementa para controlar su ventana de comandos. Editores de incrustación simplificados no pueden hospedar controles activos. En la siguiente ilustración, se muestran los objetos que se utiliza para crear un editor con incrustación simplificada.  
  
 ![Gráfico de Editor con incrustación simplificada](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
Editor con incrustación simplificada  
  
> [!NOTE]
>  Los objetos de esta ilustración, sólo el `CYourEditorFactory` objeto es necesario para crear un editor basado en archivos estándar. Si va a crear un editor personalizado, no son necesarios para implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>, ya que el editor tendrá probablemente su propio mecanismo de persistencia privado. Para los editores no personalizado, sin embargo, debe hacerlo.  
  
 Todas las interfaces implementadas para crear un editor con incrustación simplificada se encuentran en el `CYourEditorDocument` objeto. Sin embargo, para admitir varias vistas de datos del documento, divida las interfaces a objetos de datos y la vista independientes como se indica en la tabla siguiente.  
  
|Interfaz|Ubicación de la interfaz|Usar|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Ver|Proporciona la conexión a la ventana primaria.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Ver|Controla los comandos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Ver|Habilita las actualizaciones de la barra de estado.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Ver|Permite **cuadro de herramientas** elementos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Datos|Envía notificaciones cuando cambia el archivo.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Datos|Habilita la característica Guardar como para un tipo de archivo.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Datos|Habilita la persistencia del documento.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Datos|Permite la supresión de eventos de cambio de archivo, como desencadenar volver a cargar.|