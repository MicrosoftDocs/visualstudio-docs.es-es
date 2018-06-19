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
ms.openlocfilehash: 98f95c489758b808ae7a210f7d83332f84571d1f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924144"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>La propiedad &lt;nombre de la propiedad&gt; no se puede eliminar porque participa en la asociación &lt;nombre de asociación&gt;

La propiedad seleccionada está establecida como la **propiedad de asociación** para la asociación entre las clases indicadas en el mensaje de error. Las propiedades no se pueden eliminar si participan en una asociación entre clases de datos.

Establecer el **propiedad de asociación** en otra propiedad de la clase de datos para permitir la eliminación correcta de la propiedad deseada.

## <a name="to-correct-this-error"></a>Para corregir este error

1. En Object Relational Designer, seleccione la línea de asociación que conecta las clases de datos indicadas en el mensaje de error.

2. Haga doble clic en la línea para abrir el **Editor de asociaciones** cuadro de diálogo.

3. Quite la propiedad de la **propiedades de la asociación**.

4. Intente de nuevo eliminar la propiedad.

## <a name="see-also"></a>Vea también

- [Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL de las herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)