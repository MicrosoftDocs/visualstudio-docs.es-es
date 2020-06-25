---
title: Cómo crear y aplicar un recurso
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.XamlDesigner.CreateResource
- VS.XamlDesigner.EditResource
ms.assetid: 3ff4006d-659d-4073-9a41-06ff85e6cfdf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2301ce14fcd3d2d8a9c5d003a05186513d950cd4
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330118"
---
# <a name="how-to-create-and-apply-a-resource"></a>Cómo crear y aplicar un recurso

Los estilos y las plantillas de elementos del diseñador XAML se almacenan en entidades reutilizables denominadas recursos. Los estilos permiten establecer las propiedades de los elementos y volver a usar esos valores para lograr una apariencia coherente entre distintos elementos. Una propiedad [ControlTemplate](xref:Windows.UI.Xaml.Controls.ControlTemplate) define la apariencia de un control y también puede aplicarse como un recurso. Para más información, consulte [Estilos XAML](/windows/uwp/design/controls-and-patterns/xaml-styles) y [Plantillas de control](/windows/uwp/design/controls-and-patterns/control-templates).

Siempre que crea un recurso a partir de una propiedad existente, [Style](xref:Windows.UI.Xaml.Style) o [ControlTemplate](xref:Windows.UI.Xaml.Controls.ControlTemplate), el cuadro de diálogo **Crear recurso** permite definir el recurso en el nivel de aplicación, el nivel de documento o el nivel de elemento. Estos niveles determinan dónde se puede usar el recurso. Por ejemplo, si define el recurso en el nivel de elemento, solo se podrá aplicar el recurso al elemento para el que lo creó. También puede almacenar el recurso en un [diccionario de recursos](/windows/uwp/design/controls-and-patterns/resourcedictionary-and-xaml-resource-references): un archivo independiente que puede volver a usar en otro proyecto.

## <a name="create-a-new-resource"></a>Crear un nuevo recurso

1. Con un archivo XAML abierto en el diseñador XAML, cree un elemento o elija uno en la ventana Esquema del documento.

2. En la ventana **Propiedades**, seleccione el marcador de propiedad (aparece como un símbolo de cuadro a la derecha de un valor de propiedad) y, después, pulse **Convertir en nuevo recurso**. Un símbolo de cuadro blanco indica un valor predeterminado y un símbolo de cuadro negro indica normalmente que se ha aplicado un recurso local.

     Aparece el cuadro de diálogo correspondiente para crear un recurso. Este cuadro de diálogo aparece cuando se crea un recurso de pincel:

     ![Cuadro de diálogo Crear recurso](../designers/media/xaml_create_resource.png)

3. En el cuadro **Nombre (clave)**, escriba un nombre de clave. Este es el nombre que puede usar si desea que otros elementos hagan referencia al recurso.

4. En **Definir en**, seleccione la opción en la que quiere definir el recurso:

    - Para que el recurso esté disponible en cualquier documento de la aplicación, seleccione **Aplicación**.

    - Para que el recurso esté disponible únicamente en el documento actual, seleccione **Este documento**.

    - Para que el recurso esté disponible únicamente en el elemento desde el que creó el recurso o en sus elementos secundarios, seleccione **Este documento** y, en la lista desplegable, seleccione **elemento**: **nombre**.

    - Para definir el recurso en un archivo de [diccionario de recursos](/windows/uwp/design/controls-and-patterns/resourcedictionary-and-xaml-resource-references) que se pueda reutilizar en otros proyectos, haga clic en **Diccionario de recursos**. A continuación, seleccione un archivo de diccionario de recursos existente, como **StandardStyles.xaml**, en la lista desplegable.

5. Haga clic en el botón **Aceptar** para crear el recurso y aplicarlo al elemento a partir del cual se ha creado.

## <a name="apply-a-resource-to-an-element-or-property"></a>Aplicación de un recurso a un elemento o propiedad

1. En la ventana Esquema del documento, elija el elemento al que quiere aplicar un recurso.

2. Realice una de las siguientes acciones:

   - Aplique un recurso a una propiedad. En la ventana **Propiedades**, seleccione el marcador de propiedad al lado del valor de la propiedad, seleccione **Recurso local** o **Recurso del sistema**, y luego seleccione un recurso de los disponibles en la lista que aparece.

      Si no ve un recurso que espera ver, es posible que el tipo de ese recurso no coincida con el tipo de la propiedad.

   - Aplique un recurso de plantilla de control o estilo a un control. Abra el menú contextual de un control en la ventana Esquema del documento, seleccione **Editar plantilla** o **Editar plantillas adicionales**, haga clic en **Aplicar recurso** y, después, seleccione el nombre de la plantilla de control en la lista que aparece.

     > [!NOTE]
     > **Editar plantilla** se aplica a las plantillas de control. **Editar plantillas adicionales** se aplica a otros tipos de plantilla.

     Puede aplicar recursos siempre que sean compatibles. Por ejemplo, puede aplicar un recurso de pincel a la propiedad **Foreground** de un control [TextBox](xref:Windows.UI.Xaml.Controls.TextBox).

## <a name="edit-a-resource"></a>Edición de un recurso

1. Elija un elemento en la mesa de trabajo o en la ventana Esquema del documento.

2. En la ventana **Propiedades**, seleccione el marcador de propiedad predeterminado o local y, después, seleccione **Editar recurso** para abrir el cuadro de diálogo **Editar recurso**.

3. Modifique las opciones del recurso.

## <a name="see-also"></a>Vea también

- [Tutorial: Crear una UI usando el Diseñador XAML](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
