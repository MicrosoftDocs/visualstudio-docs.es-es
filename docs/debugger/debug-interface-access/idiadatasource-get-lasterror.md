---
title: Get_lasterror | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e197262b84fcf964afb74f85e86ff384daa26c9e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819842"
---
# <a name="idiadatasourcegetlasterror"></a>IDiaDataSource::get_lastError
Recupera el nombre de archivo para el último error de carga.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pRetVal  
 [out] Devuelve una cadena que contiene el nombre del archivo .pdb asociado con el último error de carga.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el último código de error causado por una operación de carga. Devuelve `E_INVALIDARG` si el `pRetVal` parámetro es `NULL`.  
  
## <a name="example"></a>Ejemplo  
  
```C++  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## <a name="see-also"></a>Vea también  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)