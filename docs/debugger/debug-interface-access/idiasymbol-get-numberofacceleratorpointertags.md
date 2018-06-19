---
title: IDiaSymbol::get_numberOfAcceleratorPointerTags | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66f5e6ceefbff4702d509c18b4a555287a1e9f42
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31466648"
---
# <a name="idiasymbolgetnumberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
Devuelve el número de etiquetas de puntero de acelerador en una función de código auxiliar de C++ AMP.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_numberOfAcceleratorPointerTags(   
   DWORD* count);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `count`  
 [out] Un puntero a un `DWORD` que contiene el número de Acelerador de etiquetas de puntero en una función de código auxiliar de C++ AMP.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Se llama a este método en un `IDiaSymbol` interfaz que corresponde a una función de código auxiliar de acelerador C++ AMP.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)