---
title: IManagedAddin::Unload
description: Se llama a este elemento justo antes de descargar un complemento VSTO administrado.
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e45fd9e6385388b9c6bc32098cf59799618d511b
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469715"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Se llama a este elemento justo antes de descargar un complemento VSTO administrado.

## <a name="syntax"></a>Sintaxis

```csharp
HRESULT Unload();
```

## <a name="return-value"></a>Valor devuelto
 Un valor HRESULT que indica si el método se ha completado correctamente.

## <a name="remarks"></a>Observaciones
 No se llama a este método con las versiones actuales de Microsoft Office. Este método está reservado para un uso futuro.

## <a name="see-also"></a>Vea también
- [Interfaz IManagedAddin](../vsto/imanagedaddin-interface.md)
- [IManagedAddIn::Load](../vsto/imanagedaddin-load.md)
