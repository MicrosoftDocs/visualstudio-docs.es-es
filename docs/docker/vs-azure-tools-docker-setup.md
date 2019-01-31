---
title: Configuración de un host de Docker con VirtualBox | Microsoft Docs
description: Instrucciones paso a paso para configurar una instancia de Docker predeterminada con la máquina de Docker y VirtualBox
services: azure-container-service
documentationcenter: na
author: mlearned
manager: jillfra
ms.assetid: 0b1335a2-7720-42a8-8260-4e06fc00c9f6
ms.service: multiple
ms.devlang: dotnet
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: multiple
ms.date: 06/08/2016
ms.author: mlearned
ms.openlocfilehash: a3c02d59021f7596c4c754e185782c591b71fd11
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55140972"
---
# <a name="configure-a-docker-host-with-virtualbox"></a>Configuración de un host de Docker con VirtualBox
## <a name="overview"></a>Información general
Este artículo le guiará por el proceso de configuración de una instancia de Docker predeterminada con la máquina de Docker y VirtualBox.
Si utiliza [Docker para Windows](https://www.docker.com/products/docker-desktop), esta configuración no es necesaria.

## <a name="prerequisites"></a>Requisitos previos
Es necesario instalar las siguientes herramientas.

* [Docker Toolbox](https://github.com/docker/toolbox/releases)

## <a name="configuring-the-docker-client-with-windows-powershell"></a>Configuración del cliente de Docker con Windows PowerShell
Para configurar a un cliente de Docker, simplemente abra Windows PowerShell y realice los pasos siguientes:

1. Cree una instancia de host de docker predeterminada.

    ```PowerShell
    docker-machine create --driver virtualbox default
    ```
2. Compruebe que la instancia predeterminada está configurada y en ejecución. (Verá que se ejecuta una instancia denominada 'predeterminada'.

    ```PowerShell
    docker-machine ls
    ```

    ![salida de docker-machine ls](media/vs-azure-tools-docker-setup/docker-machine-ls.png)
3. Establezca el host actual como predeterminado y configure el shell.

    ```PowerShell
    docker-machine env default | Invoke-Expression
    ```
4. Vea los contenedores de Docker activos. La lista debe estar vacía.

    ```PowerShell
    docker ps
    ```

    ![salida de docker ps](media/vs-azure-tools-docker-setup/docker-ps.png)

> [!NOTE]
> Cada vez que reinicie el equipo de desarrollo, deberá reiniciar el host de Docker local.
> Para ello, emita el siguiente comando en un símbolo del sistema: `docker-machine start default`.
