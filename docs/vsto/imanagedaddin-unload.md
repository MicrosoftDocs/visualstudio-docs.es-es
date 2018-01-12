---
title: IManagedAddin::Unload | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Unload method
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: aadf5235eb64c14b14f7241b4fd2b89b0a9887da
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Se llama a este elemento justo antes de descargar un complemento VSTO administrado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT Unload();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT que indica si el método se ha completado correctamente.  
  
## <a name="remarks"></a>Comentarios  
 No se llama a este método con las versiones actuales de Microsoft Office. Este método está reservado para un uso futuro.  
  
## <a name="see-also"></a>Vea también  
 [IManagedAddin Interface](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Load](../vsto/imanagedaddin-load.md)  
  
  