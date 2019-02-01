---
title: Información general (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f159dcc58a096033516fdd272819b9eb1ad916d1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922666"
---
# <a name="overview-debug-interface-access-sdk"></a>Información general (Debug Interface Access SDK)
Use el SDK de DIA para tener acceso a la información de depuración de Microsoft. El SDK de DIA proporciona COM basado en conjunto de API que elimina la necesidad de volver a escribir el código cada vez que Microsoft cambia el formato de la información de depuración. El SDK de DIA también le permite leer de un conjunto seleccionado de versiones anteriores de información de depuración, ubicados en los archivos .pdb y .dbg generados por [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] versión 5.0 y versiones posteriores.  
  
 Cada interfaz en el SDK de DIA representa un objeto COM diferente, excepto donde se indique lo contrario. Interfaces adicionales y, por tanto, los objetos adicionales, se crean por medio de consultas explícitas, como [Idiadatasource](../../debugger/debug-interface-access/idiadatasource-opensession.md) o [Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md), en lugar de mediante una llamada a `QueryInterface` en punteros de interfaz existente.  
  
## <a name="see-also"></a>Vea también  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)