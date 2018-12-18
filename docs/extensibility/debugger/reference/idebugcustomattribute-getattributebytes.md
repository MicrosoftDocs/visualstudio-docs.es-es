---
title: IDebugCustomAttribute::GetAttributeBytes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5aa1713aba2def384a9dd8290d6ae6afcee6ba64
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913240"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Obtiene la información de atributo como un blob de bytes.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetAttributeBytes(   
   BYTE*  ppBlob,  
   DWORD* pdwLen  
);  
```  
  
```csharp  
int GetAttributeBytes(  
   ref byte[] ppBlob,   
   ref uint   pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppBlob`  
 [in, out] Una matriz que se rellena con los bytes del atributo.  
  
 `pdwLen`  
 [in, out] Especifica el número máximo de bytes que se devuelven en el `ppBlob` de matriz y devuelve el número de bytes escritos realmente en la matriz.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Establecer el `ppBlob` atributos de parámetro en un valor null para devolver el número de bytes disponibles. A continuación, asigne una matriz y pasar esa matriz en para el `ppBlob` parámetro.  
  
 Los bytes de atributo representan los datos sin procesar del atributo personalizado.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)