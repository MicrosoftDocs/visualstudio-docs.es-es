---
title: 'Crear un entorno de desarrollo de Node.js con contenedores usando Kubernetes en la nube - Paso 6: Nociones del desarrollo en equipo | Microsoft Docs'
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Desarrollo rápido de Kubernetes con contenedores y microservicios en Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, contenedores
manager: ghogen
ms.openlocfilehash: 4db1d71c96da29a06884e562a277a7ca427910d4
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Introducción a Connected Environment con Node.js

Paso anterior: [Llamar a un servicio que se ejecuta en un contenedor aparte](get-started-nodejs-05.md)

[!INCLUDE[](includes/team-development-1.md)]

Veámoslo en acción:
1. Vaya a la ventana de VS Code de `mywebapi` y realice una modificación de código en el controlador GET predeterminado `/`, por ejemplo:

```javascript
app.get('/', function (req, res) {
    res.send('mywebapi now says something new');
});
```

[!INCLUDE[](includes/team-development-2.md)]

> [!div class="nextstepaction"]
> [Siguiente](get-started-nodejs-07.md)

