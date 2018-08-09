---
title: Administración de deshacer y rehacer mediante la API heredada | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: be60b3f0dd45a40663770b4b0debe8023e277f32
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638077"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>Administración de deshacer y rehacer mediante el uso de la API heredada
Los editores deben admitir las operaciones de deshacer que permiten a los usuarios revertir sus cambios recientes cuando modifica el código. La mayoría de editores implementados en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] puede tener soporte para deshacer automáticamente proporcionada por el entorno de desarrollo integrado (IDE).  
  
## <a name="in-this-section"></a>En esta sección  
 [Cómo: implementar la administración de deshacer](../extensibility/how-to-implement-undo-management.md)  
 Proporciona la capacidad de deshacer para los editores con una o varias vistas.  
  
 [Cómo: borrar la pila de deshacer](../extensibility/how-to-clear-the-undo-stack.md)  
 Describe cómo borrar una pila de deshacer.  
  
 [Cómo: usar vinculada de deshacer la administración](../extensibility/how-to-use-linked-undo-management.md)  
 Incorpora la administración de la fase de reversión vinculado en el editor.  
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Proporciona administración de la fase de reversión para un editor que admite varias vistas.  
