---
title: IDiaStackWalkHelper::readMemory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7d12d1da983a69f71d96bb06271bd3a971a16cbb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825742"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Lee un bloque de datos de imagen del archivo ejecutable en la memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `type`  
 [in] Un valor de la [MemoryTypeEnum (enumeración)](../../debugger/debug-interface-access/memorytypeenum.md) enumeración que especifica el tipo de memoria para leer.  
  
 va  
 [in] Dirección virtual en la imagen desde el que se va a comenzar la lectura.  
  
 `cbData`  
 [in] El tamaño del búfer de datos en bytes.  
  
 `pcbData`  
 [out] Devuelve el número de bytes leídos realmente. Si `pbData` es `NULL`, este es el número total de bytes de datos disponibles.  
  
 `pbData`  
 [in, out] Un búfer que se rellena con la memoria de lectura.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Enumeración MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md)