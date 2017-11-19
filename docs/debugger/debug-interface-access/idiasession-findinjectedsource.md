---
title: 'Idiasession:: Findinjectedsource | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::findInjectedSource method
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dbac48aef894272d1edd9c4881c9f916255459b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindinjectedsource"></a>IDiaSession::findInjectedSource
Recupera una lista de orígenes que se ha colocado en el almacén de símbolos por los proveedores de atributo u otros componentes del proceso de compilación.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT findInjectedSource (   
   LPCOLESTR                 srcFile,  
   IDiaEnumInjectedSources** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 srcFile  
 [in] Nombre del archivo de origen para el que se va a buscar.  
  
 ppResult  
 [out] Devuelve un [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) objeto que contiene una lista de todos los orígenes insertados.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)