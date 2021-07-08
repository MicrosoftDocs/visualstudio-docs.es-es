---
title: Eliminación de las referencias no utilizadas
description: Obtenga información sobre cómo limpiar las referencias de proyecto y los paquetes NuGet que no tienen uso con el nuevo comando Remove Unused References (Quitar referencias sin usar).
ms.custom: SEO-VS-2021
ms.date: 06/01/2021
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 707769229ad7bc1864a135bade1df918d4b27847
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2021
ms.locfileid: "111352122"
---
# <a name="remove-unused-references"></a>Eliminación de las referencias no utilizadas

Esta refactorización se aplica a lo siguiente:

- C#
- Visual Basic

**Qué:** permite quitar referencias no utilizadas.

**Cuándo:** quiere limpiar las referencias de proyecto y los paquetes NuGet que no tienen ningún uso. 

**Por qué:** la eliminación de referencias de proyecto que no tienen uso puede ayudar a ahorrar espacio y reducir el tiempo de inicio de la aplicación, ya que se tarda tiempo en cargar cada módulo y evita que el compilador cargue metadatos que nunca se usarán.

## <a name="how-to"></a>Instrucciones

1. Haga clic con el botón derecho en un nodo de dependencias o nombre de proyecto en el Explorador de soluciones.

2. Seleccione **Remove Unused References** (Quitar referencias sin usar).

    ![Comando Remove Unused References (Quitar referencias sin usar)](media/remove-unused-references-command.png)

3. Se abrirá el cuadro de diálogo **Remove Unused References** (Quitar referencias sin usar) con las referencias que no tienen ningún uso en el código fuente. Las referencias sin usar se seleccionarán previamente para su eliminación con una opción para conservarlas si se selecciona `Keep` en la lista desplegable Acción.

    ![Cuadro de diálogo para quitar referencias sin usar](media/remove-unused-references-dialog.png)

5. Haga clic en `Apply` para quitar las referencias seleccionadas. 

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)