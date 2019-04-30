---
title: Propiedades de Roles de dominio | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b78c409a761a98439cbbbfdf088e052eca745f32
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444470"
---
# <a name="properties-of-domain-roles"></a>Propiedades de los roles de dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las propiedades en la tabla siguiente se asocian con un rol de dominio. Para obtener información acerca de los roles de dominio, consulte [descripción de los modelos, las clases y relaciones](../modeling/understanding-models-classes-and-relationships.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propiedad|Descripción|Default|  
|--------------|-----------------|-------------|  
|Tipo de colección|Si este rol tiene la multiplicidad de 0.. * o 1.. \*, esta propiedad personaliza el tipo genérico que se usa para almacenar la colección de vínculos.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> se usa|  
|Atributos personalizados|Los atributos que especifique aquí se agregará como atributos a la clase de código generado.|\<none>|  
|Es la propiedad admite la exploración|Si `True`, y si la multiplicidad de la relación es de 0.. 1 o 1.. 1, se puede examinar la propiedad de rol por el usuario en el **propiedades** ventana. La propiedad muestra el nombre del elemento en el otro extremo del vínculo de relación.|`True`|  
|Es el generador de propiedad|Si `True`, se genera una propiedad de rol para este rol, que puede utilizar para recorrer la relación en el código del programa. Si se establece false, puede atravesar la relación de una manera menos eficaz mediante el uso de métodos estáticos de la relación de dominio.|`True`|  
|Modificador de acceso del captador de propiedad|El modificador de acceso del captador de la propiedad generada (`public`, `internal`, `private`, `protected`, o `protected internal`).|`public`|  
|Modificador de acceso del establecedor de propiedad|El modificador de acceso del establecedor de la propiedad generada (`public`, `internal`, `private`, `protected`, o `protected internal`).|`public`|  
|Multiplicity|El número de elementos de modelo que puede desempeñar el rol opuesto (`0..1`, `1..1`, `0..*`, o `1..*`). Si la multiplicidad es `0..*` o `1..*`, a continuación, la propiedad generada representa una colección; en caso contrario, la propiedad generada representa un único elemento de modelo.|Depende del tipo de relación y si se trata el rol de origen o destino en la relación.|  
|Name|El nombre del rol de dominio. Esta propiedad no puede contener espacios en blanco.|El nombre de la clase de dominio del encargado de rol para este rol.|  
|Propaga copia|`DoNotPropagateCopy` -El encargado de rol copiado no tendrán ninguna copia de este vínculo.<br /><br /> `PropagateCopyToLinkOnly` -El vínculo copiado apunta a la existente encargado de rol opuesto.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` -El vínculo copiado apunta a una copia del encargado de rol opuesto.|`PropagateCopyToLinkAndOppositeRolePlayer` para los roles de origen de las incrustaciones.<br /><br /> `DoNotPropagateCopy` para otros roles.<br /><br /> Para obtener más información, consulte [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md)|  
|Propaga la eliminación|`True` Para eliminar el elemento que desempeña este rol cuando se elimina el vínculo asociado.|`True` para el destino de un rol de incrustación.<br /><br /> `False` para otros roles.<br /><br /> Para obtener más información, consulte [personalizar el comportamiento de eliminación](../modeling/customizing-deletion-behavior.md).|  
|Nombre de la propiedad|El nombre de la propiedad generada en el código del encargado de rol. Este nombre no puede contener espacios en blanco.|El nombre del rol opuesto si este rol tiene un cero a uno o una multiplicidad de uno a uno; en caso contrario, el nombre de la función opuesta pluralizado.|  
|Encargado de rol|La clase de dominio del elemento que puede desempeñar este rol en la relación. Esta propiedad es de sólo lectura.|La clase de dominio del encargado de rol para este rol.|  
|Notas|Notas informales que están asociadas con el rol de dominio.|\<none>|  
|Categoría|La categoría en la que la propiedad generada aparece en la **propiedades** ventana en el diseñador generado. Si esta propiedad está vacía, la propiedad generada aparece bajo el **Misc** categoría|\<none>|  
|Descripción|La descripción que se usa para documentar código y se usa en la interfaz de usuario del diseñador generado.<br /><br /> La descripción aparece en la información sobre herramientas de Intellisense para la propiedad generada en la clase de encargado de rol.|`Description for` *el nombre completo de la función*|  
|Display Name|El nombre que se muestra en el diseñador generado para el rol de dominio.|El valor ajustado de la propiedad Name.|  
|Help Keyword|La palabra clave opcional que se utiliza para indizar la Ayuda F1 para el rol de dominio.|\<none>|  
|Propiedad nombre para mostrar|El nombre que se muestra en el diseñador generado para la propiedad de rol generado.|El valor ajustado de la propiedad de nombre de propiedad.|  
  
> [!NOTE]
> El valor predeterminado de un nombre para mostrar se basa en el valor de propiedad asociado al insertar espacios delante de cada carácter en mayúsculas que está precedido por un carácter en minúsculas y que no es seguido por otro carácter de letra mayúscula.  
  
## <a name="see-also"></a>Vea también  
 [Propiedades de las relaciones de dominio](../modeling/properties-of-domain-relationships.md)
