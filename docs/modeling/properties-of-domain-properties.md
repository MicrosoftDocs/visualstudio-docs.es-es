---
title: Propiedades de las propiedades de dominio
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain properties
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0342146f604d86dd93ce25ed20e6ab393c581ea9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544175"
---
# <a name="properties-of-domain-properties"></a>Propiedades de las propiedades de dominio
Una *propiedad de dominio* es una característica de un elemento de modelo que puede contener un valor. Por ejemplo, la clase de dominio `Person` podría tener las propiedades `Name` y `BirthDate`. En la definición de DSL, las propiedades de dominio se enumeran en el cuadro de clases de dominio en el diagrama, y en la clase de dominio en DSL Explorer (Explorador de DSL). Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md).

> [!NOTE]
> La palabra "propiedad" tiene dos usos. Una *propiedad de dominio* es una característica que se define en una clase de dominio. Por el contrario, muchos elementos de un DSL tienen *propiedades*, que se muestran en la ventana **propiedades** de la definición de DSL. Por ejemplo, todas las propiedades de dominio tienen un conjunto de características, que se describen en este tema.

 En tiempo de ejecución, cuando un usuario crea instancias de la clase de dominio, los valores de las propiedades de dominio se pueden ver en la ventana Properties (Propiedades), y se pueden mostrar en las formas.

 La mayoría de las propiedades de dominio se implementan como propiedades de CLR normales. Sin embargo, desde el punto de vista de la programación, las propiedades de dominio tienen una funcionalidad más amplia que las propiedades de programa normales:

- Puede definir reglas y eventos que supervisen el estado de una propiedad. Para obtener más información, consulte [responder a los cambios y propagarlos](../modeling/responding-to-and-propagating-changes.md).

- Las transacciones ayudan a evitar estados incoherentes. Para obtener más información, vea [navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md).

  Cuando selecciona una propiedad de dominio en un diagrama o en DSL Explorer (Explorador de DSL), puede ver los siguientes elementos en la ventana Properties (Propiedades). Para obtener más información sobre cómo usar estos elementos, vea [personalizar y extender un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Propiedad|Descripción|Valor predeterminado|
|-|-|-|
|**Descripción**|La descripción que se usa para documentar la interfaz de usuario del diseñador generado.|\<none>|
|**Nombre para mostrar**|Nombre que se mostrará en el diseñador generado para esta propiedad de dominio. Puede contener espacios y puntuación, por ejemplo "Título de la canción".|\<none>|
|**Element Name Provider**|Solo es aplicable si ha establecido `Is Element Name` en `true`. Puede escribir código que proporcione un nombre para un nuevo elemento de una clase de dominio e invalidar el comportamiento predeterminado.<br /><br /> En un archivo de código del proyecto de DSL, cree una clase que derive de <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider>.<br /><br /> En DSL Explorer (Explorador de DSL), haga clic con el botón secundario en la raíz del DSL y haga clic en Add External Type (Agregar tipo externo). Escriba el nombre de la clase.<br /><br /> Seleccione de nuevo esta propiedad de dominio y seleccione el nombre de la clase en la lista desplegable.|\<none>|
|**Getter Access Modifier**|Nivel de acceso de la clase de dominio (`public` o `internal`). Controla el ámbito en el cual el código de programa puede acceder a la propiedad.|`public`|
|**Help Keyword**|Palabra clave opcional que se usa para indizar la ayuda de F1 para esta propiedad de dominio.|\<none>|
|**Is Browsable**|Si es `True`, la propiedad de dominio se muestra al usuario en la ventana de propiedades cuando se abren los modelos de este DSL.<br /><br /> Si es `False`, la propiedad de dominio se oculta en la interfaz de usuario.<br /><br /> Si desea que la propiedad de dominio sea visible pero de solo lectura, establezca **es la interfaz de usuario de solo lectura**.|`True`|
|**Is Element Name**|Si es `True`, esta propiedad de dominio se mostrará con el nombre de su elemento modelo en DSL Explorer (Explorador de DSL).<br /><br /> Los nuevos elementos de modelo recibirán un valor predeterminado único para esta propiedad. Si desea controlar cómo se generan estos valores, establezca **el proveedor de nombres de elemento**.|`False`|
|**Is UI Read Only**|Si es `True`, el valor de la propiedad de dominio no se puede cambiar mediante la interfaz de usuario. Los programas sí pueden establecerlo y será visible en la ventana Properties (Propiedades).<br /><br /> Si desea ocultar la propiedad de dominio del usuario, establezca **es explorable**. Si desea controlar el acceso mediante programas, establezca el **modificador de acceso Setter**.|`False`|
|**Variante**|Tipo de propiedad de dominio (`Normal`, `Calculated` o `CustomStorage`). Para obtener más información, consulte [propiedades de almacenamiento calculado y personalizado](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|
|**Name**|Nombre de esta propiedad de dominio. Debe ser un identificador válido, por ejemplo **SongTitle**.|\<none>|
|**Notas**|Notas informales que están asociadas con esta propiedad de dominio.|\<none>|
|**Setter Access Modifier**|Modificador de acceso del establecedor. Controla el ámbito en el cual el código de programa puede establecer la propiedad.|`public`|
|**Tipo**|El tipo de propiedad. Para agregar a la lista de tipos disponibles, haga clic con el botón secundario en la raíz del DSL en el explorador de DSL y haga clic en **Agregar tipo externo**.|`String`|

## <a name="see-also"></a>Consulte también

- [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)