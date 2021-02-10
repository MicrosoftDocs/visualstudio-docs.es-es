---
title: Firewall sin autenticación | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.firewall.noauth
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cdd1b0bc56c0316d3a79cf59f744a7e2b0a2aece
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871616"
---
# <a name="error-firewall-no-authentication"></a>Error: Firewall sin autenticación
El firewall de conexión a Internet en el equipo remoto no está configurado para permitir la depuración remota. Para la depuración remota con `No Authentication`, msvsmon.exe se debe agregar a la lista de excepciones. Puede que también resulte necesario abrir algunos puertos IPSEC.

> [!NOTE]
> El depurador remoto puede configurar automáticamente el Firewall de Windows. Si se utiliza un firewall distinto al Firewall de Windows, por ejemplo software o hardware de terceros, el firewall se debe configurar manualmente para permitir la depuración remota. Para ello, permita el tráfico en los puertos TCP/IP en los que escuche msvsmon.exe. De forma predeterminada, estos son los puertos 4018 y 4019, donde 4018 se utiliza en todos los sistemas operativos y 4019 se usa únicamente en Windows x64 para permitir la depuración de procesos x86.

 Para obtener más información, vea [Depuración remota](../debugger/remote-debugging.md).