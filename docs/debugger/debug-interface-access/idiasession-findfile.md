---
title: 'Idiasession:: FindFile | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef230d1b82992f769011e0cb1d9d4ff11145b82d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Recupera los archivos de origen por operación de compilación y el nombre.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pCompiland`  
 [in] Un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representa la operación de compilación que se usará como un contexto para la búsqueda. Establezca este parámetro en `NULL` para buscar archivos de código fuente en todos los elementos.  
  
 `name`  
 [in] Especifica el nombre del archivo de origen que va a recuperar. Establezca este parámetro en `NULL` para todos los archivos que desea recuperar de origen.  
  
 `option`  
 [in] Especifica las opciones de comparación que se aplica a la búsqueda de nombre. Los valores de la [NameSearchOptions (enumeración)](../../debugger/debug-interface-access/namesearchoptions.md) enumeración puede utilizarse por sí solas o en combinación.  
  
 `ppResult`  
 [out] Devuelve un [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) recupera el objeto que contiene una lista de los archivos de origen.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
  
```C++  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions (enumeración)](../../debugger/debug-interface-access/namesearchoptions.md)