---
title: IDebugPortPicker::DisplayPortPicker | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f21168f249c10a4a7321b78195d86eba8c0a195a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574511"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugPortPicker::DisplayPortPicker](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportpicker-displayportpicker).  
  
Muestra el cuadro de diálogo especificado que permite al usuario seleccionar un puerto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```csharp  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `hwndParentDialog`  
 [in] Identificador para el cuadro de diálogo principal.  
  
 `pbstrPortId`  
 [out] Cadena de identificador de puerto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Un valor devuelto de `S_FALSE` (o un valor devuelto de `S_OK` con el `BSTR` establecido en `NULL`) indica que el usuario hizo clic **cancelar**.  
  
## <a name="see-also"></a>Vea también  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)

