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
ms.openlocfilehash: 1e4269c620247f256d2cfae2e84b76ff60fcf9ba
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738606"
---
# <a name="overview-debug-interface-access-sdk"></a>Información general (Debug Interface Access SDK)
Use el SDK de DIA para tener acceso a la información de depuración de Microsoft. El SDK de DIA proporciona un conjunto de API basado en COM que elimina la necesidad de volver a escribir el código cada vez que Microsoft cambia el formato de la información de depuración. El SDK de DIA también le permite leer desde un conjunto seleccionado de versiones anteriores de la información de depuración, que se encuentra en los archivos. PDB y. dbg generados por [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] versiones 5,0 y posteriores.

 Cada interfaz del SDK de DIA representa un objeto COM diferente, excepto cuando se indica lo contrario. Las interfaces adicionales y, por lo tanto, los objetos adicionales, se crean mediante consultas explícitas, como [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) o [IDiaSession:: findchildren (](../../debugger/debug-interface-access/idiasession-findchildren.md), en lugar de llamar a `QueryInterface` en punteros de interfaz existentes.

## <a name="see-also"></a>Vea también
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)