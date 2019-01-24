---
title: No se puede eliminar la propiedad
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 73e3443c5af145934de15f674213ea5bd01384d1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53951672"
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