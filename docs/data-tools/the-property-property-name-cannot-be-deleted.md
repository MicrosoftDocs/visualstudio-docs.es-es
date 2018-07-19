---
title: No se puede eliminar la propiedad
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7e85860de7494ae7d93ad37bd0a115fa786f0a87
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174018"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>La propiedad \<nombre de propiedad > no se puede eliminar

La propiedad \<nombre de propiedad > no se puede eliminar porque está configurado como el **propiedad Discriminator** para la herencia entre \<nombre de clase > y \<nombre de clase >

La propiedad seleccionada está establecida como el **propiedad Discriminator** para la herencia entre las clases indicadas en el mensaje de error. Las propiedades no se pueden eliminar si participan en la configuración de la herencia entre clases de datos.

Establecer el **propiedad Discriminator** en otra propiedad de la clase de datos para habilitar la eliminación correcta de la propiedad deseada.

## <a name="to-correct-this-error"></a>Para corregir este error

1. En el **Object Relational Designer**, seleccione la línea de herencia que conecta las clases de datos indicada en el mensaje de error.

2. Establecer el **discriminador** propiedad en otra propiedad.

3. Intente de nuevo eliminar la propiedad.

## <a name="see-also"></a>Vea también

- [Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)