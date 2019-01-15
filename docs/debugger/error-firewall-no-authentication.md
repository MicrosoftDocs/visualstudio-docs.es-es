---
title: 'Error: Firewall sin autenticación | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.firewall.noauth
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a37fc9c1df938c1cb4817b74d2ebb1d239377823
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827239"
---
# <a name="error-firewall-no-authentication"></a>Error: Firewall sin autenticación
El firewall de conexión a Internet en el equipo remoto no está configurado para permitir la depuración remota. Para la depuración remota con `No Authentication`, msvsmon.exe se debe agregar a la lista de excepciones. Puede que también resulte necesario abrir algunos puertos IPSEC.  
  
> [!NOTE]
>  El depurador remoto puede configurar automáticamente el Firewall de Windows. Si se utiliza un firewall distinto al Firewall de Windows, por ejemplo software o hardware de terceros, el firewall se debe configurar manualmente para permitir la depuración remota. Para ello, permita el tráfico en los puertos TCP/IP en los que escuche msvsmon.exe. De forma predeterminada, estos son los puertos 4018 y 4019, donde 4018 se utiliza en todos los sistemas operativos y 4019 se usa únicamente en Windows x64 para permitir la depuración de procesos x86.  
  
 Para obtener más información, consulte [depuración remota](../debugger/remote-debugging.md).