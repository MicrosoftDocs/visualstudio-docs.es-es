---
title: LocationType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 28bcaa626797313f6ea68a17da33ef9ea192a856
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154204"
---
# <a name="locationtype"></a>LocationType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Indica el tipo de información de ubicación contenida en un símbolo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## <a name="elements"></a>Elementos  
 `LocIsNull`  
 La información de ubicación no está disponible.  
  
 `LocIsStatic`  
 La ubicación es estática.  
  
 `LocIsTLS`  
 La ubicación está en el almacenamiento local del subproceso.  
  
 `LocIsRegRel`  
 La ubicación es relativa al registro.  
  
 `LocIsThisRel`  
 La ubicación es `this` -relativa.  
  
 `LocIsEnregistered`  
 La ubicación está en un registro.  
  
 `LocIsBitField`  
 La ubicación se encuentra en un campo de bits.  
  
 `LocIsSlot`  
 Location es una ranura del lenguaje intermedio de Microsoft (MSIL).  
  
 `LocIsIlRel`  
 La ubicación es relativa a MSIL.  
  
 `LocInMetaData`  
 La ubicación está en los metadatos.  
  
 `LocIsConstant`  
 La ubicación está en un valor constante.  
  
 `LocTypeMax`  
 El número de tipos de ubicación en esta enumeración.  
  
## <a name="remarks"></a>Comentarios  
 Las propiedades disponibles para la interfaz [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) dependen de la ubicación del símbolo en el archivo de imagen. Para obtener más información, vea [ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Los valores de esta enumeración son devueltos por una llamada al método [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst. h  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md)
