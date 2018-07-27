---
title: marker_series::write_message (Método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::write_message
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::write_message method
ms.assetid: 546121bc-67e0-4a5a-a456-12bd78fd6de2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70e413267623d4e9bb4b8d4c1f46fd9c6ecf7808
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237957"
---
# <a name="markerserieswritemessage-method"></a>Método marker_series::write_message
Escribe un mensaje en el archivo de seguimiento del visualizador de simultaneidad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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
 **Encabezado:** *cvmarkersobj.h*  
  
 **Espacio de nombres:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Vea también  
 [clase marker_series](../profiling/marker-series-class.md)