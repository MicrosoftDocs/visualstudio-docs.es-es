---
title: IManagedAddin::Unload
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: db805aa1e00d672b4a0579e546a6827e9135b909
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673969"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Se llama a este elemento justo antes de descargar un complemento VSTO administrado.  
  
## <a name="syntax"></a>Sintaxis  
  
```csharp
HRESULT Unload();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT que indica si el método se ha completado correctamente.  
  
## <a name="remarks"></a>Comentarios  
 No se llama a este método con las versiones actuales de Microsoft Office. Este método está reservado para un uso futuro.  
  
## <a name="see-also"></a>Vea también  
 [Interfaz IManagedAddin](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Load](../vsto/imanagedaddin-load.md)  
  
  