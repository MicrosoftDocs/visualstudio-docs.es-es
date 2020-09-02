---
title: 'IDebugField:: GetExtendedInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3de21bc984a36db87f8ce1567f4ff7d97212c40e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547564"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método obtiene información extendida sobre un campo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```csharp  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `guidExtendedInfo`  
 de Selecciona la información que se va a devolver. Los valores válidos son:  
  
|Value|Descripción|  
|-----------|-----------------|  
|`guidConstantValue`|Valor como una secuencia de bytes.|  
|`guidConstantType`|El tipo como una signatura de tipo.|  
  
 `prgBuffer`  
 enuncia Devuelve la información extendida.  
  
 `pdwLen`  
 [in, out] Devuelve el tamaño de la información extendida, en bytes.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Actualmente, este método devuelve solo el tipo o el valor de una constante. El llamador debe liberar el búfer devuelto en `prgBuffer` al llamar a la función de com `CoTaskMemFree` (C++) o <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#).  
  
## <a name="see-also"></a>Consulte también  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
