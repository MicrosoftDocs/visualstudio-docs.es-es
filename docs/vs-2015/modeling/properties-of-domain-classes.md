---
title: Propiedades de clases de dominio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c668317fba69100701fac95bfa333ed7b3446488
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701965"
---
# <a name="properties-of-domain-classes"></a>Propiedades de las clases de dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Clases de dominio tienen las propiedades en la tabla siguiente. Para obtener información acerca de las clases de dominio, consulte [descripción de los modelos, las clases y relaciones](../modeling/understanding-models-classes-and-relationships.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propiedad|Descripción|Default|  
|--------------|-----------------|-------------|  
|Modificador de acceso|Nivel de acceso de la clase de dominio (`public` o `internal`).|`public`|  
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código fuente que se genera a partir de esta clase de dominio.|\<none>|  
|Genera doble derivada|Si `True`, se generará una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|No tiene Constructor personalizado|Si `True`, se proporcionará un constructor personalizado en el código fuente. Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modificador de herencia|Describe el tipo de herencia de la clase de código fuente que se genera a partir de la clase de dominio (`none`, `abstract` o `sealed`).|`none`|  
|Clase base|Si se deriva esta clase de dominio, el nombre de la clase base.|\<none>|  
|Name|El nombre de esta clase de dominio.|Nombre actual|  
|Espacio de nombres|El espacio de nombres de esta clase de dominio.|Espacio de nombres actual|  
|Notas|Notas informales que están asociadas con esta clase de dominio.|\<none>|  
|Descripción|La descripción que se usa para documentar la interfaz de usuario del diseñador generado.|\<none>|  
|Display Name|El nombre que se mostrará en el diseñador generado para esta clase de dominio.|\<none>|  
|Help Keyword|La palabra clave opcional que se utiliza para indizar la Ayuda F1 para esta clase de dominio.|\<none>|  
  
## <a name="see-also"></a>Vea también  
 [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
