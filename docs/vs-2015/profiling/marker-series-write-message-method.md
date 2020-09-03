---
title: marker_series::write_message (Método) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::write_message
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::write_message method
ms.assetid: 546121bc-67e0-4a5a-a456-12bd78fd6de2
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f759ea679af818d85dd365f5615ce4fc664df89a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200743"
---
# <a name="marker_serieswrite_message-method"></a>marker_series::write_message (Método)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Escribe un mensaje en el archivo de seguimiento del visualizador de simultaneidad.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void write_message(  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `_Format`  
 Una cadena de formato compuesto que contiene texto combinado con cero o más elementos de formato, que corresponden a objetos de la lista de argumentos.  
  
 `_Importance`  
 Nivel de importancia.  
  
 `_Category`  
 Nivel de Category.Importance.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** cvmarkersobj.h  
  
 **Espacio de nombres**: Concurrency::diagnostic  
  
## <a name="see-also"></a>Consulte también  
 [marker_series (Clase)](../profiling/marker-series-class.md)
