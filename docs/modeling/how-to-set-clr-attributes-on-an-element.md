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
ms.openlocfilehash: ebda963bf1afa55fa8d7f98774c72a75d242ceef
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85532462"
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

## <a name="see-also"></a>Vea también

- [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)