---
ms.topic: include
ms.openlocfilehash: 94e82185b05900101f91e4b368bb30d2aaceac03
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
---
## <a name="clean-up"></a>Limpieza
Para eliminar por completo un Connected Environment en Azure (incluidos todos los servicios que hay ejecutándose en él), use el comando `vsce env rm`. Tenga en cuenta que esta acción es irreversible.

En el siguiente ejemplo se enumeran los Connected Environments existentes en la suscripción activa de Azure y, después, se elimina el entorno "myenv" que está en el grupo de recursos "myenv-rg".

```cmd
vsce env list
vsce env rm --name myenv --resource-group myenv-rg
```

