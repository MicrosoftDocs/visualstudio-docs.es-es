---
title: 'Error: El usuario no pudo ejecutar el procedimiento almacenado sp_enable_sql_debug | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_accessdenied
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 11957495-c238-4cc5-8937-e4026f5e10e1
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 759386728283d3d39219133e53668afe3259714a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697674"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>Error: El usuario no pudo ejecutar el procedimiento almacenado sp_enable_sql_debug
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El procedimiento almacenado sp_enable_sql_debug no se pudo ejecutar en el servidor. Esto se puede producir por:  
  
- Un problema de conexión. Necesita tener una conexión estable al servidor.  
  
- Faltan permisos necesarios en el servidor. Para depurar en SQL Server 2005, la cuenta que ejecuta Visual Studio y la cuenta empleada para conectar a SQL Server tienen que ser miembros del rol sysadmin. La cuenta empleada para conectar a SQL Server es la cuenta de usuario de Windows (si se utiliza la Autenticación de Windows) o una cuenta con id. de usuario y contraseña (si se utiliza la Autenticación SQL).  
  
  Para obtener más información, vea [Cómo: Establecer permisos de depuración para SQL Server](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
## <a name="see-also"></a>Consulte también  
 [Cómo: establecer permisos de SQL Server para la depuración](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Configuración de la depuración de SQL](https://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3)
