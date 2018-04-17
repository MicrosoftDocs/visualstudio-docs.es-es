---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 518429149ad1d997b860e486f3db4e519ef42cae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Llama a un controlador de eventos para recuperar los resultados de un proceso de carga de símbolos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
   IDebugModule3**    pModule,  
   BSTR*              pbstrDebugMessage,  
   MODULE_INFO_FLAGS* pdwModuleInfoFlags  
);  
```  
  
```csharp  
int GetSymbolSearchInfo(  
   IDebugModule3              pModule,   
   ref string                 pbstrDebugMessage,   
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags  
);  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pModule`  
 [out] Un objeto IDebugModule3 que representa el módulo para el que se cargaron los símbolos.  
  
 `pbstrDebugMessage`  
 [entrada, salida] Devuelve una cadena que contiene los mensajes de error del módulo. Si no hay ningún error, esta cadena solo contendrá el nombre del módulo pero nunca está vacía.  
  
> [!NOTE]
>  [C++] `pbstrDebugMessage` no puede ser `NULL` y que se debe liberar con `SysFreeString`.  
  
 `pdwModuleInfoFlags`  
 [out] Una combinación de indicadores de la [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) enumeración que indica si se han cargado los símbolos.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se recibe un controlador de la [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) evento después de que se realiza un intento para cargar símbolos de depuración para un módulo, el controlador puede llamar a este método para determinar los resultados de la carga.  
  
## <a name="see-also"></a>Vea también  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)