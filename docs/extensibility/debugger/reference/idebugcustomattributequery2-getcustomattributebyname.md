---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 706a464fb7ce67e05ca284ee35af8b330f781579
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919140"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Obtiene los bytes de los atributos personalizados según el nombre del atributo personalizado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetCustomAttributeByName(   
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```csharp  
int GetCustomAttributeByName(  
   [In] string        pszCustomAttributeName,   
   [In, Out] byte[]   ppBlob,   
   [In, Out] ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszCustomAttributeName`  
 [in] Una cadena que contiene el nombre del atributo personalizado que se busca.  
  
 `ppBlob`  
 [in, out] Una matriz que se rellena con los bytes del atributo personalizado.  
  
 `pdwLen`  
 [in, out] Especifica el número máximo de bytes que se devuelven en el `ppBlob` de matriz y devuelve el número de bytes escritos realmente en la matriz.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK o devuelve S_FALSE si no existe el atributo personalizado. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Establecer el `ppBlob` atributos de parámetro en un valor null para devolver el número de bytes disponibles. A continuación, asigne una matriz y pasar esa matriz en para el `ppBlob` parámetro.  
  
 Los bytes de atributo representan los datos sin procesar del atributo personalizado.  
  
 Si el `ppBlob` y `pdwLen` parámetros se establecen en un valor null, este método puede usarse para determinar si el atributo personalizado simplemente existe. Sin embargo, es una alternativa más sencilla llamar a la [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)