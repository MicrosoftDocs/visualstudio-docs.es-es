---
title: Procedimiento Mostrar y ocultar grupos de registros | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.registergroups
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, displaying and hiding register groups
- register groups, displaying and hiding
ms.assetid: 6be5dfb4-4cfe-4daf-b538-60405640857d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be702dcd19506e6da8fb1e291aa5262dbf4399b2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018454"
---
# <a name="how-to-display-and-hide-register-groups-c-c-visual-basic-f"></a>Procedimiento Mostrar y ocultar grupos de registros (C#, C++, Visual Basic, F#)

La ventana **Registros** está disponible únicamente si la depuración del nivel de dirección está habilitada en el cuadro de diálogo **Opciones**, nodo **Depuración**, categoría **General**.

Por motivos de claridad, los registros se organizan en grupos en la ventana **Registros**. Si hace clic con el botón derecho del mouse en la ventana **Registros**, verá un menú contextual con una lista de grupos que puede mostrar u ocultar según su conveniencia, siguiendo este procedimiento:

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, vea [Restablecer la configuración](../ide/environment-settings.md#reset-settings).

## <a name="display-or-hide-register-groups"></a>Mostrar u ocultar grupos de registros

1.  Haga clic con el botón derecho del mouse en la ventana **Registros**.

2.  En el menú contextual, seleccione los grupos de registros que desea mostrar u ocultar.

     Los grupos de registros que no son compatibles con el hardware que se está depurando aparecen deshabilitados en el menú contextual y no se pueden seleccionar.

## <a name="see-also"></a>Vea también

- [Cómo: Uso de la ventana Registros](../debugger/how-to-use-the-registers-window.md)