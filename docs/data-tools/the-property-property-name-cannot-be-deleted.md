---
title: No se puede eliminar la propiedad
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4b1e0652d19b10b1d1ede7b1b950d89ca1bf670c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55939650"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>No se puede eliminar la propiedad \<nombre de propiedad>

No se puede eliminar la propiedad \<nombre de propiedad> porque se está usando como **propiedad Discriminator** para la herencia entre las clases \<nombre de clase> y \<nombre de clase>

La propiedad seleccionada está establecida como **propiedad Discriminator** para la herencia entre las clases indicadas en el mensaje de error. Las propiedades no se pueden eliminar si participan en la configuración de la herencia entre clases de datos.

Establezca la **propiedad Discriminator** en otra propiedad de la clase de datos para que se pueda eliminar correctamente la propiedad deseada.

## <a name="to-correct-this-error"></a>Para corregir este error

1. En **Object Relational Designer**, seleccione la línea de herencia que conecta las clases de datos indicadas en el mensaje de error.

2. Establezca la **propiedad Discriminator** en otra propiedad.

3. Intente de nuevo eliminar la propiedad.

## <a name="see-also"></a>Vea también

- [Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)