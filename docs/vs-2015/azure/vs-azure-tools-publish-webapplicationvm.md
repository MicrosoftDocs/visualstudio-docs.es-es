---
title: Publish-WebApplicationVM | Microsoft Docs
description: Obtenga información sobre cómo implementar una aplicación web en una máquina virtual. Este script crea los recursos necesarios en su suscripción de Azure si no existen.
author: ghogen
manager: douge
assetId: de4cec95-f73f-44d9-babd-9f47f2633cdb
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: c2383e6d7b14d801a391a725f0482736fb926cd1
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003005"
---
# <a name="publish-webapplicationvm-windows-powershell-script"></a>Publish-WebApplicationVM (script de Windows PowerShell)
Implementa una aplicación web a una máquina virtual. El script crea los recursos necesarios en su suscripción de Azure si no existen.

```
Publish-WebApplicationVM
–Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-VMPassword @{Name = "name"; Password = "password")
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

### <a name="configuration"></a>Configuración
La ruta de acceso al archivo de configuración JSON que describe los detalles de la implementación.

| Alias | ninguna |
| --- | --- |
| ¿Obligatorio? |true |
| Posición |con nombre |
| Valor predeterminado |ninguna |
| ¿Aceptar la entrada de canalización? |False |
| ¿Aceptar caracteres comodín? |False |

### <a name="subscriptionname"></a>SubscriptionName
El nombre de la suscripción de Azure en el que desea crear la máquina virtual.

| Alias | ninguna |
| --- | --- |
| ¿Obligatorio? |False |
| Posición |con nombre |
| Valor predeterminado |Usa la primera suscripción en el archivo de suscripción |
| ¿Aceptar la entrada de canalización? |False |
| ¿Aceptar caracteres comodín? |False |

### <a name="webdeploypackage"></a>WebDeployPackage
La ruta de acceso al paquete de implementación web para publicar en la máquina virtual. Puede crear este paquete utilizando el Asistente para publicación Web en Visual Studio. Consulte [Cómo: crear un paquete de implementación Web en Visual Studio](https://msdn.microsoft.com/library/dd465323.aspx).

| Alias | ninguna |
| --- | --- |
| ¿Obligatorio? |False |
| Posición |con nombre |
| Valor predeterminado |ninguna |
| ¿Aceptar la entrada de canalización? |False |
| ¿Aceptar caracteres comodín? |False |

### <a name="allowuntrusted"></a>AllowUntrusted
Si es true, permite el uso de certificados que no están firmados por una entidad emisora raíz de confianza.

| Alias | ninguna |
| --- | --- |
| ¿Obligatorio? |False |
| Posición |con nombre |
| Valor predeterminado |False |
| ¿Aceptar la entrada de canalización? |False |
| ¿Aceptar caracteres comodín? |False |

### <a name="vmpassword"></a>VMPassword
Las credenciales para la cuenta de máquina virtual. Ejemplo: - VMPassword @{nombre = "admin"; Contraseña = "contraseña"}

| Alias | ninguna |
| --- | --- |
| ¿Obligatorio? |False |
| Posición |con nombre |
| Valor predeterminado |ninguna |
| ¿Aceptar la entrada de canalización? |False |
| ¿Aceptar caracteres comodín? |False |

### <a name="databaseserverpassword"></a>DatabaseServerPassword
Las credenciales para la base de datos de SQL Azure. Ejemplo: - DatabaseServerPassword @{nombre = "admin"; Contraseña = "contraseña"}

| Alias | ninguna |
| --- | --- |
| ¿Obligatorio? |False |
| Posición |con nombre |
| Valor predeterminado |ninguna |
| ¿Aceptar la entrada de canalización? |False |
| ¿Aceptar caracteres comodín? |False |

### <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Si es true, imprimir mensajes de la secuencia de comandos al flujo de salida.

| Alias | ninguna |
| --- | --- |
| ¿Obligatorio? |False |
| Posición |con nombre |
| Valor predeterminado |False |
| ¿Aceptar la entrada de canalización? |False |
| ¿Aceptar caracteres comodín? |False |

## <a name="remarks"></a>Comentarios
Para obtener una explicación completa de cómo usar la secuencia de comandos para crear entornos de desarrollo y pruebas, vea [utilizando Scripts de PowerShell de Windows para publicar en entornos de prueba y desarrollo](vs-azure-tools-publishing-using-powershell-scripts.md).

El archivo de configuración JSON especifica los detalles de lo que va a implementarse. Incluye la información que especificó cuando creó el proyecto, como el nombre, grupo de afinidad, imagen de VHD y el tamaño de la máquina virtual. También incluye los puntos de conexión en la máquina virtual, las bases de datos para aprovisionar, si procede y parámetros de implementación web. El código siguiente muestra un archivo de configuración de JSON de ejemplo:

```
{
    "environmentSettings": {
        "cloudService": {
            "name": "myvmname",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myvmname",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Windows-Server-2012-R2-201404.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [
                    {
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [
            {
                "connectionStringName": "",
                "databaseName": "",
                "serverName": "",
                "user": "",
                "password": ""
            }
        ],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

Puede editar el archivo de configuración JSON para cambiar lo que se aprovisiona. Se requiere una máquina virtual y un servicio en la nube, pero la sección de la base de datos es opcional.

