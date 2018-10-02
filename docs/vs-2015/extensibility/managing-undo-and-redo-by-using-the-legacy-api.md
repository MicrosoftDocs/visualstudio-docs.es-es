---
title: Administración de deshacer y rehacer mediante la API heredada | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0bb1cc883941c8365e4d4341c93084beaef44d48
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579089"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Administración de deshacer y rehacer mediante la API heredada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [administración de deshacer y rehacer mediante la API heredada](https://docs.microsoft.com/visualstudio/extensibility/managing-undo-and-redo-by-using-the-legacy-api).  
  
Los editores deben admitir las operaciones de deshacer que permiten a los usuarios revertir sus cambios recientes cuando modifica el código. La mayoría de editores implementados en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] puede tener soporte para deshacer automáticamente proporcionada por el entorno de desarrollo integrado (IDE).  
  
## <a name="in-this-section"></a>En esta sección  
 [Cómo: Implementar la administración de la fase de reversión](../extensibility/how-to-implement-undo-management.md)  
 Proporciona la capacidad de deshacer para los editores con una o varias vistas.  
  
 [Cómo: Borrar la pila de la fase de reversión](../extensibility/how-to-clear-the-undo-stack.md)  
 Describe cómo borrar una pila de deshacer.  
  
 [Cómo: Usar la administración vinculada de la fase de reversión](../extensibility/how-to-use-linked-undo-management.md)  
 Incorpora la administración de la fase de reversión vinculado en el editor.  
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Proporciona administración de la fase de reversión para un editor que admite varias vistas.  
  
## <a name="related-sections"></a>Secciones relacionadas

