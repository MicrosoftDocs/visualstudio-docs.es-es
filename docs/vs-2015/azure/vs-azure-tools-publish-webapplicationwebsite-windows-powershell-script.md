---
title: Publish-WebApplicationWebSite (script de Windows PowerShell) | Microsoft Docs
description: Aprenda a publicar un proyecto web en un sitio web de Azure. Este script crea los recursos necesarios en su suscripción de Azure si no existen.
services: visual-studio-online
author: ghogen
manager: douge
assetId: 63cfaa2d-f04d-40dc-8677-345385c278d5
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
origin.date: 11/11/2016
ms.date: 09/10/2018
ms.author: v-junlch
ms.openlocfilehash: 6953d8944bb8619560ade4c7b3924dc9e89d3b11
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830529"
---
# <a name="publish-webapplicationwebsite-windows-powershell-script"></a>Publicación de WebApplicationWebSite (script de Windows PowerShell)
## <a name="syntax"></a>Sintaxis
Publica un proyecto web en un sitio web de Azure. El script crea los recursos necesarios en su suscripción de Azure si no existen.

    Publish-WebApplicationWebSite
    -Configuration <configuration>
    -SubscriptionName <subscriptionName>
    -WebDeployPackage <packageName>
    -DatabaseServerPassword @{Name = "name"; Password = "password"}
    -SendHostMessagesToOutput
    -Verbose


## <a name="configuration"></a>Configuración
La ruta de acceso al archivo de configuración JSON que describe los detalles de la implementación.

| Parámetro | Valor predeterminado |
| --- | --- |
| Alias |ninguna |
| ¿Obligatorio? |true |
| Posición |con nombre |
| Valor predeterminado |ninguna |
| ¿Aceptar la entrada de la canalización? |False |
| ¿Aceptar caracteres comodín? |False |

## <a name="subscriptionname"></a>SubscriptionName
Nombre de la suscripción de Azure en la que desea crear el sitio web.

| Parámetro | Valor predeterminado |
| --- | --- |
| Alias |ninguna |
| ¿Obligatorio? |False |
| Posición |con nombre |
| Valor predeterminado |ninguna |
| ¿Aceptar la entrada de la canalización? |False |
| ¿Aceptar caracteres comodín? |False |

## <a name="webdeploypackage"></a>WebDeployPackage
La ruta de acceso al paquete de implementación web para publicar en el sitio web. Puede crear este paquete mediante el Asistente de publicación web en Visual Studio. Para obtener más información, consulte [Introducción a Azure Cloud Services y ASP.NET](http://go.microsoft.com/fwlink/p/?LinkID=623089).

| Parámetro | Valor predeterminado |
| --- | --- |
| Alias |ninguna |
| ¿Obligatorio? |False |
| Posición |con nombre |
| Valor predeterminado |ninguna |
| ¿Aceptar la entrada de la canalización? |False |
| ¿Aceptar caracteres comodín? |False |

## <a name="databaseserverpassword"></a>DatabaseServerPassword
El nombre de usuario y la contraseña de la base de datos SQL en Azure.

| Parámetro | Valor predeterminado |
| --- | --- |
| Alias |ninguna |
| ¿Obligatorio? |False |
| Posición |con nombre |
| Valor predeterminado |ninguna |
| ¿Aceptar la entrada de la canalización? |False |
| ¿Aceptar caracteres comodín? |False |

## <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Si es true, imprimir mensajes del script a la secuencia de salida.

| Parámetro | Valor predeterminado |
| --- | --- |
| Alias |ninguna |
| ¿Obligatorio? |False |
| Posición |con nombre |
| Valor predeterminado |False |
| ¿Aceptar la entrada de la canalización? |False |
| ¿Aceptar caracteres comodín? |False |

## <a name="remarks"></a>Comentarios
Para obtener una explicación completa de cómo usar el script para crear entornos de desarrollo y pruebas, consulte [Usar scripts de Windows PowerShell para la publicación en entornos de desarrollo y pruebas](vs-azure-tools-publishing-using-powershell-scripts.md).

El archivo de configuración JSON especifica los detalles de lo que va a implementarse. Incluye la información que especificó cuando creó el proyecto, como el nombre y el nombre de usuario para el sitio web. También incluye la base de datos que se va a aprovisionar, si la hubiera. El código siguiente muestra un archivo de configuración de JSON de ejemplo:

    {
        "environmentSettings": {
            "webSite": {
                "name": "WebApplication10554",
                "location": "China North"
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
                    "location": "China North"
                }
            ]
        }
    }

Puede editar el archivo de configuración de JSON para cambiar lo que se implementa. Una sección webSite es obligatoria pero la sección database es opcional.

## <a name="next-steps"></a>Pasos siguientes
Para obtener más información, consulte [Publish-WebApplicationVM (script de Windows PowerShell)](vs-azure-tools-publish-webapplicationvm.md)


<!-- Update_Description: update metedata properties -->