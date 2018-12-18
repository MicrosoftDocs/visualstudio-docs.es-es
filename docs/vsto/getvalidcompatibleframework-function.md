---
title: GetValidCompatibleFramework (función)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8cc16544df224e09724cae8a1f09f72039cb61e5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894500"
---
# <a name="getvalidcompatibleframework-function"></a>GetValidCompatibleFramework (función)
  Esta API admite la infraestructura de Office y no está diseñada para utilizarse directamente desde el código.  

## <a name="syntax"></a>Sintaxis  

```csharp 
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  

### <a name="parameters"></a>Parámetros  

|Parámetro|Descripción|  
|---------------|-----------------|  
|*lpwszCompatibleFrameworksXML*|No use.|  
|*pbstrValidFrameworkTag*|No use.|  

## <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, devuelve **S_OK**. Si se produce un error en la función, devuelve un código de error.  

