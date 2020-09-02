---
title: 'IDebugCustomAttribute:: GetName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4463fc4f9d321b26487e885255843a7acd945f76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62569275"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene el nombre del atributo personalizado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetName(   
   BSTR* bstrName  
);  
```  
  
```csharp  
int GetName(  
   out string bstrName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `bstrName`  
 enuncia Devuelve una cadena que contiene el nombre del atributo personalizado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El denominado devuelto por este método corresponde al nombre de la clase utilizada para declarar el atributo. Esto puede no corresponder exactamente al nombre de la propia clase de atributo personalizado como C# permite quitar el sufijo "Attribute" de un nombre de atributo personalizado cuando se usa en una declaración.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
