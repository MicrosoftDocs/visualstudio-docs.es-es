---
title: Extracción de miembros
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para extraer miembros hasta un tipo base.
ms.custom: SEO-VS-2020
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 159608644cb641aa2c84e4d55e92156215069030
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616881"
---
# <a name="pull-members-up"></a>Extracción de miembros

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** permite extraer miembros al tipo base.

**Cuándo:** si se ha implementado una interfaz y se quiere mover un miembro al tipo base.

**Por qué:** extraer miembros permite que otras implementaciones de la interfaz también hereden esos miembros.

## <a name="how-to"></a>Instrucciones

1. Coloque el cursor en cualquier miembro de una interfaz implementada.
2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

   ![Extraer miembros](media/pull-members-up.png)

2. Seleccione **Pull Members up to base type** (Extraer miembros al tipo base).

3. En el cuadro de diálogo, seleccione los miembros que le gustaría agregar a la interfaz seleccionada.

   ![Extracción de miembro](media/pull-members-up-dialog.png)

4. Elija **Aceptar**. Los miembros seleccionados se extraen a la interfaz.

   ![Extracción de miembro completada](media/pull-members-up-completed.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
