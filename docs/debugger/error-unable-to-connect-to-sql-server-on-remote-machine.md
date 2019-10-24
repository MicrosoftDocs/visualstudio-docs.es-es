---
title: 'Error: no se puede conectar con SQL Server en el equipo remoto | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlle_dcom_accessdenied
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ecee2a2dbf7c849549ed6f5e844714cbb88bfda
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736822"
---
# <a name="error-unable-to-connect-to-sql-server-on-remote-machine"></a>Error: No se puede establecer una conexión con SQL Server en el equipo remoto
No se puede conectar con SQL Server en *el nombre*del equipo remoto. Acceso denegado. Compruebe que ha instalado el depurador remoto en él. Si el equipo remoto no está en ningún dominio o si Visual Studio se ejecuta como cuenta local, el equipo remoto debe tener una cuenta con el mismo nombre de usuario y la misma contraseña que los de la cuenta local.

### <a name="to-correct-this-error"></a>Para corregir este error

- Consulte [Depuración remota](../debugger/remote-debugging.md).

## <a name="see-also"></a>Vea también
- [Depuración de SQL](/previous-versions/visualstudio/visual-studio-2010/zefbf0t6(v=vs.100))