---
title: 'Idiadatasource:: OpenSession | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 39fe9bf3a67d3ad5f26ff7c4ccdaa9772cf1346b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459872"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
Se abre una sesión para consultar los símbolos.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 ppSession  
 [out] Devuelve un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) objeto que representa la sesión abierta.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error. La tabla siguiente muestran los posibles valores devueltos para este método.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|E_UNEXPECTED|El [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) objeto previamente no se ha inicializado con un origen de símbolos.|  
|E_INVALIDARG|No válido `ppSession` parámetro.|  
|E_OUTOFMEMORY|Memoria insuficiente para abrir la sesión.|  
  
## <a name="remarks"></a>Comentarios  
 Este método abre un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) objeto para un origen de datos.  
  
 `IDiaSession` objetos de implementar las consultas en el origen de datos. Una sesión administra un espacio de direcciones para cada conjunto de símbolos de depuración. Si el archivo .exe o .dll descrito por los símbolos de origen de datos está activo en varias direcciones intervalos (por ejemplo, porque tienen varios procesos cargado), a continuación, se debe usar una sesión para cada intervalo de direcciones.  
  
## <a name="example"></a>Ejemplo  
  
```C++  
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