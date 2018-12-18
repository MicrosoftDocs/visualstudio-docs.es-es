---
title: IEEDataStorage::GetData | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 88ca53843c342547a0c0641bcb76f8e1166723ab
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860597"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Recupera el número de bytes especificado desde el objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetData(  
   ULONG  dataSize,  
   ULONG* sizeGotten,  
   BYTE*  data  
);  
```  
  
```csharp  
int GetData(  
   uint     dataSize,  
   out uint sizeGotten,  
   byte[]   data  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dataSize`  
 [in] El número de bytes para recuperar (el `data` matriz debe contener al menos este número de bytes).  
  
 `sizeGotten`  
 [out] Devuelve el número de bytes que se recuperan realmente.  
  
 `data`  
 [in, out] Matriz que se rellena con los datos solicitados.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El uso de este método recomendado consiste en recuperar todos los bytes de datos en una matriz local, ya que no hay ninguna manera de omitir bytes en el proceso de recuperación. En este caso, el parámetro `dataSize` debe ser el valor devuelto por la [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)