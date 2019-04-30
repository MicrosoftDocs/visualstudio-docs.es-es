---
title: IRemoteDebugApplicationEx:RevokeBreak | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:RevokeBreak
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:RevokeBreak
ms.assetid: 1f077860-0a39-4ec9-b676-ae0712819c7b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0992eb5637434ccdf0dbf4fa6e436c87ae3fdd6c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788409"
---
# <a name="iremotedebugapplicationexrevokebreak"></a>IRemoteDebugApplicationEx:RevokeBreak

Revoca un comando de interrupción.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT RevokeBreak( );
```

### <a name="parameters"></a>Parámetros

Ninguno.

## <a name="return-value"></a>Valor devuelto

El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.

|Valor|Descripción|
|-----------|-----------------|
|`S_OK`|El método se realizó correctamente.|

## <a name="see-also"></a>Vea también

- [IRemoteDebugApplicationEx (Interfaz)](iremotedebugapplicationex-interface.md)