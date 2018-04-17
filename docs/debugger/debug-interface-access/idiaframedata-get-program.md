---
title: 'Idiaframedata:: Get_program | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc770db5f5cf16d9870e05ada01e235206b94078
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
Recupera la cadena de programa que se utiliza para calcular el conjunto antes de llamar a la función actual de registros.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve la cadena de programa.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La cadena de programa es una secuencia de macros que se interpreta para establecer el prólogo. Por ejemplo, un marco de pila típico podría usar la cadena de programa `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`. El formato es notación de Polaco inverso, donde los operadores siguen los operandos. `T0` Representa una variable temporal en la pila. Este ejemplo realiza los pasos siguientes:  
  
1.  Mover el contenido de registro `ebp` a `T0`.  
  
2.  Agregar `4` en el valor de `T0` dará como resultado una dirección, obtener el valor de esa dirección y almacenar el valor de registro `eip`.  
  
3.  Obtener el valor de la dirección almacenada en `T0` y almacenar ese valor en registro `ebp`.  
  
4.  Agregar `8` en el valor de `T0` y almacenar ese valor en registro `esp`.  
  
 Tenga en cuenta que la cadena de programa es específica para la CPU y la convención de llamada configurado para la función representada por el marco de pila actual.  
  
## <a name="see-also"></a>Vea también  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)