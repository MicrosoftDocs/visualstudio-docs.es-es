---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords: IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bdf3b80a49641a13d9c17673376d70cfdee103cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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