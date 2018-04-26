---
title: 'Crear un entorno de desarrollo de .NET Core con contenedores usando Kubernetes en la nube - Paso 6: Nociones del desarrollo en equipo | Microsoft Docs'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desarrollo rápido de Kubernetes con contenedores y microservicios en Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, contenedores
manager: douge
ms.openlocfilehash: 4da5051b760a12f8fd8837072ada44c8c5a9b239
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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
