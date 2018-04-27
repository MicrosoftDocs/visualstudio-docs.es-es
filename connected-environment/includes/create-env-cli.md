---
ms.topic: include
ms.openlocfilehash: 97f9885780c9f697cfc6a58b78054761fdcd725d
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
---
## <a name="create-a-kubernetes-development-environment-in-azure"></a>Crear un entorno de desarrollo de Kubernetes en Azure
Con Connected Environment, puede crear entornos basados en Kubernetes totalmente administrables con Azure y optimizados para el desarrollo. El comando crea un entorno denominado `mydevenvironment` en `eastus`.
```cmd
vsce env create --name mydevenvironment --location eastus
```

Ubicaciones admitidas: `eastus`, `westeurope`

> [!Note]
> Este comando tarda aproximadamente 6 minutos. Puede proseguir con esta guía sin tener que esperar.
