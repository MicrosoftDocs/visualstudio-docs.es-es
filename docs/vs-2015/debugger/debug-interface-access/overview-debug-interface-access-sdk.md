---
title: Información general (Debug Interface Access SDK) | Documentos de Microsoft
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 741e4ee8e7b05db9d8b63b296569e268d7144dc7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193614"
---
# <a name="overview-debug-interface-access-sdk"></a>Información general (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use el SDK de DIA para tener acceso a la información de depuración de Microsoft. El SDK de DIA proporciona COM basado en conjunto de API que elimina la necesidad de volver a escribir el código cada vez que Microsoft cambia el formato de la información de depuración. El SDK de DIA también le permite leer de un conjunto seleccionado de versiones anteriores de información de depuración, ubicados en los archivos .pdb y .dbg generados por [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] versión 5.0 y versiones posteriores.  
  
 Cada interfaz en el SDK de DIA representa un objeto COM diferente, excepto donde se indique lo contrario. Interfaces adicionales y, por tanto, los objetos adicionales, se crean por medio de consultas explícitas, como [Idiadatasource](../../debugger/debug-interface-access/idiadatasource-opensession.md) o [Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md), en lugar de mediante una llamada a `QueryInterface` en punteros de interfaz existente.  
  
## <a name="see-also"></a>Vea también  
 [Idiadatasource](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)



