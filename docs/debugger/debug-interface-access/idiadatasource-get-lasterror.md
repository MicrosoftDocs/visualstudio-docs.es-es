---
title: 'Idiadatasource:: Get_lasterror | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1a8320a78c807f08d24f6bcc41db9d775850101b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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
 [out] Devuelve una cadena que contiene el nombre de archivo .pdb asociado con el último error de carga.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el último código de error causado por una operación de carga. Devuelve `E_INVALIDARG` si la `pRetVal` parámetro es `NULL`.  
  
## <a name="example"></a>Ejemplo  
  
```C++  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## <a name="see-also"></a>Vea también  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)