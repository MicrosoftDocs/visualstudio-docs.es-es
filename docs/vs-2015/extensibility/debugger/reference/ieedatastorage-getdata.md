---
title: IEEDataStorage::GetData | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f3461ec27c00148bf70617856ea900094bd3c78b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574093"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IEEDataStorage::GetData](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ieedatastorage-getdata).  
  
Recupera el número de bytes especificado desde el objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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

