---
title: 'Error: Firewall en el equipo Local | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.firewall.localmachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 160e71e357046b69019323ada5ff9cde006460bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="error-firewall-on-local-machine"></a>Error: Firewall en el equipo local
El firewall de conexión a Internet en el equipo local, el equipo donde ejecuta Visual Studio, no está configurado para permitir la depuración remota. Para una depuración remota administrada o nativa con el transporte predeterminado, el puerto TCP 135 debe estar abierto para el tráfico DCOM. Compartir impresoras y archivos debe estar abierto y devenv.exe se debe agregar a la lista de excepciones. Puede que también resulte necesario abrir algunos puertos IPSEC.  
  
 Para obtener más información, consulte [depuración remota](../debugger/remote-debugging.md).