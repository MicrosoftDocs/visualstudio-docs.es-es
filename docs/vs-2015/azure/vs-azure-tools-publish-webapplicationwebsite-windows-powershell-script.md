---
title: Publish-WebApplicationWebSite (script de Windows PowerShell) | Microsoft Docs
description: Obtenga información sobre cómo publicar un proyecto web en un sitio Web de Azure. Este script crea los recursos necesarios en su suscripción de Azure si no existen.
author: ghogen
manager: douge
assetId: 63cfaa2d-f04d-40dc-8677-345385c278d5
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 175181d5d866e9d7fab51eaf7c3262e47d0ed6a8
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002895"
---
# <a name="publish-webapplicationwebsite-windows-powershell-script"></a>Publish-WebApplicationWebSite (script de Windows PowerShell)
## <a name="syntax"></a>Sintaxis
Publica un proyecto web en un sitio Web de Azure. El script crea los recursos necesarios en su suscripción de Azure si no existen.

    Publish-WebApplicationWebSite
    –Configuration <configuration>
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
| ¿Aceptar la entrada de canalización? |False |
| ¿Aceptar caracteres comodín? |False |

## <a name="subscriptionname"></a>SubscriptionName
El nombre de la suscripción de Azure que desea crear el sitio Web en.

| Parámetro | Valor predeterminado |
| --- | --- |
| Alias |ninguna |
| ¿Obligatorio? |False |
| Posición |con nombre |
| Valor predeterminado |ninguna |
| ¿Aceptar la entrada de canalización? |False |
| ¿Aceptar caracteres comodín? |False |

## <a name="webdeploypackage"></a>WebDeployPackage
La ruta de acceso al paquete de implementación web para publicar en el sitio Web. Puede crear este paquete utilizando el Asistente para publicación Web en Visual Studio. Para obtener más información, consulte [empezar a trabajar con Azure Cloud Services y ASP.NET](http://go.microsoft.com/fwlink/p/?LinkID=623089).

| Parámetro | Valor predeterminado |
| --- | --- |
| Alias |ninguna |
| ¿Obligatorio? |False |
| Posición |con nombre |
| Valor predeterminado |ninguna |
| ¿Aceptar la entrada de canalización? |False |
| ¿Aceptar caracteres comodín? |False |

## <a name="databaseserverpassword"></a>DatabaseServerPassword
El nombre de usuario y la contraseña para la base de datos de SQL Azure.

| Parámetro | Valor predeterminado |
| --- | --- |
| Alias |ninguna |
| ¿Obligatorio? |False |
| Posición |con nombre |
| Valor predeterminado |ninguna |
| ¿Aceptar la entrada de canalización? |False |
| ¿Aceptar caracteres comodín? |False |

## <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Si es true, imprimir mensajes de la secuencia de comandos al flujo de salida.

| Parámetro | Valor predeterminado |
| --- | --- |
| Alias |ninguna |
| ¿Obligatorio? |False |
| Posición |con nombre |
| Valor predeterminado |False |
| ¿Aceptar la entrada de canalización? |False |
| ¿Aceptar caracteres comodín? |False |

## <a name="remarks"></a>Comentarios
Para obtener una explicación completa de cómo usar la secuencia de comandos para crear entornos de desarrollo y pruebas, vea [utilizando Scripts de PowerShell de Windows para publicar en entornos de prueba y desarrollo](vs-azure-tools-publishing-using-powershell-scripts.md).

El archivo de configuración JSON especifica los detalles de lo que va a implementarse. Incluye la información que especificó cuando creó el proyecto, como el nombre y el nombre de usuario para el sitio Web. También incluye la base de datos para aprovisionar, si existe. El código siguiente muestra un archivo de configuración de JSON de ejemplo:

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

Puede editar el archivo de configuración JSON para cambiar lo que se implementa. Una sección webSite es obligatoria, pero la sección de la base de datos es opcional.

## <a name="next-steps"></a>Pasos siguientes
Para obtener más información, consulte [Publish-WebApplicationVM (script de Windows PowerShell)](vs-azure-tools-publish-webapplicationvm.md)

