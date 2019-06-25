---
title: Publish-WebApplicationVM | Microsoft Docs
description: Obtenga información para implementar una aplicación web en una máquina virtual. Este script crea los recursos necesarios en su suscripción de Azure si no existen.
author: ghogen
manager: jillfra
assetId: de4cec95-f73f-44d9-babd-9f47f2633cdb
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 8b4b7a05de87ab8b70046b51fe9f256f05d3aee5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62572290"
---
# <a name="publish-webapplicationvm-windows-powershell-script"></a>Publish-WebApplicationVM (script de Windows PowerShell)
Implementa una aplicación web en una máquina virtual. El script crea los recursos necesarios en su suscripción de Azure si no existen.

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
| ¿Aceptar la entrada de la canalización? |False |
| ¿Aceptar caracteres comodín? |False |

### <a name="subscriptionname"></a>SubscriptionName
Nombre de la suscripción de Azure en la que desea crear la máquina virtual.

| Alias | ninguna |
| --- | --- |
| ¿Obligatorio? |False |
| Posición |con nombre |
| Valor predeterminado |Utiliza la primera suscripción en el archivo de suscripción |
| ¿Aceptar la entrada de la canalización? |False |
| ¿Aceptar caracteres comodín? |False |

### <a name="webdeploypackage"></a>WebDeployPackage
Ruta de acceso al paquete de implementación web para publicar en la máquina virtual. Puede crear este paquete mediante el Asistente de publicación web en Visual Studio. Vea [Cómo: Creación de un paquete de implementación web en Visual Studio](https://msdn.microsoft.com/library/dd465323.aspx).

| Alias | ninguna |
| --- | --- |
| ¿Obligatorio? |False |
| Posición |con nombre |
| Valor predeterminado |ninguna |
| ¿Aceptar la entrada de la canalización? |False |
| ¿Aceptar caracteres comodín? |False |

### <a name="allowuntrusted"></a>AllowUntrusted
Si es true, permite el uso de certificados que no están firmados por una entidad de certificación raíz de confianza.

| Alias | ninguna |
| --- | --- |
| ¿Obligatorio? |False |
| Posición |con nombre |
| Valor predeterminado |False |
| ¿Aceptar la entrada de la canalización? |False |
| ¿Aceptar caracteres comodín? |False |

### <a name="vmpassword"></a>VMPassword
Credenciales de la cuenta para la máquina virtual. Ejemplo: -VMPassword @{Name = "admin"; Password = "contraseña"}

| Alias | ninguna |
| --- | --- |
| ¿Obligatorio? |False |
| Posición |con nombre |
| Valor predeterminado |ninguna |
| ¿Aceptar la entrada de la canalización? |False |
| ¿Aceptar caracteres comodín? |False |

### <a name="databaseserverpassword"></a>DatabaseServerPassword
Credenciales para la base de datos SQL en Azure. Ejemplo: -DatabaseServerPassword @{Name = "admin"; Password = "contraseña"}

| Alias | ninguna |
| --- | --- |
| ¿Obligatorio? |False |
| Posición |con nombre |
| Valor predeterminado |ninguna |
| ¿Aceptar la entrada de la canalización? |False |
| ¿Aceptar caracteres comodín? |False |

### <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Si es true, imprimir mensajes del script a la secuencia de salida.

| Alias | ninguna |
| --- | --- |
| ¿Obligatorio? |False |
| Posición |con nombre |
| Valor predeterminado |False |
| ¿Aceptar la entrada de la canalización? |False |
| ¿Aceptar caracteres comodín? |False |

## <a name="remarks"></a>Comentarios
Para obtener una explicación completa de cómo usar el script para crear entornos de desarrollo y pruebas, consulte [Usar scripts de Windows PowerShell para la publicación en entornos de desarrollo y pruebas](vs-azure-tools-publishing-using-powershell-scripts.md).

El archivo de configuración JSON especifica los detalles de lo que va a implementarse. Incluye la información que especificó cuando creó el proyecto, como el nombre, el grupo de afinidad, la imagen VHD y el tamaño de la máquina virtual. También incluye los extremos de la máquina virtual, las bases de datos para aprovisionar, si existen, y parámetros de implementación web. El código siguiente muestra un archivo de configuración de JSON de ejemplo:

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

Puede editar el archivo de configuración de JSON para cambiar lo que se aprovisiona. Se necesitan una máquina virtual y un servicio en la nube, pero la sección de la base de datos es opcional.
