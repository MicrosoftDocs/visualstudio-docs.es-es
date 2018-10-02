---
title: Idiadatasource | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e4b0e1a1b105f349daed2fea03a290522f3ccb7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581300"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Idiadatasource](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiadatasource-opensession).  
  
Se abre una sesión para consultar los símbolos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 ppSession  
 [out] Devuelve un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) objeto que representa la sesión abierta.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. En la tabla siguiente se muestra los posibles valores devueltos para este método.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|E_UNEXPECTED|El [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) objeto previamente no se ha inicializado con un origen de símbolos.|  
|E_INVALIDARG|No válido `ppSession` parámetro.|  
|E_OUTOFMEMORY|Memoria insuficiente para abrir la sesión.|  
  
## <a name="remarks"></a>Comentarios  
 Este método abre un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) objeto para un origen de datos.  
  
 `IDiaSession` los objetos implementan las consultas en el origen de datos. Una sesión administra un espacio de direcciones para cada conjunto de símbolos de depuración. Si el archivo .exe o .dll descrito por los símbolos del origen de datos está activo en la dirección de varios intervalos de direcciones (por ejemplo, porque tienen varios procesos de carga), a continuación, se debe usar una sesión para cada intervalo de direcciones.  
  
## <a name="example"></a>Ejemplo  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Información general](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Consultar el archivo .pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)



