---
title: 'IDebugSymbolProvider:: GetAddressesFromPosition | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 27349cfdc438da133c4cea05077649ebb4df376c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547161"
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
 de Posición del documento.  
  
 `fStatmentOnly`  
 de Si es TRUE, limita las direcciones de depuración a una única instrucción.  
  
 `ppEnumBegAddresses`  
 enuncia Devuelve un enumerador para las direcciones de depuración de inicio asociadas a esta instrucción o línea.  
  
 `ppEnumEndAddresses`  
 enuncia Devuelve un enumerador [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) para las direcciones de depuración finales asociadas a esta instrucción o línea.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Una posición de documento suele indicar un intervalo de líneas de código fuente. Este método proporciona las direcciones de depuración inicial y final asociadas a estas líneas. Algunos lenguajes admiten instrucciones que abarcan varias líneas o líneas que contienen más de una instrucción. Este método proporciona una marca para limitar las direcciones de depuración a una única instrucción.  
  
 Es posible que una sola instrucción tenga varias direcciones de depuración, como en el caso de las plantillas.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
