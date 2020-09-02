---
title: IDiaDataSource::get_lastError | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3ad0570436dda6ac9ae52325c891b32a563cf6f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547369"
---
# <a name="idiadatasourceget_lasterror"></a>IDiaDataSource::get_lastError
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera el nombre de archivo para el último error de carga.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pRetVal  
 enuncia Devuelve una cadena que contiene el nombre del archivo. pdb asociado al último error de carga.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el último código de error producido por una operación de carga. Devuelve `E_INVALIDARG` si el `pRetVal` parámetro es `NULL` .  
  
## <a name="example"></a>Ejemplo  
  
```cpp#  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## <a name="see-also"></a>Consulte también  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
