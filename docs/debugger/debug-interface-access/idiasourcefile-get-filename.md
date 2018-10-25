---
title: Idiasourcefile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_fileName method
ms.assetid: a5cb8927-23c6-469e-8f78-f2787d85dba4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eb77905968cd40bffa400ebf8e68f6a7fd7df4c5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822857"
---
# <a name="idiasourcefilegetfilename"></a>IDiaSourceFile::get_fileName
Recupera el nombre de archivo de origen.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_fileName (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve el nombre de archivo de origen.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)