---
title: "Cómo: establecer los atributos CLR en un elemento | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.EditAttributesDialog
helpviewer_keywords: Domain-Specific Language, custom attrributes
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 91f1143e593ae63d41e15beb74612f192ec736d1
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
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
 [Glosario de herramientas de lenguaje específico de dominio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)