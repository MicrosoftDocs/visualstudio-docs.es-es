---
title: Incrustación simplificada ( Simplified Inbedding) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9bc9619ae1ed75aed3656ff014296f7c7d88fa0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700073"
---
# <a name="simplified-embedding"></a>Inserción simplificada
La incrustación simplificada se habilita en un editor cuando su objeto de vista [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]de documento <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> está parented to (es decir, hecho un elemento secundario de) y la interfaz se implementa para controlar sus comandos de ventana. Los editores de incrustación simplificados no pueden hospedar controles activos. Los objetos utilizados para crear un editor con incrustación simplificada se muestran en la siguiente ilustración.

 ![Gráfico simplificado del Editor de incrustaciones](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") Editor con incrustación simplificada

> [!NOTE]
> De los objetos de `CYourEditorFactory` esta ilustración, solo se requiere el objeto para crear un editor estándar basado en archivos. Si va a crear un editor personalizado, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>no es necesario implementar , porque es probable que el editor tenga su propio mecanismo de persistencia privada. Para los editores no personalizados, sin embargo, debe hacerlo.

 Todas las interfaces implementadas para crear un editor `CYourEditorDocument` con incrustación simplificada están contenidas en el objeto. Sin embargo, para admitir varias vistas de datos de documento, divida las interfaces en datos independientes y vea objetos como se indica en la tabla siguiente.

|Interfaz|Ubicación de la interfaz|Uso|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Ver|Proporciona conexión a la ventana primaria.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Ver|Maneja comandos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Ver|Habilita las actualizaciones de la barra de estado.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Ver|Habilita los elementos **de Toolbox.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|data|Envía notificaciones cuando cambia el archivo.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|data|Habilita la función Guardar como para un tipo de archivo.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|data|Habilita la persistencia del documento.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|data|Permite la supresión de eventos de cambio de archivo, como la activación de recarga.|
