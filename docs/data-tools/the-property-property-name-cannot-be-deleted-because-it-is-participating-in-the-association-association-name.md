---
title: La propiedad no se puede eliminar porque participa en la asociación
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6ed6b14f64d16d1f18d4b358761169c3d424cee8
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174067"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>La propiedad &lt;nombre de la propiedad&gt; no se puede eliminar porque participa en la asociación &lt;nombre de asociación&gt;

La propiedad seleccionada está establecida como el **propiedad de asociación** para la asociación entre las clases indicadas en el mensaje de error. Las propiedades no se pueden eliminar si participan en una asociación entre clases de datos.

Establecer el **propiedad de asociación** en otra propiedad de la clase de datos para habilitar la eliminación correcta de la propiedad deseada.

## <a name="to-correct-this-error"></a>Para corregir este error

1. Seleccione la línea de asociación en el **Object Relational Designer** que conecta las clases de datos indicadas en el mensaje de error.

2. Haga doble clic en la línea para abrir el **Editor de asociaciones** cuadro de diálogo.

3. Quite la propiedad de la **propiedades de la asociación**.

4. Intente de nuevo eliminar la propiedad.

## <a name="see-also"></a>Vea también

- [Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)