---
title: IDiaPropertyStorage::ReadMultiple | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77ead9e28f86067c08aa610fc902f2a0847bfb25
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
Lee las propiedades del conjunto actual de la propiedad especificadas.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cpspec`  
 [in] Recuento de propiedades especificadas en el `rgpspec` matriz. Si es cero, el método no devuelve ninguna propiedad pero devolver `S_OK` como un código correcto.  
  
 `rgpspec`  
 [in] Una matriz de propiedades que se leerán. Propiedades pueden especificarse por un identificador de propiedad o por un nombre de cadena opcional. No es necesario especificar propiedades en ningún orden concreto de la matriz. La matriz puede contener propiedades duplicadas, lo que produce valores de propiedad duplicada en la devolución de propiedades simples. Las propiedades de simple no deberían devolver acceso denegado al intentar abrir una segunda vez. La matriz puede contener una combinación de identificadores de propiedad y los identificadores de cadena. Esta matriz debe tener al menos `cpspec` número de valores de propiedad.  
  
 `rgvar`  
 [entrada, salida] Una matriz de `PROPVARIANT` estructuras (en el espacio de nombres de ensamblados Microsoft.VisualStudio.OLE.Interop) que para se debe rellenar con valores para cada propiedad. La matriz debe tener al menos `cpspec` elementos de tamaño. El llamador no es necesario inicializar los valores de la matriz.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se encontraron una o varias de las propiedades. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si una propiedad no se encontró, la entrada correspondiente en el `rgvar` matriz contiene un `VARIANT` con el tipo de `VT_EMPTY`.  
  
## <a name="see-also"></a>Vea también  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)