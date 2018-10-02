---
title: IDebugClassField::GetDefaultIndexer | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b632103d30dddb178ad0d2866f72e6f864d9f197
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582999"
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugClassField::GetDefaultIndexer](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugclassfield-getdefaultindexer).  
  
Obtiene el nombre del indizador predeterminado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetDefaultIndexer(   
   BSTR* pbstrIndexer  
);  
```  
  
```csharp  
int GetDefaultIndexer(  
   out string pbstrIndexer  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrIndexer`  
 [out] Devuelve una cadena que contiene el nombre del indizador predeterminado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK o devuelve S_FALSE si no hay ningún indizador predeterminado. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El indizador predeterminado de una clase es la propiedad que está marcada como el `Default` propiedad para accesos de matriz. Esto es específico [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]. Este es un ejemplo de un indizador predeterminado declarado en [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] y cómo se utiliza.  
  
```vb  
Imports System.Collections;  
  
Public Class Class1  
    Private myList as Hashtable  
  
    Default Public Property Item(ByVal Index As Integer) As Integer  
        Get  
            Return CType(List(Index), Integer)  
        End Get  
        Set(ByVal Value As Integer)  
            List(Index) = Value  
        End Set  
    End Property  
End Class  
  
Function GetItem(Index as Integer) as Integer  
    Dim classList as Class1 = new Class1  
    Dim value as Integer  
  
    ' Access array through default indexer  
    value = classList(2)  
  
    ' Access array through explicit property  
    value = classList.Item(2)  
  
    Return value  
End Function  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)

