---
title: 'Crear un entorno de desarrollo de .NET Core con contenedores usando Kubernetes en la nube con Visual Studio - Paso 4: Depurar un contenedor en Kubernetes | Microsoft Docs'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desarrollo rápido de Kubernetes con contenedores y microservicios en Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, contenedores
manager: douge
ms.openlocfilehash: 75588fcabbba739c4670da42e24665428ff89130
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Introducción a Connected Environment con .NET Core y Visual Studio

Paso anterior: [Crear un entorno de desarrollo en Azure](get-started-netcore-visualstudio-03.md)

## <a name="debug-a-container-in-kubernetes"></a>Depurar un contenedor en Kubernetes
Cuando tenga el entorno de desarrollo creado correctamente, podrá depurar la aplicación. Establezca un punto de interrupción en el código, por ejemplo, en la línea 20 del archivo `HomeController.cs`, donde está establecida la variable `Message`. Presione **F5** para iniciar la depuración. 

Visual Studio se comunicará con el entorno de desarrollo para compilar e implementar la aplicación y, seguidamente, abre un explorador donde se ejecuta la aplicación web. Puede parecer que el contenedor se ejecuta localmente, pero en realidad se está ejecutando en nuestro entorno de desarrollo en Azure. El uso de la dirección de host local viene motivado porque Connected Environment crea un túnel SSH temporal para el contenedor que se ejecuta en Azure.

Haga clic en el vínculo "**About**" en la parte superior de la página para activar el punto de interrupción. Tendrá acceso completo a la información de depuración tal y como lo haría si el código se ejecutara localmente, como las pilas de llamadas, las variables locales, la información de excepciones, etc.

> [!div class="nextstepaction"]
> [Llamar a otro contenedor](get-started-netcore-visualstudio-05.md)