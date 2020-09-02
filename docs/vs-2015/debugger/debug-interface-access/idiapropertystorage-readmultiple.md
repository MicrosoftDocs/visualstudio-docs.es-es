---
title: IDiaPropertyStorage::ReadMultiple | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 40cd84e00f2e6abea285368a6206c7400abf8877
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538088"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lee las propiedades especificadas del conjunto de propiedades actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cpspec`  
 de Recuento de propiedades especificadas en la `rgpspec` matriz. Si el valor es cero, el método no devuelve ninguna propiedad pero se devuelve `S_OK` como un código de operación correcta.  
  
 `rgpspec`  
 de Matriz de propiedades que se van a leer. Las propiedades se pueden especificar mediante un identificador de propiedad o un nombre de cadena opcional. No es necesario especificar propiedades en ningún orden concreto de la matriz. La matriz puede contener propiedades duplicadas, por lo que los valores de propiedad duplicados se devuelven para propiedades simples. Las propiedades no simples deben devolver acceso denegado al intentar abrirlas una segunda vez. La matriz puede contener una combinación de identificadores de propiedad y de cadena. Esta matriz debe tener al menos un `cpspec` número de valores de propiedad.  
  
 `rgvar`  
 [in, out] Matriz de `PROPVARIANT` estructuras (en el espacio de nombres Microsoft. VisualStudio. OLE. Interop) que se va a rellenar con valores para cada propiedad. La matriz debe tener al menos un `cpspec` elemento de tamaño. El autor de la llamada no necesita inicializar los valores de la matriz.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se encuentra una o varias de las propiedades. En caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si no se encuentra una propiedad, la entrada correspondiente en la `rgvar` matriz contiene un `VARIANT` con el tipo de `VT_EMPTY` .  
  
## <a name="see-also"></a>Consulte también  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
