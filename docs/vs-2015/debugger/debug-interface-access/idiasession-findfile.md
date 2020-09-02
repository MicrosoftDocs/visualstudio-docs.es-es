---
title: IDiaSession::findFile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e791bc09ba3dd4f1811c650926eadb0f7f0462a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431646"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera los archivos de código fuente mediante la operación de compilación y nombre.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pCompiland`  
 de Objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa la operación de compilación que se va a usar como contexto de la búsqueda. Establezca este parámetro en `NULL` para buscar archivos de código fuente en todos los compilandos.  
  
 `name`  
 de Especifica el nombre del archivo de código fuente que se va a recuperar. Establezca este parámetro en `NULL` para todos los archivos de origen que se van a recuperar.  
  
 `option`  
 de Especifica las opciones de comparación aplicadas a la búsqueda de nombres. Los valores de la enumeración [namesearchoptions (](../../debugger/debug-interface-access/namesearchoptions.md) se pueden usar solos o en combinación.  
  
 `ppResult`  
 enuncia Devuelve un objeto [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) que contiene una lista de los archivos de código fuente recuperados.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
  
```cpp#  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## <a name="see-also"></a>Consulte también  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeración NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)
