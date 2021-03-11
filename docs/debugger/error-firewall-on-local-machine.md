---
description: El firewall de conexión a Internet en el equipo local, el equipo donde ejecuta Visual Studio, no está configurado para permitir la depuración remota.
title: Firewall en el equipo local | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.firewall.localmachine
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
ms.openlocfilehash: bad1dcbfa2dd80ade46bd0e848e3c1f186f3c903
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146970"
---
# <a name="error-firewall-on-local-machine"></a>Error: Firewall en la máquina local
El firewall de conexión a Internet en el equipo local, el equipo donde ejecuta Visual Studio, no está configurado para permitir la depuración remota. Para una depuración remota administrada o nativa con el transporte predeterminado, el puerto TCP 135 debe estar abierto para el tráfico DCOM. Compartir impresoras y archivos debe estar abierto y devenv.exe se debe agregar a la lista de excepciones. Puede que también resulte necesario abrir algunos puertos IPSEC.

 Para obtener más información, vea [Depuración remota](../debugger/remote-debugging.md).
