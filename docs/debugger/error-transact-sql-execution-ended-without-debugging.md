---
title: 'Error: la ejecución de Transact-SQL finalizó sin depuración | Microsoft Docs'
ms.date: 11/08/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
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
ms.openlocfilehash: 94ced2902becc2e988cde5198eff28911864dcbb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736945"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Error: La ejecución de Transact-SQL finalizó sin depuración

Este error se produce cuando se intenta depurar un procedimiento de Transact-SQL o SQLCLR y el depurador no recibe mensajes de depuración del SQL Server.

Este problema puede deberse a problemas de red o a problemas en el SQL Server, pero la causa más probable es un problema de permisos.

Existen dos cuentas:

- La cuenta de la aplicación es la cuenta de usuario con la que se ejecuta [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- La cuenta de conexión es la identidad que se utiliza para realizar la conexión a SQL Server. Esta cuenta no es necesariamente la misma que la identidad en la que se ejecuta Visual Studio, como si la conexión estuviera usando la autenticación de SQL.

  La depuración de SQL requiere que la cuenta de aplicación debe coincidir con la cuenta de conexión o ser sysadmin.

  Si utiliza un nombre de cuenta de SQL como SA, la cuenta de aplicación debe estar configurada en el SQL Server como administrador del registro de aplicaciones. De forma predeterminada, los administradores del equipo en el que se ejecuta SQL Server son SQL Server sysadmins.

  Para corregir este error, es posible que necesite:

  - Comprobar la configuración de los permisos. Para obtener más información, vea [Cómo: establecer permisos de SQL Server para la depuración](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

  - Asegurarse de que la depuración de SQL esté correctamente configurada.

  - Consultar al administrador de bases de datos o de la red.

## <a name="see-also"></a>Vea también

- [Configurar la depuración de SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Cómo: establecer permisos de SQL Server para la depuración](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)
- [Remote Debugging](../debugger/remote-debugging.md)