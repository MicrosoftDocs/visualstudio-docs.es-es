---
title: Instrucciones para crear áreas de formulario de Outlook
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a962b1ae2bff7b9a954204485a6ee73a3b63eb7b
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255954"
---
# <a name="guidelines-to-create-outlook-form-regions"></a>Instrucciones para crear áreas de formulario de Outlook
  La siguiente información puede ayudarle a optimizar las áreas del formulario y a evitar posibles problemas:

- [Usar nombres de área de formulario](#UsingFormRegions).

- [Deshabilitar la herencia del área de formulario](#DisablingInheritance).

- [Comprender los tipos y los nombres de clase de mensaje](#ClassNames).

- [Diseñar áreas de formulario adyacentes para el panel de lectura](#ReadingPane).

- [Usar tamaños de icono óptimos](#UsingOptimal).

  Para obtener más información sobre las áreas de formulario, consulte [crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md).

  [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="UsingFormRegions"></a>Usar nombres de área de formulario
 Existen varios nombres que se usan para describir el área de formulario. Es importante que comprenda la diferencia entre estos nombres y cómo afectan al área de formulario. En la siguiente tabla se describe cada uno de los nombres.

|Nombre del área de formulario|Descripción|
|----------------------|-----------------|
|Nombre de elemento del área de formulario|Es el nombre que especifica para el elemento **Área de formulario de Outlook** en el cuadro de diálogo **Agregar nuevo elemento** . Éste es el nombre del archivo de código del área de formulario que aparece en el **Explorador de soluciones**.|
|Propiedad<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A>|Debe especificar este nombre en la página **Escriba un texto descriptivo y seleccione sus preferencias de presentación** del asistente **Nueva área de formulario de Outlook** . Este nombre aparece como la propiedad **FormRegionName** en la ventana **Propiedades** .<br /><br /> Use la propiedad <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> para especificar la etiqueta que identifica el área de formulario en la interfaz de usuario (UI) de Outlook. En áreas de formulario independientes, este nombre aparece como un botón en la cinta de opciones del elemento de Outlook.<br /><br /> En las áreas de formulario adyacentes, este nombre aparece como texto de encabezado sobre el área de formulario.|
|Atributo `Microsoft.Office.Tools.Outlook.FormRegionName`|Al agregar un elemento **Área de formulario de Outlook** al proyecto, Visual Studio establece esta propiedad en el nombre completo del área de formulario. El nombre completo predeterminado es el nombre del complemento VSTO conectado al nombre del área de formulario mediante un punto; por ejemplo, `OutlookAddIn1.FormRegion1`.<br /><br /> Este nombre completo también aparece como atributo en la parte superior de la clase del generador del área del formulario.<br /><br /> Use el atributo `Microsoft.Office.Tools.Outlook.FormRegionName` para identificar de forma exclusiva el área de formulario en todos los complementos VSTO de Outlook. No puede cambiar el valor del atributo `Microsoft.Office.Tools.Outlook.FormRegionName` cambiando el nombre del elemento del área de formulario, ni cambiando la propiedad <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A>. Para cambiar este nombre, debe modificar el atributo `Microsoft.Office.Tools.Outlook.FormRegionName` en el archivo de código del área de formulario.|

## <a name="DisablingInheritance"></a>Deshabilitar la herencia del área de formulario
 De forma predeterminada, una clase de mensaje personalizada hereda todas las asociaciones de área de formulario de la clase de mensaje base. Por ejemplo, una clase de mensaje denominada `IPM.Task.Contoso` se deriva de `IPM.Task`. Por consiguiente, `IPM.Task.Contoso` hereda las asociaciones del área de formulario de `IPM.Task`.

 Si no desea que el área de formulario esté asociada a una clase de mensaje derivada, establezca la propiedad <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> del área de formulario en **true**. Por ejemplo, si asocia un área de `IPM.Task` formulario adyacente a y establece la <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> propiedad en **true**, el área de formulario solo se anexará a la parte inferior de un formulario de tareas estándar. El área de formulario no se anexará a la parte inferior de ninguna versión personalizada de un formulario de tareas estándar.

## <a name="ClassNames"></a>Descripción de los tipos y los nombres de clase de mensaje
 El nombre de tipo de un elemento de Outlook difiere del nombre de la clase de mensaje de un elemento de Outlook. Por ejemplo, el nombre de tipo de un elemento RSS es `Microsoft.Office.Interop.Outlook.PostItem`. El nombre de clase de mensaje de un elemento RSS es `IPM.Post.RSS`.

 Use el nombre del tipo para hacer referencia a un elemento de Outlook en el código. Para obtener una lista de nombres de tipo, consulte [asociar un área de formulario a una clase de mensaje de Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

 Use el nombre de la clase de mensaje de elementos de Outlook en el asistente **Nueva área de formulario de Outlook** para asociar el elemento al área de formulario. Para obtener una lista de nombres de clase de mensaje válidos, vea [asociar un área de formulario a una clase de mensaje de Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

## <a name="ReadingPane"></a>Diseñar áreas de formulario adyacentes para el panel de lectura
 Puede usar el panel de lectura de Outlook para ofrecer una vista previa de un elemento de Outlook sin tener que abrir el elemento. El panel de lectura está diseñado solo para su lectura. Por consiguiente, es posible que los controles de entrada que se agregan a un área de formulario adyacente (como un cuadro de texto), no se comporten de la manera esperada cuando el elemento y el área de formulario se abren en el panel de lectura.

 Por ejemplo, si un elemento que tiene un área de formulario adyacente se abre en el panel de lectura, se puede producir la situación siguiente:

1. Seleccione texto en el cuadro de texto que está incluido en el área de formulario.

2. Presione **Supr**.

3. Se eliminará el elemento de correo al completo, en lugar del texto incluido en el cuadro de texto.

   Si diseña un área de formulario adyacente que contenga controles de entrada, pruebe los controles en el panel de lectura para asegurarse de que funcionan correctamente. Considere la posibilidad de agregar código personalizado que deshabilite los controles que no funcionen según lo esperado.

   Asimismo, también puede establecer la propiedad <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> del área de formulario en **False**. De esta manera, el área de formulario no se podrá usar en el panel de lectura.

## <a name="UsingOptimal"></a>Usar tamaños de icono óptimos
 Puede especificar qué iconos desea mostrar en el área de formulario, estableciendo las propiedades de iconos en el grupo de propiedades **Iconos** de la ventana **Propiedades** . Use las siguientes instrucciones para lograr una calidad visual inmejorable:

- Para el icono **Página** , use un archivo de formato PNG (Portable Network Graphics).

- Los iconos**Ventana** deben tener 32 por 32 píxeles.

- Todos los demás iconos deben ser de 16 por 16 píxeles.

  El icono **Página** aparecerá en la cinta de opciones de un inspector, en aquellos elementos que tengan áreas de formulario de tipo Independiente, Reemplazo o Reemplazo total.

  El icono de **ventana** aparece en el área de notificación y en el cuadro de diálogo de la**pestaña** **Alt**+para los elementos abiertos que muestran las áreas de formulario de reemplazo o de reemplazo completo.

## <a name="see-also"></a>Vea también
- [Obtener acceso a un área de formulario en tiempo de ejecución](../vsto/accessing-a-form-region-at-run-time.md)
- [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)
- [Tutorial: Diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Cómo: Agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Asociar un área de formulario a una clase de mensaje de Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
