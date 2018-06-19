---
title: Cómo usar kubectl con un Connected Environment | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 03/12/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desarrollo rápido de Kubernetes con contenedores y microservicios en Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, contenedores
manager: douge
ms.openlocfilehash: 138dce09e0d53dc47703b9c6f56a7efda4adc255
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31883532"
---
# <a name="use-kubectl-with-a-connected-environment"></a>Usar `kubectl` con un Connected Environment

Puede tener acceso al clúster de Kubernetes dentro de un Connected Environment y usar herramientas de Kubernetes existentes como, por ejemplo, `kubectl`.

Ejecutar `vsce env create` o `vsce env select` hace que se agregue automáticamente un contexto de configuración de `kubectl`, por lo que kubectl ya debe estar conectado a su clúster de Kubernetes de VSCE. Ejemplos:
- Confirmar el contexto actual: `kubectl config current-context`
- Enumerar todos los contextos disponibles: `kubectl config get-contexts` Un clúster de Kubernetes creado por VSCE tendrá un nombre parecido a "vsce-<guid>".
- Cambiar el contexto: `kubectl config use-context <context-name>`
- Ver el panel de Kubernetes: ejecute `kubectl proxy` y abra el explorador en la dirección que emita este comando (anexe `/ui` a la dirección URL para ir hasta el panel de Kubernetes).
- Enumerar los servicios en ejecución en el espacio de VSCE predeterminado denominado *mainline*: `kubectl get services --namespace=mainline`

