---
title: Implementación de VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99ef0124c06cd6f1a4d24e29b2c02cd0b50a37b0
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115270"
---
# <a name="vs-shell-deployment"></a>Implementación de VS Shell

Un shell aislado le permite determinar qué funcionalidad de Visual Studio necesita para interactuar con el lenguaje específico del dominio y cómo debe aparecer esa solución. Para obtener más información sobre el shell aislado de Visual Studio, vea [personalizar el shell aislado](https://vspartner.com/pages/vsshells).

Para establecer un shell de Visual Studio como destino de implementación:

1. En el proyecto **DslPackage** , Abra **source.Extension.TT**.

2. En `<SupportedProducts>` insertar:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Reemplace *MyIsolatedShell* por el nombre del paquete de Shell aislado.
