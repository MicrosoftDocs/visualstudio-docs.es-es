---
title: La cadena de conexión contiene la contraseña
description: La cadena de conexión contiene credenciales con una contraseña en texto no cifrado y no usa seguridad integrada
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 1ce11b59ad7f38de4c71fa13371da16225b5b843
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858415"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>La cadena de conexión contiene credenciales con una contraseña en texto no cifrado y no usa seguridad integrada

¿Desea guardar la cadena de conexión en el archivo DBML y archivos de configuración de la aplicación actuales con esta información confidencial?  Haga clic en **No** para guardar la cadena de conexión sin la información confidencial.

Al trabajar con conexiones de datos que incluyen información confidencial (contraseñas incluidas en la cadena de conexión), se puede optar por guardar la cadena de conexión en el archivo DBML y el archivo de configuración de la aplicación de un proyecto, con o sin la información confidencial.

> [!WARNING]
> Al establecer explícitamente la propiedad **Configuración de la aplicación** de las propiedades de la **Conexión** en **Falso**, se agregará la contraseña al archivo DBML.

## <a name="save-options"></a>Opciones de guardado

- Para guardar la cadena de conexión con la información confidencial, elija **sí**.

   La cadena de conexión se almacena como una configuración de la aplicación. La cadena de conexión incluye la información confidencial en texto sin formato. El archivo DBML no contiene ninguna información confidencial.

- Para guardar la cadena de conexión sin la información confidencial, elija **no**.

   La cadena de conexión se almacena como una configuración de la aplicación, pero no se incluye la contraseña.

## <a name="see-also"></a>Vea también

- [Herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
