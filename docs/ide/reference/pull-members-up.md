---
title: Extracción de miembros
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 65ce1b44063fd6152fc300e32e7dd075fa8afcbf
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335898"
---
# <a name="pull-members-up"></a>Extracción de miembros

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** permite extraer miembros al tipo base.

**Cuándo:** si se ha implementado una interfaz y se quiere mover un miembro al tipo base.

**Por qué:** extraer miembros permite que otras implementaciones de la interfaz también hereden esos miembros.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en cualquier miembro de una interfaz implementada.
2. Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.

   ![Extraer miembros](media/pull-members-up.png)

2. Seleccione **Pull Members up to base type** (Extraer miembros al tipo base).

3. En el cuadro de diálogo, seleccione los miembros que le gustaría agregar a la interfaz seleccionada.

   ![Extracción de miembro](media/pull-members-up-dialog.png)

4. Elija **Aceptar**. Los miembros seleccionados se extraen a la interfaz.

   ![Extracción de miembro completada](media/pull-members-up-completed.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
