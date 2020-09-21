---
title: 'Cómo: Establecer atributos de CLR en un elemento'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49551a5e96e3c354b54b6b2ba7cedf1ba2ab4470
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90811206"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Cómo: Establecer atributos de CLR en un elemento
Los atributos personalizados son atributos especiales que se pueden agregar a elementos de dominio, formas, conectores y diagramas. Puede agregar cualquier atributo que herede de la `System.Attribute` clase.

### <a name="to-add-a-custom-attribute"></a>Para agregar un atributo personalizado

1. En el **Explorador de DSL**, seleccione el elemento al que desea agregar un atributo personalizado.

2. En la ventana **propiedades** , junto a la propiedad **atributos personalizados** , haga clic en el icono de examinar (**...**).

     Se abre el cuadro de diálogo **Editar atributos** .

3. En la columna **nombre** , haga clic en **\<add attribute>** y escriba el nombre del atributo. Presione ENTRAR.

4. La línea bajo el nombre del atributo muestra paréntesis. En esta línea, escriba un tipo de parámetro para el atributo (por ejemplo, `string` ) y, a continuación, presione Entrar.

5. En la columna de la **propiedad nombre** , escriba un nombre adecuado, por ejemplo, `MyString` .

6. Haga clic en **Aceptar**.

     La propiedad **atributos personalizados** ahora muestra el atributo con el siguiente formato:

     `[`*AttributeName* `(` *ParameterName* `=` *Tipo* de`)]`

## <a name="see-also"></a>Consulte también

- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))