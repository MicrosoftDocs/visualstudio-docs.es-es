---
title: 'Idiastackwalkframe:: ReadMemory | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 03750c990d259bab3a4942021e0b3ee8b1e0fd65
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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