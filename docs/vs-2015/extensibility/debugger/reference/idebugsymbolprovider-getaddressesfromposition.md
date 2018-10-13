---
title: IDebugSymbolProvider::GetAddressesFromPosition | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f729c6805a1d9b65cad2c2248a4873be9dd2a949
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240141"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método asigna una posición de documento en una matriz de direcciones de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetAddressesFromPosition(   
   IDebugDocumentPosition2* pDocPos,  
   BOOL                     fStatmentOnly,  
   IEnumDebugAddresses**    ppEnumBegAddresses,  
   IEnumDebugAddresses**    ppEnumEndAddresses  
);  
```  
  
```csharp  
int GetAddressesFromPosition(   
   IDebugDocumentPosition2  pDocPos,  
   bool                     fStatmentOnly,  
   out IEnumDebugAddresses  ppEnumBegAddresses,  
   out IEnumDebugAddresses  ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pDocPos`  
 [in] La posición del documento.  
  
 `fStatmentOnly`  
 [in] Si es TRUE, limita las direcciones de depuración para una sola instrucción.  
  
 `ppEnumBegAddresses`  
 [out] Devuelve un enumerador para las direcciones iniciales de depuración asociados con esta instrucción o línea.  
  
 `ppEnumEndAddresses`  
 [out] Devuelve un [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) enumerador para las direcciones de depuración final asociado a esta instrucción o línea.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Una posición de documento normalmente indica un intervalo de líneas de código fuente. Este método proporciona la fecha inicial y final de las direcciones de depuración asociadas con estas líneas. Algunos lenguajes permiten que las instrucciones que abarcan varias líneas, o líneas que contiene más de una instrucción. Este método proporciona una marca para limitar las direcciones de depuración para una sola instrucción.  
  
 Es posible que una sola instrucción tener varias direcciones de depuración, como en el caso de plantillas.  
  
## <a name="see-also"></a>Vea también  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)

