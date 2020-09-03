---
title: IDiaDataSource::openSession | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bec5507d15374e6e88afd4567d4b0fec9ca6cb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198600"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Abre una sesión para consultar los símbolos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 ppSession  
 enuncia Devuelve un objeto [IDiaSession](../../debugger/debug-interface-access/idiasession.md) que representa la sesión abierta.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. En la tabla siguiente se muestran los posibles valores devueltos para este método.  
  
|Value|Descripción|  
|-----------|-----------------|  
|E_UNEXPECTED|El objeto [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) no se ha inicializado previamente con un origen de símbolos.|  
|E_INVALIDARG|El parámetro `ppSession` no es válido.|  
|E_OUTOFMEMORY|Memoria insuficiente para abrir la sesión.|  
  
## <a name="remarks"></a>Comentarios  
 Este método abre un objeto [IDiaSession](../../debugger/debug-interface-access/idiasession.md) para un origen de datos.  
  
 `IDiaSession` los objetos implementan consultas en el origen de datos. Una sesión administra un espacio de direcciones para cada conjunto de símbolos de depuración. Si el archivo. exe o. dll descrito por los símbolos del origen de datos está activo en varios intervalos de direcciones (por ejemplo, debido a que se han cargado varios procesos), se debe usar una sesión para cada intervalo de direcciones.  
  
## <a name="example"></a>Ejemplo  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>Consulte también  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Visión](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Consultar el archivo .pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
