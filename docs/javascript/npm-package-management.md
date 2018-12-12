---
title: Administrar paquetes de npm
description: Visual Studio ayuda a administrar paquetes mediante el administrador de paquetes de Node.js (npm)
ms.custom: seodec18
ms.date: 06/06/2018
ms.technology: vs-nodejs
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 297bad186c7f3412e56a5a59f65b82ab9cd35a03
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049659"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Administrar paquetes de npm en Visual Studio

npm permite instalar y administrar paquetes para su uso en las aplicaciones de Node.js. Si no está familiarizado con npm y quiere obtener más información, vaya a la [documentación de npm](https://docs.npmjs.com/).

Visual Studio facilita la interacción con npm y la emisión de comandos de npm a través de la interfaz de usuario o directamente. Puede usar los siguientes métodos:
* [Instalar paquetes desde el Explorador de soluciones](#npmInstallWindow)
* [Administrar paquetes instalados desde el Explorador de soluciones](#solutionExplorer)
* [Usar el comando `.npm` en la ventana interactiva de Node.js](#interactive)

Estas características funcionan conjuntamente y se sincronizan con el sistema del proyecto y el archivo *package.json* del proyecto.

## <a name="npmInstallWindow"></a> Instalar paquetes desde el Explorador de soluciones

La manera más sencilla de instalar paquetes de npm es a través de la ventana de instalación de paquetes de npm. Para acceder a esta ventana, haga clic con el botón derecho en el nodo **npm** del proyecto y seleccione **Instalar nuevos paquetes de NPM**.

![Instalación del nuevo paquete de npm desde el Explorador de soluciones](../javascript/media/solution-explorer-install-package.png)

En esta ventana puede buscar un paquete, especificar opciones e instalar. 

![Búsqueda del paquete de npm](../javascript/media/search-package.png)

* **Tipo de dependencia**: elija entre paquetes **Estándar**, **Desarrollo** y **Opcional**. Estándar especifica que el paquete es una dependencia en tiempo de ejecución, mientras que Desarrollo especifica que el paquete solo es necesario durante el desarrollo.
* **Agregar a package.json**: esta opción está en desuso
* **Versión seleccionada**: seleccione la versión del paquete que quiere instalar.
* **Otros argumentos de NPM**: especifique otros argumentos estándar de npm. Por ejemplo, puede escribir un valor de versión como `@~0.8` para instalar una versión determinada que no esté disponible en la lista de versiones.

Puede ver el progreso de la instalación en la pestaña de npm de la ventana Resultados. Esto puede llevar algo de tiempo.

> [!TIP]
> Puede buscar paquetes con ámbito si antepone el ámbito que le interesa a la consulta de búsqueda, por ejemplo, escriba `@types/mocha` para buscar archivos de definición de TypeScript para Mocha. Además, al instalar las definiciones de tipos de TypeScript, puede especificar la versión de TypeScript de destino si agrega `@ts2.6` al campo del argumento de npm.

## <a name="solutionExplorer"></a>Administrar paquetes instalados desde el Explorador de soluciones

Los paquetes de npm se muestran en el Explorador de soluciones. Las entradas del nodo **npm** imitan las dependencias del archivo *package.json*.

![Búsqueda del paquete de npm](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Estado del paquete
* ![Paquete instalado](../javascript/media/installed-npm.png) - Instalado y en la lista de package.json
* ![Paquete extraño](../javascript/media/extraneous-npm.png): instalado, pero sin aparecer de forma explícita en package.json
* ![Paquete que falta](../javascript/media/missing-npm.png) - No instalado, pero en la lista de package.json

Haga clic con el botón derecho en el nodo de un paquete o en el nodo **npm** para realizar una de las siguientes acciones:
* **Instalar los paquetes que faltan** que aparecen en *package.json*
* **Actualizar paquetes** a la versión más reciente
* **Desinstalar un paquete** y quitarlo de *package.json*

## <a name="interactive"></a>Usar el comando .npm en la ventana interactiva de Node.js

También puede usar el comando `.npm` en la ventana interactiva de Node.js para ejecutar comandos de npm. Para abrir la ventana, haga clic con el botón derecho en el Explorador de soluciones y elija **Abrir la ventana interactiva de Node.js**.

En la ventana, puede usar comandos como los siguientes para instalar un paquete:

`.npm install azure@4.2.3`
 
 > [!Tip]
 > De forma predeterminada, npm se ejecuta en el directorio de inicio del proyecto. Si tiene varios proyectos en la solución, especifique el nombre o la ruta de acceso del proyecto entre paréntesis. 
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Si el proyecto no contiene un archivo package.json, use `.npm init -y` para crear un archivo package.json con entradas predeterminadas. 