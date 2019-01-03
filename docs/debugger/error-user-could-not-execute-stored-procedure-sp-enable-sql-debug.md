---
title: 'Error: Usuario podría no ejecutar el procedimiento almacenado sp_enable_sql_debug | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
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
ms.openlocfilehash: 7b121b863237a3b12b5131be348581ea3fd043d2
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348566"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>Error: El usuario no pudo ejecutar el procedimiento almacenado sp_enable_sql_debug

El procedimiento almacenado sp_enable_sql_debug no se pudo ejecutar en el servidor. Esto se puede producir por:

- Un problema de conexión. Necesita tener una conexión estable al servidor.

- Faltan permisos necesarios en el servidor. Para depurar en SQL Server 2005, la cuenta que ejecuta Visual Studio y la cuenta empleada para conectar a SQL Server tienen que ser miembros del rol sysadmin. La cuenta empleada para conectar a SQL Server es la cuenta de usuario de Windows (si se utiliza la Autenticación de Windows) o una cuenta con id. de usuario y contraseña (si se utiliza la Autenticación SQL).

Para obtener más información, vea [Cómo: Establecer permisos de SQL Server para la depuración](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

## <a name="see-also"></a>Vea también

- [Cómo: Establecer permisos de SQL Server para la depuración](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Configurar la depuración de SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))