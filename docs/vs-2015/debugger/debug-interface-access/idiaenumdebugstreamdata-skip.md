---
title: IDiaEnumDebugStreamData::Skip | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Skip method
ms.assetid: 106ae1d3-a379-4077-babf-2665e697b0c4
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e71d9631949fc9ae22f80b1b5be3b0662d918ddd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187356"
---
# <a name="idiaenumdebugstreamdataskip"></a>IDiaEnumDebugStreamData::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Omite un número especificado de registros en una secuencia enumerada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 celt  
 de Número de registros que se van a omitir en la secuencia enumerada.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve si no hay `S_FALSE` más registros para omitir.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
