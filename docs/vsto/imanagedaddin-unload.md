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
ms.openlocfilehash: 283fd069e0de72af92f7999871190c6c8a0d345b
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Se llama a este elemento justo antes de descargar un complemento VSTO administrado.  
  
## <a name="syntax"></a>Sintaxis  
  
```c++
HRESULT Unload();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT que indica si el método se ha completado correctamente.  
  
## <a name="remarks"></a>Comentarios  
 No se llama a este método con las versiones actuales de Microsoft Office. Este método está reservado para un uso futuro.  
  
## <a name="see-also"></a>Vea también  
 [Interfaz IManagedAddin](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Load](../vsto/imanagedaddin-load.md)  
  
  