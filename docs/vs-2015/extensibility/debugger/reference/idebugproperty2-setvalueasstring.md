---
title: 'IDebugProperty2:: SetValueAsString | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d50057570b5b067447321f975d4d33da8aa3de43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193443"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Establece el valor de una propiedad a partir de una cadena determinada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   UINT      nRadix,  
   DWORD     dwTimeout  
);  
```  
  
```csharp  
int SetValueAsString (   
   string pszValue,  
   uint   nRadix,  
   uint   dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszValue`  
 de Cadena que contiene el valor que se va a establecer.  
  
 `nRadix`  
 de Base que se va a utilizar para interpretar cualquier información numérica. Puede ser 0 para intentar determinar la base automáticamente.  
  
 `dwTimeout`  
 de Especifica el tiempo máximo, en milisegundos, que se va a esperar antes de que se devuelva desde este método. Use `INFINITE` para esperar indefinidamente.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve el código de error. En la tabla siguiente se muestran otros valores posibles.  
  
|Value|Descripción|  
|-----------|-----------------|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|La cadena no se pudo convertir en un valor de propiedad o no se pudo establecer el valor de la propiedad.|  
|`E_SETVALUE_VALUE_IS_READONLY`|La propiedad es de solo lectura.|  
  
## <a name="see-also"></a>Consulte también  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
