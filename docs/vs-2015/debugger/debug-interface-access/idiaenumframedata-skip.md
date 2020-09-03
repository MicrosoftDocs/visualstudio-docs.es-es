---
title: IDiaEnumFrameData::Skip | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Skip method
ms.assetid: 67140b4c-7125-4895-932d-42412326da29
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ff8b58f6d36e9ce9759e2672f7e438bc0019fc1e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179494"
---
# <a name="idiaenumframedataskip"></a>IDiaEnumFrameData::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Omite un número especificado de elementos de datos de marco en una secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 celt  
 de El número de elementos de datos de marco en la secuencia de enumeración que se va a omitir.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve si no hay `S_FALSE` más registros para omitir.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
