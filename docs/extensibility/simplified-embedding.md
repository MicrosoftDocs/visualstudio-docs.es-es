---
title: Incrustación simplificada | Microsoft Docs
description: Obtenga información sobre la incrustación simplificada, que se puede habilitar en un editor cuando su objeto de vista de documento es un elemento secundario de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dca3b0c11c916a1fc47e4687bfeeabee35bcdfb4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056381"
---
# <a name="simplified-embedding"></a>Inserción simplificada
La incrustación simplificada está habilitada en un editor cuando su objeto de vista de documento es primario (es decir, se ha convertido en un elemento secundario de) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaz se implementa para controlar sus comandos de ventana. Los editores de incrustación simplificados no pueden hospedar controles activos. En la ilustración siguiente se muestran los objetos que se usan para crear un editor con incrustación simplificada.

 ![Gráfico del editor de incrustación simplificada](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") Editor con incrustación simplificada

> [!NOTE]
> De los objetos de esta ilustración, solo el `CYourEditorFactory` objeto es necesario para crear un editor estándar basado en archivos. Si está creando un editor personalizado, no es necesario que implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> , ya que el editor probablemente tendrá su propio mecanismo de persistencia privado. No obstante, para los editores no personalizados, debe hacerlo.

 Todas las interfaces implementadas para crear un editor con incrustación simplificada están contenidas en el `CYourEditorDocument` objeto. Sin embargo, para admitir varias vistas de datos de documento, divida las interfaces en datos independientes y vea objetos, tal como se indica en la tabla siguiente.

|Interfaz|Ubicación de la interfaz|Usar|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Ver|Proporciona conexión a la ventana primaria.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Ver|Controla los comandos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Ver|Habilita las actualizaciones de la barra de estado.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Ver|Habilita los elementos del **cuadro de herramientas** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|data|Envía notificaciones cuando cambia el archivo.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|data|Habilita la característica guardar como para un tipo de archivo.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|data|Habilita la persistencia del documento.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|data|Permite la supresión de eventos de cambio de archivo, como el desencadenamiento de recarga.|
