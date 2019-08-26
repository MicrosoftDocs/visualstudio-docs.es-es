---
title: Encapsulado y alineación de cadenas de llamada
description: Aprenda a encapsular y alinear cadenas de llamadas a método.
ms.date: 08/13/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 2a5b6bea4c915e029ca3ae448444decce0d7b041
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/19/2019
ms.locfileid: "69620017"
---
# <a name="wrap-and-align-call-chains"></a>Encapsulado y alineación de cadenas de llamada

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** permite encapsular y alinear cadenas de llamadas a método.

**Cuándo:** tiene una cadena larga que consta de varias llamadas a método en una instrucción.

**Por qué:** es más fácil leer una lista larga cuando sus elementos están encapsulados o con una sangría, según la preferencia del usuario.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en cualquiera de las cadenas de llamada.
2. Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.
3. Seleccione **Encapsular la cadena de llamada** o **Encapsular y alinear la cadena de llamada** para aceptar la refactorización.

   ![Encapsulado y alineación de cadenas de llamada](media/wrap-call-chain.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
