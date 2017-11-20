---
title: Propiedades de propiedades de dominio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, domain properties
ms.assetid: a9471562-d6f2-46bf-9872-e0d66ba03150
caps.latest.revision: "24"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 58402e1030516e6f587ec428bd98179ff82ec43a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-domain-properties"></a>Propiedades de las propiedades de dominio
A *propiedad domain* es una característica de un elemento de modelo que puede contener un valor. Por ejemplo, la clase de dominio `Person` podría tener las propiedades `Name` y `BirthDate`. En la definición de DSL, las propiedades de dominio se enumeran en el cuadro de clases de dominio en el diagrama, y en la clase de dominio en DSL Explorer (Explorador de DSL). Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md).  
  
> [!NOTE]
>  La palabra "propiedad" tiene dos usos. A *propiedad domain* es una característica que define en una clase de dominio. Por el contrario, tienen muchos elementos de un DSL *propiedades*, que se enumeran en la **propiedades** ventana en la definición DSL. Por ejemplo, todas las propiedades de dominio tienen un conjunto de características, que se describen en este tema.  
  
 En tiempo de ejecución, cuando un usuario crea instancias de la clase de dominio, los valores de las propiedades de dominio se pueden ver en la ventana Properties (Propiedades), y se pueden mostrar en las formas.  
  
 La mayoría de las propiedades de dominio se implementan como propiedades de CLR normales. Sin embargo, desde el punto de vista de la programación, las propiedades de dominio tienen una funcionalidad más amplia que las propiedades de programa normales:  
  
-   Puede definir reglas y eventos que supervisen el estado de una propiedad. Para obtener más información, consulte [responder a y propagar los cambios](../modeling/responding-to-and-propagating-changes.md).  
  
-   Las transacciones ayudan a evitar estados incoherentes. Para obtener más información, consulte [navegar y actualizar un modelo de código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
 Cuando selecciona una propiedad de dominio en un diagrama o en DSL Explorer (Explorador de DSL), puede ver los siguientes elementos en la ventana Properties (Propiedades). Para obtener más información sobre cómo usar estos elementos, vea [personalizar y ampliar un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propiedad|Descripción|Valor predeterminado|  
|--------------|-----------------|-------------------|  
|**Descripción**|La descripción que se usa para documentar la interfaz de usuario del diseñador generado.|\<Ninguno >|  
|**Nombre para mostrar**|Nombre que se mostrará en el diseñador generado para esta propiedad de dominio. Puede contener espacios y puntuación, por ejemplo "Título de la canción".|\<Ninguno >|  
|**Proveedor de nombres de elemento**|Solo es aplicable si ha establecido `Is Element Name` en `true`. Puede escribir código que proporcione un nombre para un nuevo elemento de una clase de dominio e invalidar el comportamiento predeterminado.<br /><br /> En un archivo de código del proyecto de DSL, cree una clase que derive de <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider>.<br /><br /> En DSL Explorer (Explorador de DSL), haga clic con el botón secundario en la raíz del DSL y haga clic en Add External Type (Agregar tipo externo). Escriba el nombre de la clase.<br /><br /> Seleccione de nuevo esta propiedad de dominio y seleccione el nombre de la clase en la lista desplegable.|\<Ninguno >|  
|**Modificador de acceso de captador**|Nivel de acceso de la clase de dominio (`public` o `internal`). Controla el ámbito en el cual el código de programa puede acceder a la propiedad.|`public`|  
|**Palabra clave de ayuda**|Palabra clave opcional que se usa para indizar la ayuda de F1 para esta propiedad de dominio.|\<Ninguno >|  
|**Admite la exploración**|Si es `True`, la propiedad de dominio se muestra al usuario en la ventana de propiedades cuando se abren los modelos de este DSL.<br /><br /> Si es `False`, la propiedad de dominio se oculta en la interfaz de usuario.<br /><br /> Si desea que la propiedad de dominio esté visible pero de solo lectura, establezca **es interfaz de usuario de solo lectura**.|`True`|  
|**Es el nombre del elemento**|Si es `True`, esta propiedad de dominio se mostrará con el nombre de su elemento modelo en DSL Explorer (Explorador de DSL).<br /><br /> Los nuevos elementos de modelo recibirán un valor predeterminado único para esta propiedad. Si desea controlar cómo se generan estos valores, establezca **proveedor de nombres de elemento**.|`False`|  
|**Es la interfaz de usuario de solo lectura**|Si es `True`, el valor de la propiedad de dominio no se puede cambiar mediante la interfaz de usuario. Los programas sí pueden establecerlo y será visible en la ventana Properties (Propiedades).<br /><br /> Si desea ocultar la propiedad de dominio del usuario, establezca **es examinable**. Si desea controlar el acceso mediante programas, establezca **modificador de acceso de establecedor**.|`False`|  
|**Tipo**|Tipo de propiedad de dominio (`Normal`, `Calculated` o `CustomStorage`). Para obtener más información, consulte [calculadas y las propiedades de almacenamiento personalizada](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|  
|**Nombre**|Nombre de esta propiedad de dominio. Debe ser un identificador válido, por ejemplo **título**.|\<Ninguno >|  
|**Notas**|Notas informales que están asociadas con esta propiedad de dominio.|\<Ninguno >|  
|**Modificador de acceso de establecedor**|Modificador de acceso del establecedor. Controla el ámbito en el cual el código de programa puede establecer la propiedad.|`public`|  
|**ype**|El tipo de propiedad. Para agregar a la lista de tipos disponibles, haga clic en la raíz de DSL en el Explorador de DSL y haga clic en **Agregar tipo externo**.|`String`|  
  
## <a name="see-also"></a>Vea también  
 [Glosario de herramientas de lenguaje específico de dominio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)