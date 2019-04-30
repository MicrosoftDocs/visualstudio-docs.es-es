---
title: 'Error: El firewall en el equipo Local | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.firewall.localmachine
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 23290ebb12c2cb3e6bb12554aa9fbb89c4fb82fa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62535559"
---
# <a name="error-firewall-on-local-machine"></a>Error: Firewall en la máquina local
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El firewall de conexión a Internet en el equipo local, el equipo donde ejecuta Visual Studio, no está configurado para permitir la depuración remota. Para una depuración remota administrada o nativa con el transporte predeterminado, el puerto TCP 135 debe estar abierto para el tráfico DCOM. Compartir impresoras y archivos debe estar abierto y devenv.exe se debe agregar a la lista de excepciones. Puede que también resulte necesario abrir algunos puertos IPSEC.  
  
 Para obtener más información, consulte [establecer las herramientas remotas en el dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).
