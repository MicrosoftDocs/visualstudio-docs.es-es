---
title: Idiastackwalkframe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 00171e470bd5dfd2a64bf7faabb0e338eceed7b1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53874671"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Lee de la imagen de memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT readMemory (   
   MemoryTypeEnum type,  
   ULONGLONG va,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `type`  
 [in] Uno de los [MemoryTypeEnum (enumeración)](../../debugger/debug-interface-access/memorytypeenum.md) valores de enumeración que especifica el tipo de memoria para tener acceso.  
  
 `va`  
 [in] Ubicación de dirección virtual de imagen a comenzar la lectura.  
  
 `cbData`  
 [in] Tamaño del búfer de datos, en bytes.  
  
 `pcbData`  
 [out] Devuelve el número de bytes devueltos. Si `data` es `NULL`, a continuación, `pcbData` contiene el número total de bytes de datos disponibles.  
  
 `data`  
 [out] Un búfer que se va a rellenar con datos de la ubicación especificada.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)