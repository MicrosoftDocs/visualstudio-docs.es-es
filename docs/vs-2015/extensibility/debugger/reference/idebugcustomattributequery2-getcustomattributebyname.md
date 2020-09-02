---
title: 'IDebugCustomAttributeQuery2:: Getcustomattributebyname (| Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e1af059cf4319c18b8f8bb63e7b50ec3d2822e93
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568439"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene los atributos personalizados bytes dado el nombre del atributo personalizado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 de Cadena que contiene el nombre del atributo personalizado que se va a buscar.  
  
 `ppBlob`  
 [in, out] Matriz que se rellena con los bytes de atributos personalizados.  
  
 `pdwLen`  
 [in, out] Especifica el número máximo de bytes que se van a devolver en la `ppBlob` matriz y devuelve el número de bytes escritos realmente en la matriz.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, Devuelve S_OK o devuelve S_FALSE si el atributo personalizado no existe. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Establezca el `ppBlob` parámetro en un valor null para devolver el número de atributos bytes disponibles. A continuación, asigne una matriz y pase esa matriz en para el `ppBlob` parámetro.  
  
 Los bytes de atributo representan los datos sin procesar del atributo personalizado.  
  
 Si los `ppBlob` `pdwLen` parámetros y se establecen en un valor null, este método se puede utilizar para determinar si el atributo personalizado existe. Sin embargo, una alternativa más sencilla es llamar al método [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) .  
  
## <a name="see-also"></a>Consulte también  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
