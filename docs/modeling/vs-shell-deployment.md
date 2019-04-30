---
title: Implementación de VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70f39dd23851a2ebc0a48afd05da54b0d8deb24a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934300"
---
# <a name="vs-shell-deployment"></a>Implementación de VS Shell

Un shell aislado le permite determinar qué Visual Studio funcionalidad que necesita para interactuar con su lenguaje específico de dominio y cómo debe aparecer esa solución. Para obtener más información acerca del shell aislado de Visual Studio, consulte [personalización del Shell aislado](https://vspartner.com/pages/vsshells).

Para establecer un Shell de Visual Studio como el destino de implementación:

1. En el **DslPackage** proyecto, abra **source.extension.tt**.

2. Bajo `<SupportedProducts>` insertar:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Reemplace *MyIsolatedShell* con el nombre del paquete de shell aislado.