---
title: Idiadatasource | Documentos de Microsoft
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
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 79c3ec1974341ddee0a147830491bf324b1fe0c5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769843"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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



