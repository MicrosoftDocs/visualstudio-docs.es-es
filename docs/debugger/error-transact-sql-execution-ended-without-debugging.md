---
title: 'Error: La ejecución de Transact-SQL finalizó sin depuración | Microsoft Docs'
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
ms.openlocfilehash: e86e24f775d8470b54ed7b9c54d27a5d3c1ee8da
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916302"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Error: La ejecución de Transact-SQL finalizó sin depuración

Este error se produce cuando se intenta depurar un procedimiento de Transact-SQL o SQLCLR, y el depurador no recibe mensajes de depuración desde SQL Server.

Esta incidencia se podría deber a problemas de red o de SQL Server, pero la causa más probable es un problema de permisos.

Existen dos cuentas:

- La cuenta de la aplicación es la cuenta de usuario con la que se ejecuta [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- La cuenta de conexión es la identidad que se utiliza para realizar la conexión a SQL Server. Esta cuenta no es necesariamente igual a la identidad con la que se ejecuta Visual Studio si la conexión utiliza la autenticación de SQL.

  La depuración de SQL requiere que la cuenta de la aplicación coincida con la cuenta de conexión o que sea un administrador del sistema.

  Si usa una nombre de cuenta de SQL como sa, la cuenta de la aplicación se debe establecer en SQL Server como sysadmin. De manera predeterminada, los administradores en el equipo donde se ejecuta SQL Server son administradores del sistema de SQL Server.

  Para corregir este error, es posible que necesite:

  - Comprobar la configuración de los permisos. Para obtener más información, vea [Cómo: para establecer permisos de depuración para SQL Server](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

  - Asegurarse de que la depuración de SQL esté correctamente configurada.

  - Consultar al administrador de bases de datos o de la red.

## <a name="see-also"></a>Vea también

- [Configuración de la depuración de SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Cómo: para establecer permisos de depuración para SQL Server](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)
- [Remote Debugging](../debugger/remote-debugging.md)