---
title: 'Idiastackwalkframe:: ReadMemory | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: 9874972bd5d6ec72ecd36e32d4487343fa4c231e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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
 [in] Ubicación de dirección virtual en la imagen a comenzar la lectura.  
  
 `cbData`  
 [in] Tamaño del búfer de datos, en bytes.  
  
 `pcbData`  
 [out] Devuelve el número de bytes devueltos. Si `data` es `NULL`, a continuación, `pcbData` contiene el número total de bytes de datos disponibles.  
  
 `data`  
 [out] Búfer que va a rellenar con datos de la ubicación especificada.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)