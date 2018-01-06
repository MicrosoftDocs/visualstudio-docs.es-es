---
title: LocationType | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3f59f33ef51eee099a8dfe5bbc5c822f217f8cd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="locationtype"></a>LocationType
Indica el tipo de información de ubicación contenida en un símbolo.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
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
 La ubicación es relativa del registro.  
  
 `LocIsThisRel`  
 Ubicación es `this`-relativa.  
  
 `LocIsEnregistered`  
 Ubicación está en un registro.  
  
 `LocIsBitField`  
 Se encuentra en un campo de bits.  
  
 `LocIsSlot`  
 La ubicación es una ranura de lenguaje intermedio de Microsoft (MSIL).  
  
 `LocIsIlRel`  
 Ubicación es relativo a MSIL.  
  
 `LocInMetaData`  
 Se encuentra en los metadatos.  
  
 `LocIsConstant`  
 Se encuentra en un valor constante.  
  
 `LocTypeMax`  
 El número de tipos de ubicación de esta enumeración.  
  
## <a name="remarks"></a>Comentarios  
 Las propiedades disponibles para la [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) interfaz dependen de la ubicación del símbolo en el archivo de imagen. Para obtener más información, consulte [ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Los valores de esta enumeración son devueltos por una llamada a la [idiasymbol:: Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Idiasymbol:: Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md)