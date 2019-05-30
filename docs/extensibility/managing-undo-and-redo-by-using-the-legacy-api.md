---
title: Administración de deshacer y rehacer mediante la API heredada | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a223d23cb792f13f1df9f869a540ffa61f50f9b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340644"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>Administración de deshacer y rehacer mediante el uso de la API heredada
Los editores deben admitir las operaciones de deshacer que permiten a los usuarios revertir sus cambios recientes cuando modifica el código. La mayoría de editores implementados en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] puede tener soporte para deshacer automáticamente proporcionada por el entorno de desarrollo integrado (IDE).

## <a name="in-this-section"></a>En esta sección
- [Cómo: Implementar la administración de deshacer](../extensibility/how-to-implement-undo-management.md) proporciona capacidad de deshacer para editores con una o varias vistas.

- [Cómo: Borrar la pila de deshacer](../extensibility/how-to-clear-the-undo-stack.md) se describe cómo borrar una pila de deshacer.

- [Cómo: Usar la administración de la fase de reversión vinculado](../extensibility/how-to-use-linked-undo-management.md) Incorporates vinculada de deshacer la administración en el editor.

## <a name="reference"></a>Referencia
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> Proporciona administración de la fase de reversión para un editor que admite varias vistas.
