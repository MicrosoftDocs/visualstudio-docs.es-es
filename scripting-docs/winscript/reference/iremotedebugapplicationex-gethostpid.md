---
title: IRemoteDebugApplicationEx:GetHostPid | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:GetHostPid
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:GetHostPid
ms.assetid: 4cf9f46c-29cf-4201-87f0-5b1ddbed2f2b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62033169e10585015b5f1439067aa0cbc42447a4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54754645"
---
# <a name="iremotedebugapplicationexgethostpid"></a>IRemoteDebugApplicationEx:GetHostPid

Devuelve el identificador de proceso para la aplicación host.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetHostPid(
   DWORD*  dwHostPid
);
```

### <a name="parameters"></a>Parámetros

`dwHostPid`

[out] El identificador de proceso de host.

## <a name="return-value"></a>Valor devuelto

El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.

|Valor|Descripción|
|-----------|-----------------|
|`S_OK`|El método se realizó correctamente.|

## <a name="remarks"></a>Comentarios

Utilizado por el IDE.

## <a name="see-also"></a>Vea también

- [IRemoteDebugApplicationEx (Interfaz)](iremotedebugapplicationex-interface.md)