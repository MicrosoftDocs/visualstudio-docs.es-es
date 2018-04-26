---
title: 'Crear un entorno de desarrollo de Node.js con contenedores usando Kubernetes en la nube - Paso 6: Nociones del desarrollo en equipo | Microsoft Docs'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desarrollo rápido de Kubernetes con contenedores y microservicios en Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, contenedores
manager: douge
ms.openlocfilehash: 6a17dfc3eeebccf1508ea3f69aecb53d067de7af
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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

