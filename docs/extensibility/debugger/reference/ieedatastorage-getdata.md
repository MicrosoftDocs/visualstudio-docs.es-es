---
title: IEEDataStorage::GetData | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEDataStorage::GetData
helpviewer_keywords: IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ae4d4e371a79178be741e45662f4a8db8680b5ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Recupera el número especificado de bytes desde el objeto.  
  
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
 [in] El número de bytes que se va a recuperar (el `data` matriz debe contener al menos este número de bytes).  
  
 `sizeGotten`  
 [out] Devuelve el número de bytes que se recuperan en realidad.  
  
 `data`  
 [entrada, salida] Matriz que se rellenará con los datos solicitados.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El uso de este método recomendado consiste en recuperar todos los bytes de datos en una matriz local, porque no hay ninguna manera de saltarse bytes en el proceso de recuperación. En este caso, el parámetro `dataSize` debe ser el valor devuelto por la [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)