---
ms.topic: include
ms.openlocfilehash: dbf7482acb02c6347c9c0d0765ef962cfb43a050
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
---
## <a name="initialize-debug-assets-with-the-vs-code-extension"></a>Inicializar los activos de depuración con la extensión de VS Code
En primer lugar, tenemos que configurar un proyecto de código para que VS Code se comunique con nuestro entorno de desarrollo en Azure. La extensión de VS Code para Connected Environment proporciona un comando de aplicación auxiliar para establecer la configuración de depuración. 

Abra la **paleta de comandos** (a través del menú **Ver | Paleta de comandos**) use la función Autocompletar para escribir y seleccionar este comando: `Connected Environment: Create configuration files for connected development`. 

Esto hace que se agregue una configuración de depuración para Connected Environment en la carpeta `.vscode`.

![](../media/vsce-command-palette.png)

> [!Note]
> **IMPORTANTE**: debido a un error, cierre y vuelva a abrir VS Code antes de continuar.