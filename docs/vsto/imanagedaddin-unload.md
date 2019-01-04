---
title: IManagedAddin::Unload
ms.date: 02/02/2017
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
ms.openlocfilehash: 4aa3c07ed715a6118bd053d44503607a889f3da7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53880905"
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
