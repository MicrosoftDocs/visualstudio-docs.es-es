---
title: "Propiedades de las propiedades de dominio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lenguaje específico de dominio, propiedades de dominio"
ms.assetid: a9471562-d6f2-46bf-9872-e0d66ba03150
caps.latest.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 24
---
# Propiedades de las propiedades de dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una *propiedad de dominio* es una característica de un elemento de modelo que puede guardar un valor.  Por ejemplo, la clase de dominio `Person` podría tener las propiedades `Name` y `BirthDate`.  En la definición de DSL, las propiedades de dominio se enumeran en el cuadro de clases de dominio en el diagrama, y en la clase de dominio en DSL Explorer \(Explorador de DSL\).  Para obtener más información, vea [Cómo: Definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md).  
  
> [!NOTE]
>  La palabra "propiedad" tiene dos usos.  Una *propiedad de dominio* es una característica que se define en una clase de dominio.  En cambio, muchos elementos de un DSL tienen *propiedades*, que se enumeran en la ventana **Properties** \(Propiedades\) de la definición de DSL.  Por ejemplo, todas las propiedades de dominio tienen un conjunto de características, que se describen en este tema.  
  
 En tiempo de ejecución, cuando un usuario crea instancias de la clase de dominio, los valores de las propiedades de dominio se pueden ver en la ventana Properties \(Propiedades\), y se pueden mostrar en las formas.  
  
 La mayoría de las propiedades de dominio se implementan como propiedades de CLR normales.  Sin embargo, desde el punto de vista de la programación, las propiedades de dominio tienen una funcionalidad más amplia que las propiedades de programa normales:  
  
-   Puede definir reglas y eventos que supervisen el estado de una propiedad.  Para obtener más información, vea [Responder a los cambios y propagarlos](../modeling/responding-to-and-propagating-changes.md).  
  
-   Las transacciones ayudan a evitar estados incoherentes.  Para obtener más información, vea [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
 Cuando selecciona una propiedad de dominio en un diagrama o en DSL Explorer \(Explorador de DSL\), puede ver los siguientes elementos en la ventana Properties \(Propiedades\).  Para obtener más información sobre el uso de estos elementos, vea [Personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propiedad|Descripción|Valor predeterminado|  
|---------------|-----------------|--------------------------|  
|**Description**|La descripción que se usa para documentar la interfaz de usuario del diseñador generado.|\<none\>|  
|**Display Name**|Nombre que se mostrará en el diseñador generado para esta propiedad de dominio.  Puede contener espacios y puntuación, por ejemplo "Título de la canción".|\<none\>|  
|**Element Name Provider**|Solo es aplicable si ha establecido `Is Element Name` en `true`.  Puede escribir código que proporcione un nombre para un nuevo elemento de una clase de dominio e invalidar el comportamiento predeterminado.<br /><br /> En un archivo de código del proyecto de DSL, cree una clase que derive de <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider>.<br /><br /> En DSL Explorer \(Explorador de DSL\), haga clic con el botón secundario en la raíz del DSL y haga clic en Add External Type \(Agregar tipo externo\).  Escriba el nombre de la clase.<br /><br /> Seleccione de nuevo esta propiedad de dominio y seleccione el nombre de la clase en la lista desplegable.|\<none\>|  
|**Getter Access Modifier**|Nivel de acceso de la clase de dominio \(`public` o `internal`\).  Controla el ámbito en el cual el código de programa puede acceder a la propiedad.|`public`|  
|**Help Keyword**|Palabra clave opcional que se usa para indizar la ayuda de F1 para esta propiedad de dominio.|\<none\>|  
|**Is Browsable**|Si es `True`, la propiedad de dominio se muestra al usuario en la ventana de propiedades cuando se abren los modelos de este DSL.<br /><br /> Si es `False`, la propiedad de dominio se oculta en la interfaz de usuario.<br /><br /> Si quiere que la propiedad de dominio sea visible pero de solo lectura, establezca **Is UI Read Only** \(Es IU de solo lectura\).|`True`|  
|**Is Element Name**|Si es `True`, esta propiedad de dominio se mostrará con el nombre de su elemento modelo en DSL Explorer \(Explorador de DSL\).<br /><br /> Los nuevos elementos de modelo recibirán un valor predeterminado único para esta propiedad.  Si quiere controlar cómo se generan estos valores, establezca **Element Name Provider** \(Proveedor de nombres de elemento\).|`False`|  
|**Is UI Read Only**|Si es `True`, el valor de la propiedad de dominio no se puede cambiar mediante la interfaz de usuario.  Los programas sí pueden establecerlo y será visible en la ventana Properties \(Propiedades\).<br /><br /> Si quiere ocultar la propiedad de dominio al usuario, establezca **Is Browsable** \(Se puede examinar\).  Si quiere controlar el acceso de los programas, establezca **Setter Access Modifier** \(Modificador de acceso de establecedor\).|`False`|  
|**Kind**|Tipo de propiedad de dominio \(`Normal`, `Calculated` o `CustomStorage`\).  Para obtener más información, vea [Propiedades de almacenamiento personalizados y calculados](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|  
|**Name**|Nombre de esta propiedad de dominio.  Debe ser un identificador válido, por ejemplo, SongTitle.|\<none\>|  
|**Notes**|Notas informales que están asociadas con esta propiedad de dominio.|\<none\>|  
|**Setter Access Modifier**|Modificador de acceso del establecedor.  Controla el ámbito en el cual el código de programa puede establecer la propiedad.|`public`|  
|**Type**|El tipo de propiedad.  Para agregar a la lista de tipos disponibles, haga clic con el botón secundario en la raíz del DSL en DSL Explorer \(Explorador de DSL\) y haga clic en **Add External Type** \(Agregar tipo externo\).|`String`|  
  
## Vea también  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/es-es/ca5e84cb-a315-465c-be24-76aa3df276aa)