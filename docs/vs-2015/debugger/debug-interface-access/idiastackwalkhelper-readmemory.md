---
title: IDiaStackWalkHelper::readMemory | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8bef01cd29bb2312bd682f2f1f1150ee78da293e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999219"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lee un bloque de datos de imagen del archivo ejecutable en la memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
