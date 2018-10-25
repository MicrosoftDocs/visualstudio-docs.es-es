---
title: IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: afa0839d5f820a634c84dc1bec4b0fedf6089739
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885595"
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dado un valor de la etiqueta correspondiente, este método devuelve una enumeración de los símbolos que se encuentran en una función de código auxiliar del Acelerador primario especificado en una dirección virtual relativa especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   DWORD                 rva,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `parent`  
 [in] Un `IDiaSymbol` que corresponde a la función de código auxiliar de acelerador se va a buscar.  
  
 `tagValue`  
 [in] El valor de etiqueta de puntero.  
  
 `rva`  
 [in] La dirección virtual relativa.  
  
 `ppResult`  
 [out] Un puntero a un `IDiaEnumSymbols` puntero de interfaz que se inicializa con el resultado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Llame a este método solo en un `IDiaSymbol` interfaz que corresponde a una función de código auxiliar del acelerador.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



