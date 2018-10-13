---
title: LocationType | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35e78e3430ebb751d97cc3b46057f61b68c4e03e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248903"
---
# <a name="locationtype"></a>LocationType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Indica el tipo de información de ubicación contenida en un símbolo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum LocationType {   
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
 Información de ubicación no está disponible.  
  
 `LocIsStatic`  
 Ubicación es estática.  
  
 `LocIsTLS`  
 Ubicación está en almacenamiento local de subprocesos.  
  
 `LocIsRegRel`  
 Ubicación es relativa del registro.  
  
 `LocIsThisRel`  
 Ubicación es `this`-relativa.  
  
 `LocIsEnregistered`  
 Ubicación está en un registro.  
  
 `LocIsBitField`  
 Ubicación está en un campo de bits.  
  
 `LocIsSlot`  
 La ubicación es una ranura de lenguaje intermedio de Microsoft (MSIL).  
  
 `LocIsIlRel`  
 Ubicación es relativa a MSIL.  
  
 `LocInMetaData`  
 Ubicación está en los metadatos.  
  
 `LocIsConstant`  
 Ubicación está en un valor constante.  
  
 `LocTypeMax`  
 El número de tipos de ubicación de esta enumeración.  
  
## <a name="remarks"></a>Comentarios  
 Las propiedades disponibles para el [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) interfaz dependen de la ubicación del símbolo en el archivo de imagen. Para obtener más información, consulte [ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Los valores de esta enumeración se devuelven mediante una llamada a la [Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md)



