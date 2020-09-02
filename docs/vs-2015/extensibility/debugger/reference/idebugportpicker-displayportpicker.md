---
title: IDebugPortPicker::D isplayPortPicker | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3dd9317a73800a3886a5a807e9e28b0c24b2301c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188376"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
 de Identificador del cuadro de diálogo primario.  
  
 `pbstrPortId`  
 enuncia Cadena de identificador de puerto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Un valor devuelto de `S_FALSE` (o un valor devuelto de `S_OK` con el `BSTR` establecido en `NULL` ) indica que el usuario hizo clic en **Cancelar**.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
