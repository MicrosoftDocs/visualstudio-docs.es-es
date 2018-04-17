---
title: IDebugSettingsCallback2::EnumEEs | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSettingsCallback2::EnumEEs
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: add7f9b34119fb11938064598b213e26000ecb1a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsettingscallback2enumees"></a>IDebugSettingsCallback2::EnumEEs
Enumera los evaluadores de expresión disponibles dados los identificadores de idioma y el proveedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT EnumEEs(  
   DWORD  celtBuffer,  
   GUID*  rgguidLang,  
   GUID*  rgguidVendor,  
   DWORD* pceltEEs  
);  
```  
  
```csharp  
public int EnumEEs(  
   uint       celtBuffer,  
   ref Guid   rgguidLang,  
   ref Guid   rgguidVendor,  
   ref uint[] pceltEEs  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celtBuffer`  
 [in] Número de elementos de la `pceltEEs` búfer.  
  
 `rgguidLang`  
 [entrada, salida] Identificador único para el lenguaje de programación.  
  
 `rgguidVendor`  
 [entrada, salida] Identificador único para el proveedor.  
  
 `pceltEEs`  
 [entrada, salida] Matriz de evaluadores de expresión.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)