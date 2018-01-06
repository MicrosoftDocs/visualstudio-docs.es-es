---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords: IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c462551d5664e58727446fb4c4101446366d6c3b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Obtiene los bytes de atributos personalizados según el nombre del atributo personalizado.  
  
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
 [in] Una cadena que contiene el nombre del atributo personalizado para buscar.  
  
 `ppBlob`  
 [entrada, salida] Una matriz que se rellena con los bytes del atributo personalizado.  
  
 `pdwLen`  
 [entrada, salida] Especifica el número máximo de bytes que se va a devolver en la `ppBlob` de matriz y devuelve el número de bytes escritos realmente en la matriz.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK o devuelva S_FALSE si no existe el atributo personalizado. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Establecer el `ppBlob` atributos de parámetro con un valor null para devolver el número de bytes disponibles. A continuación, asigne una matriz y pasar esa matriz en para el `ppBlob` parámetro.  
  
 Los bytes del atributo representan los datos sin formato del atributo personalizado.  
  
 Si el `ppBlob` y `pdwLen` parámetros se establecen en un valor null, este método puede utilizarse para determinar si el atributo personalizado simplemente existe. Una alternativa más sencilla, sin embargo, es llamar a la [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)