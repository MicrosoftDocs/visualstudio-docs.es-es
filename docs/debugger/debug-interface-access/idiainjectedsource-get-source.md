---
title: Get_source | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2966405dfe3bb7e6134f5ef35e55b30ef6c66c6e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909914"
---
# <a name="idiainjectedsourcegetsource"></a>IDiaInjectedSource::get_source
Recupera los bytes de código de origen.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cbData`  
 [in] El número de bytes que representa el tamaño del búfer de datos.  
  
 `pcbData`  
 [out] Devuelve el número de bytes que representa los bytes devueltos. Si `data` es `NULL`, a continuación, `pcbData` es el número total de bytes de datos disponibles.  
  
 `data[]`  
 [out] Un búfer que se va a rellenar con los bytes de origen.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)