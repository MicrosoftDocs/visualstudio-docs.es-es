---
title: IDiaStackWalkFrame::readMemory | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97a868973d2a514150b8d728e685523e918f88f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150162"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lee la memoria de la imagen.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 de Uno de los valores de enumeración de la [enumeración memorytypeenum (](../../debugger/debug-interface-access/memorytypeenum.md) que especifica el tipo de memoria a la que se va a obtener acceso.  
  
 `va`  
 de Ubicación de la dirección virtual de la imagen en la que se va a empezar a leer.  
  
 `cbData`  
 de Tamaño del búfer de datos, en bytes.  
  
 `pcbData`  
 enuncia Devuelve el número de bytes devueltos. Si `data` es `NULL` , `pcbData` contiene el número total de bytes de datos disponibles.  
  
 `data`  
 enuncia Búfer que se va a rellenar con los datos de la ubicación especificada.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
