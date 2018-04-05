---
title: 'Crear un entorno de desarrollo de .NET Core con contenedores usando Kubernetes en la nube - Paso 6: Nociones del desarrollo en equipo | Microsoft Docs'
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Desarrollo rápido de Kubernetes con contenedores y microservicios en Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, contenedores
manager: ghogen
ms.openlocfilehash: 80e02e6ce1299278ba1abf530f38cb10b9f36c51
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Introducción a Connected Environment con .NET Core

Paso anterior: [Llamar a otro contenedor](get-started-netcore-05.md)

[!INCLUDE[](includes/team-development-1.md)]

Veámoslo en acción:
1. Vaya a la ventana de VS Code de `mywebapi` y realice una modificación de código en el método `string Get(int id)`, por ejemplo:

```csharp
[HttpGet("{id}")]
public string Get(int id)
{
    return "mywebapi now says something new";
}
```

[!INCLUDE[](includes/team-development-2.md)]

> [!div class="nextstepaction"]
> [Siguiente](get-started-netcore-07.md)
