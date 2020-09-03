---
title: IDebugClassField::D oesInterfaceExist | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9f71346c1b69729ae54ef0d33be4149e7000316c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191130"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Determina si una interfaz específica está definida en la clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT DoesInterfaceExist(   
   LPCOLESTR pszInterfaceName  
);  
```  
  
```csharp  
int DoesInterfaceExist(  
   [In] string pszInterfaceName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszInterfaceName`  
 de Cadena que contiene el nombre de interfaz que se va a buscar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, Devuelve S_OK, devuelve S_FALSE si la interfaz no existe; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Observaciones  
 Este método en vigor obtiene una enumeración de todas las interfaces y busca en la lista una interfaz coincidente.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
