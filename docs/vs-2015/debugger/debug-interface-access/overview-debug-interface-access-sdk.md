---
title: Información general (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7374b03da42e34e8ac3be8c7cc570769d9cfd1ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179211"
---
# <a name="overview-debug-interface-access-sdk"></a>Información general (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use el SDK de DIA para tener acceso a la información de depuración de Microsoft. El SDK de DIA proporciona un conjunto de API basado en COM que elimina la necesidad de volver a escribir el código cada vez que Microsoft cambia el formato de la información de depuración. El SDK de DIA también le permite leer desde un conjunto seleccionado de versiones anteriores de la información de depuración, que se encuentra en los archivos. PDB y. dbg generados por [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] las versiones 5,0 y posteriores.  
  
 Cada interfaz del SDK de DIA representa un objeto COM diferente, excepto cuando se indica lo contrario. Las interfaces adicionales y, por lo tanto, los objetos adicionales, se crean mediante consultas explícitas, como [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) o [IDiaSession:: findchildren (](../../debugger/debug-interface-access/idiasession-findchildren.md), en lugar de llamar a `QueryInterface` en punteros de interfaz existentes.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
