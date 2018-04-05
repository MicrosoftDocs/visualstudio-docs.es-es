---
title: Cómo usar kubectl con un Connected Environment | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 03/12/2018
ms.topic: article
ms.technology: vsce-kubernetes
description: Desarrollo rápido de Kubernetes con contenedores y microservicios en Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, contenedores
manager: ghogen
ms.openlocfilehash: 46c69f80e58a4265aa5e4320e731c3ad241a8116
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="use-kubectl-with-a-connected-environment"></a>Usar `kubectl` con un Connected Environment

Puede tener acceso al clúster de Kubernetes dentro de un Connected Environment y usar herramientas de Kubernetes existentes como, por ejemplo, `kubectl`.

Ejecutar `vsce env create` o `vsce env select` hace que se agregue automáticamente un contexto de configuración de `kubectl`, por lo que kubectl ya debe estar conectado a su clúster de Kubernetes de VSCE. Ejemplos:
- Confirmar el contexto actual: `kubectl config current-context`
- Enumerar todos los contextos disponibles: `kubectl config get-contexts` Un clúster de Kubernetes creado por VSCE tendrá un nombre parecido a "vsce-<guid>".
- Cambiar el contexto: `kubectl config use-context <context-name>`
- Ver el panel de Kubernetes: ejecute `kubectl proxy` y abra el explorador en la dirección que emita este comando (anexe `/ui` a la dirección URL para ir hasta el panel de Kubernetes).
- Enumerar los servicios en ejecución en el espacio de VSCE predeterminado denominado *mainline*: `kubectl get services --namespace=mainline`

