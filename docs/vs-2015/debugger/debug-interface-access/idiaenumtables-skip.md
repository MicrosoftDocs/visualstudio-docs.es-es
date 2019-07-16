---
title: IDiaEnumTables::Skip | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Skip method
ms.assetid: 5c9db956-0654-4f1a-8775-530aa980d8ec
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4498789b3497ea70faf9948fcf0d03c6196f250e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68161456"
---
# <a name="idiaenumtablesskip"></a>IDiaEnumTables::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Omite un número especificado de las tablas de una secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] El número de tablas en la secuencia de enumeración que se omitirán.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` si no hay ningún más tablas que se omitirán.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
