---
title: No se puede eliminar la propiedad
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 63e99bf7b247856815fd3e8de0f4932fed4881dc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535296"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>La propiedad \<property name> no se puede eliminar

No se \<property name> puede eliminar la propiedad porque está establecida como la **propiedad Discriminator** para la herencia entre \<class name> y\<class name>

La propiedad seleccionada está establecida como **propiedad Discriminator** para la herencia entre las clases indicadas en el mensaje de error. Las propiedades no se pueden eliminar si participan en la configuración de la herencia entre clases de datos.

Establezca la **propiedad Discriminator** en otra propiedad de la clase de datos para que se pueda eliminar correctamente la propiedad deseada.

## <a name="to-correct-this-error"></a>Para corregir este error

1. En **Object Relational Designer**, seleccione la línea de herencia que conecta las clases de datos indicadas en el mensaje de error.

2. Establezca la **propiedad Discriminator** en otra propiedad.

3. Intente de nuevo eliminar la propiedad.

## <a name="see-also"></a>Vea también

- [Herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)