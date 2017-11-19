---
title: "Administración de deshacer y rehacer mediante la API heredado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41672845d318707512472f556753f429661d008c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Administración de deshacer y rehacer mediante la API heredado
Editores deben admitir las operaciones de deshacer que permiten a los usuarios revertir sus cambios recientes cuando modifica el código. La mayoría de editores implementados en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] puede tener soporte deshacer proporciona automáticamente el entorno de desarrollo integrado (IDE).  
  
## <a name="in-this-section"></a>En esta sección  
 [Cómo: implementar la administración de deshacer](../extensibility/how-to-implement-undo-management.md)  
 Proporciona la capacidad de deshacer de editores con una o varias vistas.  
  
 [Cómo: borrar la pila de deshacer](../extensibility/how-to-clear-the-undo-stack.md)  
 Describe cómo borrar una pila de deshacer.  
  
 [Cómo: usar la administración de la acción de deshacer vinculada](../extensibility/how-to-use-linked-undo-management.md)  
 Incorpora la administración de la acción de deshacer vinculada en el editor.  
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Proporciona administración de deshacer para un editor que admite varias vistas.  
  
## <a name="related-sections"></a>Secciones relacionadas