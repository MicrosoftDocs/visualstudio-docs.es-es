---
title: Publicación de una aplicación Web mediante un script de PowerShell
description: Aprenda a publicar un proyecto web en un sitio web de Azure. Este script crea los recursos necesarios en su suscripción de Azure si no existen.
author: ghogen
manager: jillfra
assetId: 63cfaa2d-f04d-40dc-8677-345385c278d5
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 3d8a6a73f50c331c516f1e433d7d9b1104731380
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2020
ms.locfileid: "89739880"
---
# <a name="publish-webapplicationwebsite-windows-powershell-script"></a>Publicación de WebApplicationWebSite (script de Windows PowerShell)
## <a name="syntax"></a>Sintaxis
Publica un proyecto web en un sitio web de Azure. El script crea los recursos necesarios en su suscripción de Azure si no existen.

```
Publish-WebApplicationWebSite
–Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

## <a name="configuration"></a>Configuración
La ruta de acceso al archivo de configuración JSON que describe los detalles de la implementación.

| Parámetro | Valor predeterminado |
| --- | --- |
| Alias |None |
| ¿Necesario? |true |
| Posición |con nombre |
| Valor predeterminado |None |
| ¿Aceptar la entrada de la canalización? |false |
| ¿Aceptar caracteres comodín? |false |

## <a name="subscriptionname"></a>SubscriptionName
Nombre de la suscripción de Azure en la que desea crear el sitio web.

| Parámetro | Valor predeterminado |
| --- | --- |
| Alias |None |
| ¿Necesario? |false |
| Posición |con nombre |
| Valor predeterminado |None |
| ¿Aceptar la entrada de la canalización? |false |
| ¿Aceptar caracteres comodín? |false |

## <a name="webdeploypackage"></a>WebDeployPackage
La ruta de acceso al paquete de implementación web para publicar en el sitio web. Puede crear este paquete mediante el Asistente de publicación web en Visual Studio. Para obtener más información, consulte [Introducción a Azure Cloud Services y ASP.NET](vs-azure-tools-publish-webapplicationwebsite-windows-powershell-script.md).

| Parámetro | Valor predeterminado |
| --- | --- |
| Alias |None |
| ¿Necesario? |false |
| Posición |con nombre |
| Valor predeterminado |None |
| ¿Aceptar la entrada de la canalización? |false |
| ¿Aceptar caracteres comodín? |false |

## <a name="databaseserverpassword"></a>DatabaseServerPassword
El nombre de usuario y la contraseña de la base de datos SQL en Azure.

| Parámetro | Valor predeterminado |
| --- | --- |
| Alias |None |
| ¿Necesario? |false |
| Posición |con nombre |
| Valor predeterminado |None |
| ¿Aceptar la entrada de la canalización? |false |
| ¿Aceptar caracteres comodín? |false |

## <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Si es true, imprimir mensajes del script a la secuencia de salida.

| Parámetro | Valor predeterminado |
| --- | --- |
| Alias |None |
| ¿Necesario? |false |
| Posición |con nombre |
| Valor predeterminado |false |
| ¿Aceptar la entrada de la canalización? |false |
| ¿Aceptar caracteres comodín? |false |

## <a name="remarks"></a>Observaciones
Para obtener una explicación completa de cómo usar el script para crear entornos de desarrollo y pruebas, consulte [Usar scripts de Windows PowerShell para la publicación en entornos de desarrollo y pruebas](vs-azure-tools-publishing-using-powershell-scripts.md).

El archivo de configuración JSON especifica los detalles de lo que va a implementarse. Incluye la información que especificó cuando creó el proyecto, como el nombre y el nombre de usuario para el sitio web. También incluye la base de datos que se va a aprovisionar, si la hubiera. El código siguiente muestra un archivo de configuración de JSON de ejemplo:

```json
{
    "environmentSettings": {
        "webSite": {
            "name": "WebApplication10554",
            "location": "West US"
        },
        "databases": [
            {
                "connectionStringName": "DefaultConnection",
                "databaseName": "WebApplication10554_db",
                "serverName": "iss00brc88",
                "user": "sqluser2",
                "password": "",
                "edition": "",
                "size": "",
                "collation": "",
                "location": "West US"
            }
        ]
    }
}
```

Puede editar el archivo de configuración de JSON para cambiar lo que se implementa. Una sección webSite es obligatoria pero la sección database es opcional.

## <a name="next-steps"></a>Pasos siguientes
Para obtener más información, consulte [Publish-WebApplicationVM (script de Windows PowerShell)](vs-azure-tools-publish-webapplicationvm.md).
