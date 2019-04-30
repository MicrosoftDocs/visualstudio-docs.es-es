---
title: 'Error: El firewall en el equipo Local | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.firewall.localmachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87a1813410a092ced335f37b9df4cf6547ca1cc3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851044"
---
# <a name="error-firewall-on-local-machine"></a>Error: Firewall en la máquina local
El firewall de conexión a Internet en el equipo local, el equipo donde ejecuta Visual Studio, no está configurado para permitir la depuración remota. Para una depuración remota administrada o nativa con el transporte predeterminado, el puerto TCP 135 debe estar abierto para el tráfico DCOM. Compartir impresoras y archivos debe estar abierto y devenv.exe se debe agregar a la lista de excepciones. Puede que también resulte necesario abrir algunos puertos IPSEC.

 Para obtener más información, consulte [depuración remota](../debugger/remote-debugging.md).