---
title: IDiaFrameData::get_program | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d87f5c7fda25a901d44b9f511b9a92eb4471f845
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180013"
---
# <a name="idiaframedataget_program"></a>IDiaFrameData::get_program
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera la cadena de programa que se usa para calcular el conjunto de registros antes de la llamada a la función actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 enuncia Devuelve la cadena de programa.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La cadena de programa es una secuencia de macros que se interpreta para establecer el prólogo. Por ejemplo, un marco de pila típico podría usar la cadena de programa `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="` . El formato es la notación de polaco inversa, donde los operadores siguen los operandos. `T0` representa una variable temporal en la pila. En este ejemplo se realizan los siguientes pasos:  
  
1. Mueva el contenido del registro `ebp` a `T0` .  
  
2. Agregue `4` al valor de `T0` para generar una dirección, obtener el valor de esa dirección y almacenar el valor en el registro `eip` .  
  
3. Obtiene el valor de la dirección almacenada en `T0` y almacena ese valor en el registro `ebp` .  
  
4. Agregue `8` al valor de `T0` y almacene ese valor en el registro `esp` .  
  
   Tenga en cuenta que la cadena de programa es específica de la CPU y de la Convención de llamada configurada para la función representada por el marco de pila actual.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
