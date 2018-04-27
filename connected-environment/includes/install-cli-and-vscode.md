---
ms.topic: include
ms.openlocfilehash: 78de57178350d4317896c41a455efbeeb553c58d
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
---
## <a name="install-the-connected-environment-cli"></a>Instalar la CLI de Connected Environment
Connected Environment requiere una configuración mínima del equipo local. La mayor parte de la configuración del entorno de desarrollo se almacena en la nube y se puede compartir con otros usuarios.

### <a name="install-on-mac"></a>Instalar en Mac
Descargue e instale la CLI de Connected Environment:
```cmd
curl -L https://aka.ms/get-vsce-mac | bash
```

### <a name="install-on-windows"></a>Instalar en Windows
1. Descargue y ejecute el [instalador de la CLI de Connected Environment](https://aka.ms/get-vsce-windows). 

### <a name="install-on-linux"></a>Instalar en Linux
Próximamente...

## <a name="get-kubernetes-debugging-for-vs-code"></a>Obtener la depuración de Kubernetes para VS Code
Aunque la CLI de Connected Environment se puede usar como una herramienta independiente, los desarrolladores de .NET Core y Node.js que usen VS Code tienen a su disposición algunas características sofisticadas, como la depuración de Kubernetes.

1. Si no la tiene, instale [VS Code](https://code.visualstudio.com/Download).
1. Descargue la [extensión de VS Connected Environment](https://aka.ms/get-vsce-code).
1. Instale la extensión: 

```cmd
code --install-extension path-to-downloaded-extension/vsce-0.1.1.vsix
```
