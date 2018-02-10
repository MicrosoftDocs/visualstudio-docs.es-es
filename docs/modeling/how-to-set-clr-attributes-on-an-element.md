---
title: "Cómo: establecer los atributos CLR en un elemento | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1eedf41931c7f9476691e507ab0afcd9e2a4c4ee
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Cómo: Establecer atributos de CLR en un elemento
Atributos personalizados son atributos especiales que se pueden agregar a los diagramas, formas, conectores y elementos de dominio. Puede agregar cualquier atributo que hereda de la `System.Attribute` clase.  
  
### <a name="to-add-a-custom-attribute"></a>Para agregar un atributo personalizado  
  
1.  En el **DSL explorador**, seleccione el elemento al que desea agregar un atributo personalizado.  
  
2.  En el **propiedades** ventana, junto a la **atributos personalizados** propiedad, haga clic en el botón Examinar (**...** ) icono.  
  
     El **editar atributos** abre el cuadro de diálogo.  
  
3.  En el **nombre** columna, haga clic en  **\<Agregar atributo >** y escriba el nombre del atributo. Presione ENTRAR.  
  
4.  La línea en el nombre del atributo muestra entre paréntesis. En esta línea, escriba un tipo de parámetro para el atributo (por ejemplo, `string`), y, a continuación, presione ENTRAR.  
  
5.  En el **propiedad Name** columna, escriba un nombre adecuado, por ejemplo, `MyString`.  
  
6.  Haga clic en **Aceptar**.  
  
     El **atributos personalizados** propiedad ahora muestra el atributo en el formato siguiente:  
  
     `[`*AttributeName* `(` *ParameterName* `=` *tipo*`)]`  
  
## <a name="see-also"></a>Vea también  
 [Glosario de herramientas de lenguaje específico de dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)