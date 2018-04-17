---
title: Información general (Debug Interface Access SDK) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6494ebe261128ba700cbb92467db78a3d77a3600
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="overview-debug-interface-access-sdk"></a>Información general (Debug Interface Access SDK)
Use el SDK de DIA para tener acceso a la información de depuración de Microsoft. El SDK de DIA proporciona el conjunto de API que elimina la necesidad de volver a escribir el código cada vez que Microsoft cambia el formato de la información de depuración basada en un COM. El SDK de DIA también le permite leer de un conjunto de versiones anteriores de información de depuración, ubicados en archivos .pdb y .dbg generados por [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] versiones 5.0 y versiones posteriores.  
  
 Cada interfaz en el SDK de DIA representa un objeto COM diferente, excepto donde se indique lo contrario. Interfaces adicionales por lo que los objetos adicionales, se crean por medio de consultas, como [idiadatasource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) o [idiasession:: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md), en lugar de mediante una llamada a `QueryInterface` en punteros de interfaz existente.  
  
## <a name="see-also"></a>Vea también  
 [Idiadatasource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)